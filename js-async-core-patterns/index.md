---
id: Zr4RfI
filename: js-async-core-patterns
image: https://heropy.dev/postAssets/Zr4RfI/main.jpg
title: JS 비동기 핵심 패턴
createdAt: 2023-12-14
updatedAt: 2023-12-15
group: JS
author:
  - ParkYoungWoong
tags:
  - JS
  - Async/Await
  - Promise
description: 
  동기적으로 동작하는 코드와 비동기적으로 동작하는 코드의 차이점을 알아보고, 비동기 코드를 작성할 때 사용하는 여러 핵심 패턴을 알아봅니다.
---

동기적으로 동작하는 코드와 비동기적으로 동작하는 코드의 차이점을 알아보고, 비동기 코드를 작성할 때 사용하는 여러 핵심 패턴을 알아봅니다.

## 동기와 비동기

동기(Synchronous)는 하나의 작업이 실행되고 완료될 떄까지 다음 작업이 실행되지 않고 대기하는 것을 말합니다.
다음 작업이 실행되려면, 이전 작업이 완료되어야 합니다. 
즉, 직렬적으로 실행됩니다.

다음 예제에서 각 코드는 순서대로 실행되고, 다음 코드가 실행되기 전에 이전 코드가 완료되어야 합니다.

```js --caption=순서대로 실행되는 코드
console.log(1)
;(() => console.log(2))()
console.log(3)
// 1
// 2
// 3
```

비동기(Asynchronous)는 하나의 작업 완료와 상관없이 다음 작업이 실행될 수 있는 것을 의미합니다.
이전 작업이 실행되면, 완료되지 않아도 다음 작업이 실행될 수 있습니다.
즉, 병렬적으로 실행됩니다.

다음 예제에서 `setTimeout` 함수는 두 번째로 실행되지만, 완료되기 전에 다음 코드가 실행/완료됩니다.

```js --line-active=2 --caption=순서대로 실행되지 않는 코드
console.log(1)
setTimeout(() => console.log(2), 0)
console.log(3)
// 1
// 3
// 2
```

조금 더 구체적인 예제를 살펴봅시다.
다음과 같이 실제 서버에서 영화 정보를 가져오는 함수가 있습니다.
영화 정보를 가져오려면, 서버와 통신하는 과정이 필요하고 그 시간은 네트워크 속도나 서버 상태 등에 따라 매번 달라집니다. 
만약 이것이 동기적으로 동작한다면, 영화 정보를 가져오기 전에는 다른 코드가 전혀 실행되지 않기 떄문에, 사용자는 시스템이 멈추는 것처럼 느낄 수 있습니다.
따라서 대표적으로 네트워크 통신을 위한 코드는 비동기적으로 동작하게 작성합니다.

```js --caption=getMovies 함수
const getMovies = (title) => {
  return fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
    .then(res => res.json())
    .then(({ Search }) => console.log(Search))
}
```

이제 위 함수를 활용해 다음과 같이 코드를 작성하면, 영화 정보를 모두 가져오기 전에 `'종료!'` 메시지가 먼저 출력됩니다.
`getMovies`는 비동기 함수이기 때문에, 실행되고 완료되기 전에 다음 코드가 실행될 수 있습니다.

```js --caption=순서대로 실행되지 않는 코드
console.log('시작!')
getMovies('avengers')
getMovies('frozen')
console.log('종료!')
// 1. '시작!'
// 4. '종료!'
// 3. Frozen[]
// 2. Avengers[]
```

만약 동기적으로 실행되는 순서를 유지하고 싶다면, 다음과 같이 콜백 함수를 활용해서 영화 정보를 가져온 후 콜백이 실행되는 구조로 수정할 수 있습니다.

```js --line-active=1,6
const getMovies = (title, callback) => {
  return fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
    .then(res => res.json())
    .then(({ Search }) => {
      console.log(Search)
      callback()
    })
}
```

`getMovies` 함수로 전달하는 콜백은 영화 정보를 가져온 후 실행되기 구조로 변경되었으므로, 순서대로 실행할 다음 작업을 콜백 함수 안에서 작성할 수 있습니다.

```js --caption=순서대로 동작하는 콜백 패턴
console.log('시작!')
getMovies('avengers', () => {
  getMovies('frozen', () => {
    console.log('종료!')
  })
})
// 1. '시작!'
// 2. Avengers[]
// 3. Frozen[]
// 4. '종료!'
```

위의 콜백 방식으로도 원하는 순서로 코드가 실행되도록 만들 수 있지만, 더 최신의 방식도 있습니다.
일단 최신 방식을 사용하려면, `getMovies` 함수를 `Promise` 클래스를 사용하도록 다음과 같이 수정해야 합니다.

```js
const getMovies = (title) => {
  return new Promise(resolve => {
    fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
      .then(res => res.json())
      .then(({ Search }) => {
        console.log(Search)
        resolve()
      })
  })
}
```

이제 `.then()` 메소드를 사용해 좀 더 간결하고 직관적으로 코드를 작성할 수 있습니다.

```js --line-active=3-4 --caption=순서대로 동작하는 .then() 패턴
console.log('시작!')
getMovies('avengers')
  .then(() => getMovies('frozen'))
  .then(() => console.log('종료!'))
// 1. '시작!'
// 2. Avengers[]
// 3. Frozen[]
// 4. '종료!'
```

`.then()` 메소드 대신, `async`와 `await` 키워드를 사용해, 동기적인 코드처럼 작성할 수도 있습니다.

```js --line-active=1,3-4 --caption=순서대로 동작하는 async/await 패턴
;(async () => {
  console.log('시작!')
  await getMovies('avengers')
  await getMovies('frozen')
  console.log('종료!')
})()
// 1. '시작!'
// 2. Avengers[]
// 3. Frozen[]
// 4. '종료!'
```

## 비동기 코드 패턴

비동기 코드를 작성하는 패턴은 크게 콜백과 Promise 패턴으로 나눌 수 있습니다.
Promise 패턴에서는 `.then()` 메소드를 사용하거나 `async`, `await` 키워드를 사용하는 방식으로 나뉩니다.

### 콜백

다음 예제에서 `a`는 1초 뒤에 숫자 `1`을 출력하는 비동기적으로 동작하는 함수(줄여서 '비동기 함수'라고 부릅시다)이고, `b`와 `c`는 숫자 `2`와 `3`을 출력하는 '동기 함수'입니다.
각 함수를 순서대로 호출하지만, `a`는 비동기 함수이기 때문에, 실행 후 완료되지 않아도 다음 함수 실행으로 넘어갈 수 있습니다.
따라서 `2`, `3`, `1` 순서로 결과가 출력됩니다.

```js
const a = () => {
  setTimeout(() => {
    console.log(1)
  }, 1000)
}
const b = () => console.log(2)
const c = () => console.log(3)

a()
b()
c()
// 2
// 3
// 1 
```

만약 `1`, `2`, `3` 순서로 결과를 출력하고 싶다면, 다음과 같이 `a` 함수를 콜백을 사용하도록 수정할 수 있습니다.
`a` 함수로 전달된 콜백 함수는 모든 동작이 완료된 시점에서 호출됩니다.

```js --line-active=4,8-11
const a = callback => {
  setTimeout(() => {
    console.log(1)
    callback()
  }, 1000)
}

a(() => {
  b()
  c()
})
// 1
// 2
// 3
```

이렇게 콜백 방식은 비동기 코드를 처리할 때 유용하지만, 순서 보장을 위한 함수를 여러 번 중첩하면 코드가 복잡해지고 가독성이 떨어지기 쉽습니다.

다음 예제는 여러 비동기 함수를 순차적으로 실행하기 위해서 어떤 패턴이 작성되는지 보여줍니다.
이렇게 콜백 함수가 여러 번 중첩돼 점점 들여쓰여지는 코드 패턴이 마치 개미 지옥과 비슷하다고 해서 **콜백 지옥(Callback Hell)** 이라고 부릅니다.

```js --caption=콜백 패턴의 문제점(콜백 지옥)
const a = callback => {
  setTimeout(() => {
    console.log(1)
    callback()
  }, 1000) // 1초
}
const b = callback => {
  setTimeout(() => {
    console.log(2)
    callback()
  }, 700) // 0.7초
}
const c = callback => {
  setTimeout(() => {
    console.log(3)
    callback()
  }, 3000) // 3초
}
const d = callback => {
  setTimeout(() => {
    console.log(4)
    callback()
  }, 1200) // 1.2초
}
// ...

// 콜백 지옥!
a(() => {
  b(() => {
    c(() => {
      d(() => {
        // ...
      })
    })
  })
})
```

다음은 콜백 패턴으로 영화 정보를 순차적으로 가져오는 예제입니다.

```js --caption=콜백 패턴을 사용한 순차적인 영화 검색
const getMovies = (title, callback) => {
  fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
    .then(res => res.json())
    .then(({ Search }) => {
      callback(Search)
    })
}

getMovies('frozen', movies => {
  console.log('1. 겨울왕국:', movies)
  getMovies('avengers', movies => {
    console.log('2. 어벤져스:', movies)
    getMovies('avatar', movies => {
      console.log('3. 아바타:', movies)
    })
  })
})
// 1. 겨울왕국: Frozen[]
// 2. 어벤져스: Avengers[]
// 3. 아바타: Avatar[]
```


### .then()

위에서 살펴본 콜백 패턴의 단점을 보완하기 위해, ES2015에서 `Promise` 클래스가 도입되었습니다.
`Promise` 클래스를 통해 콜백 대신 `resolve` 메소드를 호출하면, 모든 동작이 완료된 시점을 보장할 수 있습니다.
이제 함수를 호출할 때, `.then()` 메소드를 체이닝으로 사용할 수 있고, `.then()` 메소드의 콜백은 모든 동작이 완료된 시점(`resolve` 호출 위치)에서 실행됩니다.

/// message-box --icon=info
Promise 클래스의 자세한 사용법은 아래에서 살펴봅니다.
///

```js --line-active=2,5,12
const a = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      console.log(1)
      resolve()
    }, 1000)
  })
}
const b = () => console.log(2)
const c = () => console.log(3)

a().then(() => {
  b()
  c()
})
// 1
// 2
// 3
```

앞서 콜백 방식에서 살펴본 순차적으로 실행할 여러 비동기 함수가 있습니다. 
모두 `Promise` 클래스를 사용해 수정했지만, 여전히 콜백 지옥과 같은 패턴 문제가 발생합니다.

```js
const a = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      console.log(1)
      resolve()
    }, 1000)
  })
}
const b = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      console.log(2)
      resolve()
    }, 700)
  })
}
const c = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      console.log(3)
      resolve()
    }, 3000)
  })
}
const d = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      console.log(4)
      resolve()
    }, 1200)
  })
}
```

```js
a().then(() => {
  b().then(() => {
    c().then(() => {
      d().then(() => {
        // ...
      })
    })
  })
})
// 1
// 2
// 3
// 4
```

여기서 중요한 것은 `.then()`에서 각 비동기 함수 호출의 결과(`promise` 인스턴스)를 반환하면, 다시 `.then()`을 체이닝으로 사용할 수 있습니다.

```js --caption=콜백 지옥해서 해방
a()
  .then(() => b())
  .then(() => c())
  .then(() => d())
  .then(() => {
    // ...
  })
```

사용 패턴에 따라 다음과 같이 비동기 함수 자체를 반환해도 동일한 결과를 얻을 수 있습니다.

```js
a()
  .then(b)
  .then(c)
  .then(d)
```

다음은 `Promise` 클래스로 작성한 함수와 `.then()` 메소드를 사용해 영화 정보를 순차적으로 가져오는 예제입니다.

```js
const getMovies = (title) => {
  return new Promise(resolve => {
    fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
      .then(res => res.json())
      .then(({ Search }) => {
        resolve(Search)
      })
  })
}

getMovies('frozen')
  .then(movies => {
    console.log('1. 겨울왕국:', movies)
    return getMovies('avengers')
  })
  .then(movies => {
    console.log('2. 어벤져스:', movies)
    return getMovies('avatar')
  })
  .then(movies => {
    console.log('3. 아바타:', movies)
  })
```

### async/await

`.then()` 메소드를 사용하는 방식은 콜백 패턴보다 가독성이 훨씬 좋지만, 여전히 일부 콜백 구조를 가지고 있습니다.
ES2017에서 새롭게 도입된 `async`와 `await` 키워드를 사용하면, 더 쉽게 비동기 코드를 작성할 수 있습니다.

/// message-box --icon=info
앞서 `Promise` 클래스로 작성한 함수는 동일합니다.
///

다음과 같이 `.then()` 메소드르 사용하는 패턴을, `async`와 `await` 키워드를 사용해서 작성할 수도 있습니다.

```js
a()
  .then(() => b())
  .then(() => c())
  .then(() => d())
  .then(() => {
    // ...
  })
```

`await` 키워드는 비동기 함수의 실행 후 완료를 기다리는 역할을 합니다.
`await` 키워드는 `async` 키워드가 붙은 함수 안에서만 사용할 수 있으니 주의하세요!

```js
;(async () => {
  await a()
  await b()
  await c()
  await d()
  // ...
})()
```

다음은 `Promise` 클래스로 작성한 함수와 `async`와 `await` 키워드를 사용해 영화 정보를 순차적으로 가져오는 예제입니다.

```js
const getMovies = (title) => {
  return new Promise(resolve => {
    fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
      .then(res => res.json())
      .then(({ Search }) => {
        resolve(Search)
      })
  })
}

;(async () => {
  const frozen = await getMovies('frozen')
  console.log('1. 겨울왕국:', movies)
  
  const avengers = await getMovies('avengers')
  console.log('2. 어벤져스:', avengers)
  
  const avatar = await getMovies('avatar')
  console.log('3. 아바타:', avatar)
})()
```

비동기 함수 호출에서 반환되는 결과를 별도 변수에 할당하지 않고 다음과 같이 바로 사용할 수도 있습니다.

```js
;(async () => {
  console.log('1. 겨울왕국:', await getMovies('frozen'))
  console.log('2. 어벤져스:', await getMovies('avengers'))
  console.log('3. 아바타:', await getMovies('avatar'))
})()
```

## Promise

`Promise` 클래스를 생성자 함수로 호출하면, 비동기 함수를 랩핑한 프로미스(약속) 인스턴스(`promise`)를 반환합니다.
이 프로미스(약속) 인스턴스는 `.then()` 메소드나 `await` 키워드로 사용하며, 이때 비동기 함수의 실행부터 완료까지의 각 상태를 가지게 됩니다.

- 대기(Pending): 약속한 동작이 시작된 후, 약속이 이행되거나 거부되기 전까지 기다리는 상태.
- 이행(Fulfilled): 약속한 동작이 정상적으로 완료됨, 약속을 이행함.
- 거부(Rejected): 약속한 동작이 완료되지 못함, 약속의 이행을 거부함.

```js --line-active=6,8
function 함수(resolve, reject) {
  // ... 대기(..)
  if (error) reject(에러) // 거부(X)
  resolve(데이터) // 이행(O)
}

const promise = new Promise(함수)
```

`resolve(데이터)` 호출의 인수(`데이터`)는, `.then()` 메소드의 콜백 매개변수로 전달되거나 `await` 키워드의 반환값으로 사용됩니다.
`reject(에러)` 호출의 인수(`에러`)는, `.catch()` 메소드 콜백 매개변수로 전달되거나 `try/catch` 구문의 `catch` 블록의 에러변수로 전달됩니다.

```js --caption=.then() 메소드를 사용하는 경우.
promise
  .then(데이터 => {})

// 또는,

promise
  .then(데이터 => {})
  .catch(에러 => {})
  .finally(() => {})
```

```js --caption=async/await 키워드를 사용하는 경우.
;(async () {
  const 데이터 = await promise
})()

// 또는,

;(async () {
  try {
    const 데이터 = await promise
  } catch (에러) {
    //
  } finally {
    //
  }
})()
```

### 에러 핸들링

비동기 코드에서 문제가 발생하는 상황에 동작할 내용을 등록(에러 핸들링, Error Handling)해야 하는 경우가 있습니다.

다음 예제에서 `delayAdd` 함수는 숫자 데이터를 받아 1초 뒤에 `1`을 더한 결과를 반환합니다.
그런데 만약 숫자 데이터가 `10`보다 크면, 결과 대신 에러 메시지를 반환하고, `done` 콜백은 항상 실행됩니다.

결과를 잘 처리(이행)하거나 처리하지 못했을 때(거부) 그리고 어떤 상황이든 항상 실행할 각 콜백 함수를 받아 처리하고 있습니다.

```js
const delayAdd = (num, success, failure, done) => {
  setTimeout(() => {
    if (num > 10) {
      failure(`${num}는 10보다 클 수 없습니다.`)
      done()
      return
    }
    success(num + 1)
    done()
  }, 1000)
}
```

```js
// delayAdd(숫자, 성공, 실패, 최종)

delayAdd(
  4,
  res => console.log(res),
  err => console.error(err),
  () => console.log('종료!')
)
// 5
// `종료!`

delayAdd(
  92,
  res => console.log(res),
  err => console.error(err),
  () => console.log('종료!')
)
// '92는 10보다 클 수 없습니다.'
// `종료!`
```

비동기 함수는 콜백 대신 다음과 같이 `Promise` 클래스를 활용해 작성할 수 있습니다.
`success` 대신 `resolve`, `failure` 대신 `reject`를 사용합니다.

/// message-box --icon=info
`resolve`와 `reject` 호출 후 다음 작업은 정상적으로 실행되지만, `resolve`가 호출되면 `reject`은 호출되지 않고, `reject`가 호출되면 `resolve`는 호출되지 않습니다.
따라서 필요한 경우, `return` 키워드를 사용해 다음 작업이 실행되지 않도록 처리해야 할 수 있습니다.
///

```js
const delayAdd = num => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (num > 10) {
        reject(`${num}는 10보다 클 수 없습니다.`)
        return
      }
      console.log(num)
      resolve(num + 1)
    }, 1000)
  })
}
```

기존의 콜백 패턴의 `done` 대신 `.finally()` 메소드를 사용할 수 있습니다.
`.finally()` 메소드는 이행이나 거부 상태와 상관없이 항상 실행됩니다.

```js
delayAdd(11)
  .then(res => console.log(res)) // 성공
  .catch(err => console.error(err)) // 실패
  .finally(() => console.log('종료!')) // 최종
```

`async`와 `await` 키워드를 사용하면, `try/catch/finally` 구문을 사용해 에러 핸들링을 할 수 있습니다.

```js
;(async () => {
  try {
    const res = await delayAdd(11)
    console.log(res)
  } catch (err) {
    console.error(err)
  } finally {
    console.log('종료!')
  }
})()
```

기존에 살펴봤던 영화 정보를 가져오는 `getMovies` 함수를 `Promise` 클래스를 통해 다음과 같이 수정할 수 있습니다.
영화 정보를 가져오는 과정에서 에러가 발생하면(네트워크 실패, 잘못된 검색어 제공 등), `reject`를 호출하고, 성공하면 `resolve`를 호출합니다.

```js
const getMovies = title => {
  return new Promise((resolve, reject) => {
    fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
      .then(res => res.json())
      .then(json => {
        if (json.Response === 'False') {
          reject(json.Error)
        }
        resolve(json.Search)
      })
      .catch(error => {
        reject(error)
      })
  })
}
```

다음은 `.then()`, `.catch()`, `.finally()` 메소드를 사용한 예제입니다.

```js
let loading = true
getMovies('avengers')
  .then(movies => console.log('영화 목록:', movies))
  .catch(error => console.log('에러 발생:', error))
  .finally(() => loading = false)
```

다음은 `async`와 `await` 키워드를 사용한 예제입니다.

```js
let loading = true
;(async () => {
  try {
    const movies = await getMovies('avengers')
    console.log('영화 목록:', movies)
  } catch (error) {
    console.log('에러 발생:', error)
  } finally {
    loading = false
  }
})()
```

### 반복문에서 비동기 처리

비동기 함수를 반복 호출하는 경우, `for` 반복문(`of`, `in` 포함)을 사용해야 이전 작업이 완료된 후 다음 작업이 실행됩니다.
`.forEach()`, `.map()` 등의 반복 메소드는 이전 작업의 완료 여부와 상관없이 실행되기 때문에, 비동기 함수의 반복 호출에 적합하지 않습니다.

```js
const getMovies = title => {
  return new Promise(resolve => {
    fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
      .then(res => res.json())
      .then(res => resolve(res))
  })
}

const titles = ['frozen', 'avengers', 'avatar']

// 잘못된 방법!
titles.forEach(async title => {
  const movies = await getMovies(title)
  console.log(title, movies)
})

// 올바른 방법!
;(async () => {
  for (const title of titles) {
    const movies = await getMovies(title)
    console.log(title, movies)
  }
})()
```

### 정적 메소드

#### Promise.all

제공되는 배열 내의 모든 약속(프로미스)을 동시에 실행해, 모두 이행되기까지 기다립니다.
단, 약속이 하나라도 거부되면, 첫 거부의 이유(값)로 모든 약속이 함께 거부됩니다.

```js
const getMovies = (title) => {
  return new Promise((resolve, reject) => {
    if (!title) {
      reject('검색어를 제공해야 합니다!')
    }
    fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
      .then(res => res.json())
      .then(({ Search }) => {
        resolve(Search)
      })
  })
}
```

```js --line-active=6-8,16-18 --line-error=9-11,19-21 --caption=모두 이행되는 경우.
const frozen = getMovies('frozen')
const avengers = getMovies('avengers')
const avatar = getMovies('avatar')

Promise.all([frozen, avengers, avatar])
  .then(res => {
    console.log(res) // [Frozen[], Avengers[], Avatar[]]
  })
  .catch(err => { // 실행되지 않음!
    console.error(err)
  })

// 또는,

;(async () => {
  try {
    const res = await Promise.all([frozen, avengers, avatar])
    console.log(res) // [Frozen[], Avengers[], Avatar[]]
  } catch (err) { // 실행되지 않음!
    console.error(err)
  }
})()
```

```js --line-active=2,9-11,19-21 --line-error=6-8,18 --caption=거부가 포함된 경우.
const frozen = getMovies('frozen')
const avengers = getMovies() // 거부되는 프로미스!
const avatar = getMovies('avatar')

Promise.all([frozen, avengers, avatar])
  .then(res => { // 실행되지 않음!
    console.log(res)
  })
  .catch(err => {
    console.error(err) // Error: 검색어를 제공해야 합니다.
  })

// 또는,

;(async () => {
  try {
    const res = await Promise.all([frozen, avengers, avatar])
    console.log(res) // 실행되지 않음!
  } catch (err) {
    console.error(err) // Error: 검색어를 제공해야 합니다.
  }
})()
```

#### Promise.allSettled

제공되는 배열 내의 모든 약속을 동시에 실행해, 모든 이행되거나 거부되기까지 기다립니다.
앞서 살펴본 `.all()`과 다르게, 거부가 있더라도 모든 프로미스는 완료됩니다.
그리고 각 약속의 이행/거부 상태와 값을 반환합니다.

```ts --caption=Promise.allSettled의 반환 타입
type AllSettledResult = {
  status: 'fulfilled' | 'rejected' // 이행 또는 거부 상태
  value?: any // 이행된 값
  reason?: any // 거부된 이유(값)
}[]
```

```js
const frozen = getMovies('frozen')
const avengers = getMovies() // 거부되는 프로미스!
const avatar = getMovies('avatar')

Promise.allSettled([frozen, avengers, avatar])
  .then(res => {
    console.log(res)
    // [
    //   { status: 'fulfilled', value: Frozen[] }, 
    //   { status: 'rejected', reason: '검색어를 입력하세요.' }, 
    //   { status: 'fulfilled', value: Avatar[] }
    // ]
  })

// 또는,

;(async () => {
  const res = await Promise.allSettled([frozen, avengers, avatar])
  console.log(res)
  // [
  //   { status: 'fulfilled', value: Frozen[] }, 
  //   { status: 'rejected', reason: '검색어를 입력하세요.' }, 
  //   { status: 'fulfilled', value: Avatar[] }
  // ]
})()
```

#### Promise.race

제공되는 배열 내의 모든 약속을 동시에 실행해, 가장 먼저 이행되거나 거부된 약속을 하나만 반환합니다.

/// message-box --icon=info
'race'라는 단어에서 알 수 있듯이, 선착순입니다.
///

```js
const getMovies = (title, delay = 0) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (!title) {
        reject('검색어를 입력하세요.')
      }
      fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
        .then(res => res.json())
        .then(({ Search }) => {
          resolve(Search)
        })
    }, delay)
  })
}

const frozen = getMovies('frozen', 1000) // 1초
const avengers = getMovies(null, 3000) // 3초, 거부되는 프로미스!
const avatar = getMovies('avatar', 2000) // 2초

Promise.race([frozen, avengers, avatar])
  .then(res => {
    console.log(res) // Frozen[]
  })
  .catch(err => {
    console.error(err)
  })

// 또는,

;(async () => {
  try {
    const res = await Promise.race([frozen, avengers, avatar])
    console.log(res) // Frozen[]
  } catch (err) {
    console.error(err)
  }
})()
```

#### Promise.any

제공되는 배열 내의 모든 약속을 동시에 실행해, 가장 먼저 이행된 약속을 하나만 반환합니다.
이행된 프로미스가 하나라도 있는 경우, 거부된 프로미스는 무시합니다.
만약 모든 프로미스가 거부된 경우, `AggregateError`를 반환합니다.

/// message-box --icon=info
`.race()`와 마찬가지로 선착순이지만, 거부된 약속은 무시하고 이행된 약속만 취급합니다.
///

```js
const getMovies = (title, delay = 0) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (!title) {
        reject('검색어를 입력하세요.')
      }
      fetch(`https://omdbapi.com/?apikey=7035c60c&s=${title}`)
        .then(res => res.json())
        .then(({ Search }) => {
          resolve(Search)
        })
    }, delay)
  })
}

const frozen = getMovies('frozen', 2000) // 2초
const avengers = getMovies(null, 1000) // 1초, 거부되는 프로미스!
const avatar = getMovies('avatar', 3000) // 3초

Promise.any([frozen, avengers, avatar])
  .then(res => {
    console.log(res) // Frozen[]
  })

// 또는,

;(async () => {
  const res = await Promise.any([frozen, avengers, avatar])
  console.log(res) // Frozen[]
})()
```

```js --caption=모든 프로미스가 거부된 경우.
const frozen = getMovies(null, 2000) // 2초, 거부되는 프로미스!
const avengers = getMovies(null, 1000) // 1초, 거부되는 프로미스!
const avatar = getMovies(null, 3000) // 3초, 거부되는 프로미스!

Promise.any([frozen, avengers, avatar])
  .then(res => {
    console.log(res) // AggregateError: All promises were rejected
  })

// 또는,

;(async () => {
  const res = await Promise.any([frozen, avengers, avatar])
  console.log(res) // AggregateError: All promises were rejected
})()
```

#### Promise.resolve

무조건 이행되는 약속을 반환합니다.

```js --line-active=4,10-11 --line-error=5,12-13
const promise = Promise.resolve(123)

promise
  .then((res) => console.log(res)) // 123
  .catch((err) => console.log(err)) // 실행되지 않음!

// 또는,

;(async () => {
  try {
    console.log(await promise) // 123
  } catch (err) {
    console.log(err) // 실행되지 않음!
  }
})()
```

#### Promise.reject

무조건 거부되는 약속을 반환합니다.

```js --line-active=5,12-14 --line-error=4,10-11
const promise = Promise.reject('거부됨!')

promise
  .then((res) => console.log(res)) // 실행되지 않음!
  .catch((err) => console.log(err)) // '거부됨!'

// 또는,

;(async () => {
  try {
    console.log(await promise) // 실행되지 않음!
  } catch (err) {
    console.log(err) // '거부됨!'
  }
})()
```

## 이미지 로드 예제

이미지를 요청하고 가져와 화면에 출력하기 전에, 로딩 애니메이션을 보여주는 예제입니다.
메모리상의 이미지 요소에서 `load` 이벤트가 발생하면, 로딩 애니메이션을 제거하고 이미지를 화면에 출력합니다.

```html
<style>
  .loader {
    width: 40px;
    height: 40px;
    border: 4px solid royalblue;
    border-top-color: transparent;
    border-radius: 50%;
    animation: loader 1s infinite linear;
  }
  @keyframes loader {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }
</style>
<div id="image">
  <div class="loader"></div>
</div>
```

```js
function loadImage(src) {
  return new Promise((resolve, reject) => {
    const img = new Image()
    img.src = src
    img.addEventListener('load', () => resolve(img))
    img.addEventListener('error', () => reject(new Error(`이미지 로드에 실패하였습니다: ${src}`)))
  })
}

;(async () => {
  const imgEl = await loadImage('https://picsum.photos/2000')
  const imgContainerEl = document.querySelector('#image')
  imgContainerEl.innerHTML = ''
  imgContainerEl.append(imgEl)
})()
```