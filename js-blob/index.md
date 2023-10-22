---
id: JMVvEdT
filename: js-blob
title: Blob(블랍) 이해하기
createdAt: 2019-02-28
thumbnail: js
group: JavaScript
tags:
  - js
  - blob
description:
  JavaScript에서 Blob(Binary Large Object, 블랍)은 이미지, 사운드, 비디오와 같은 멀티미디어 데이터를 다룰 때 사용할 수 있습니다.
  대개 데이터의 크기(Byte) 및 MIME 타입을 알아내거나, 데이터를 송수신을 위한 작은 Blob 객체로 나누는 등의 작업에 사용합니다.
  이 글에서는 Blob의 생성과 읽고 쓰는 방법들에 대해서 알아보겠습니다.
---

<!-- toc -->

# Blob(블랍) 이해하기

JavaScript에서 Blob(Binary Large Object, 블랍)은 이미지, 사운드, 비디오와 같은 멀티미디어 데이터를 다룰 때 사용할 수 있습니다.
대개 데이터의 크기(Byte) 및 MIME 타입을 알아내거나, 데이터를 송수신을 위한 작은 Blob 객체로 나누는 등의 작업에 사용합니다.
이 글에서는 Blob의 생성과 읽고 쓰는 방법들에 대해서 알아보겠습니다.

> [File 객체](https://developer.mozilla.org/ko/docs/Web/API/File)도 `name`과 `lastModifiedDate` 속성이 존재하는 Blob 객체입니다.

![Blob File Object](/JMVvEdT/blob-file-object.jpg)

## Blob 생성

Blob 생성자는 새로운 Blob 객체를 반환합니다.
생성 시 인수로 `array`와 `options`을 받습니다.

```js
const newBlob = new Blob(array, options);
```

### array

Blob 생성자의 첫번째 인수로 [ArrayBuffer](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer), [ArrayBufferView](https://developer.mozilla.org/en-US/docs/Web/API/ArrayBufferView), Blob([File](https://developer.mozilla.org/ko/docs/Web/API/File)), [DOMString](https://developer.mozilla.org/ko/docs/Web/API/DOMString) 객체 또는 이러한 객체가 혼합된 Array를 사용할 수 있습니다.

```js
new Blob([new ArrayBuffer(data)], { type: 'video/mp4' });
new Blob(new Uint8Array(data), { type: 'image/png' });  
new Blob(['<div>Hello Blob!</div>'], {
  type: 'text/html',
  endings: 'native'
});  
```

### options

옵션으로는 `type`과 `endings`를 설정할 수 있습니다.
`type`은 데이터의 [MIME 타입](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types)을 설정하며, 기본값은 `""` 입니다.
`endings`는 `\n`을 포함하는 문자열 처리를 `"transparent"`와 `"native"`로 지정할 수 있으며, 기본값은 `"transparent"`입니다.

## Blob 객체

### Properties

다음은 약 43KB의 PNG 이미지로 생성한 Blob 객체 입니다.

![Blob Object](/JMVvEdT/blob-object.jpg)

생성자를 통해 만들어진 Blob 객체는 `size`, `type`의 속성을 가집니다.
`size`는 Blob 객체의 바이트(Byte) 단위 크기를 의미하며, `type`은 객체의 MIME 타입을 의미합니다.
MIME 타입을 알 수 없는 경우 빈 문자열(`""`)이 할당됩니다.

### Methods

Blob 객체에서 사용할 수 있는 `slice` 메소드는 지정된 바이트 범위의 데이터를 포함하는 새로운 Blob 객체를 만드는 데 사용됩니다.
10MB 이상 사이즈가 큰 Blob 객체를 작게 조각내어 사용할 때 유용합니다.

```js
const blob = new Blob();  // New blob object
blob.slice(start, end, type);
```

`start`는 시작 범위(Byte, Number), `end`는 종료 범위(Byte, Number), `type`은 새로운 Blob 객체의 MIME 타입(String)을 지정합니다.

```js
// Blob 객체(blob)에서 첫 1KB의 JPG Blob 객체(chunk)를 생성
const chunk = blob.slice(0, 1024, 'image/jpeg');
```

다음 예제는 위에서 살펴본 Blob 객체(약 43KB의 PNG 이미지로 생성한)를 10개의 Chunk로 조각냅니다.
그리고 각 Chunk를 `chunks` 배열에 순서대로 저장합니다.

```js
const chunks = [];
const numberOfSlices = 10;
const chunkSize = Math.ceil(blob.size / numberOfSlices);
for (let i = 0; i < numberOfSlices; i += 1) {
  const startByte = chunkSize * i;
  chunks.push(
    blob.slice(
      startByte,
      startByte + chunkSize,
      blob.type
    )
  );
}
console.log(chunks);  // This is as follows..
```

![Blob Slice](/JMVvEdT/blob-object-slice.jpg)

이렇게 조각낸 Blob 객체들(Chunks)은 필요에 의해 간단하게 다시 합칠 수 있습니다.

```js
const mergedBlob = new Blob(
  chunks,
  { type: blob.type }
);
document.getElementById('merged-image').src = window.URL.createObjectURL(mergedBlob);
document.getElementById('chunk-image').src = window.URL.createObjectURL(chunk[0]);

// Revoke Blob URL..
```

아래 이미지는 위 코드의 결과로 왼쪽 이미지는 `#merged-image` 요소, 오른쪽 이미지는 `#chunk-image` 요소입니다.
오른쪽 이미지가 약 1/10로 잘려서 출력되는 것을 볼 수 있습니다.

> 이미지를 시각적으로 분리(조각)하는 용도는 아니며, 이해를 돕기 위해서 첨부합니다.

![Blob Original image VS Sliced image](/JMVvEdT/blob-origin-vs-sliced.jpg)

위 코드의 마지막을 보면 `URL.createObjectURL()`을 사용하였으며, 이는 Blob 객체를 가리키는 URL을 생성하여 DOM에서 참조할 수 있게 합니다.
Blob URL에 대해서 간단하게 알아봅시다.

## Blob URL

Blob 객체를 가리키는 URL을 생성을 위해 [URL 객체](https://developer.mozilla.org/ko/docs/Web/API/URL)의 정적 메소드(Static Method)로 [createObjectURL](https://developer.mozilla.org/ko/docs/Web/API/URL/createObjectURL)과 [revokeObjectURL](https://developer.mozilla.org/ko/docs/Web/API/URL/revokeObjectURL)를 사용할 수 있습니다.

### createObjectURL

`URL.createObjectURL()`은 Blob 객체를 나타내는 URL를 포함한 다음과 같은 DOMString를 생성합니다.(`blob:URL`)
이 Blob URL은 생성된 window의 document에서만(브라우저) 유효합니다.
다른 window에서 재활용할 수 없으며, URL의 수명이 한정되어 있기 때문에 `file:URL`과 다르게 보안 이슈에서 벗어날 수 있습니다.

```plaintext
blob:http://localhost:1234/28ff8746-94eb-4dbe-9d6c-2443b581dd30
```

다음과 같이 활용할 수 있습니다.

```html
<img src="blob:http://localhost:1234/28ff8746-94eb-4dbe-9d6c-2443b581dd30" alt="Blob URL Image" />
```

### revokeObjectURL

`URL.revokeObjectURL()`은 `URL.createObjectURL()`을 통해 생성한 기존 URL을 해제(폐기)합니다.
`revokeObjectURL`을 통해 해제하지 않으면 기존 URL를 유효하다고 판단하고 자바스크립트 엔진에서 [GC](https://developer.mozilla.org/ko/docs/Web/JavaScript/Memory_Management#%EA%B0%80%EB%B9%84%EC%A7%80_%EC%BD%9C%EB%A0%89%EC%85%98) 되지 않습니다.
메모리 누수를 방지하기 위해 생성된 URL을 DOM과 바인딩한 후에는 해제하는 것이 좋습니다.


```js
// Create Blob URL
const blobUrl = window.URL.createObjectURL(blob);

// Revoke Blob URL after DOM updates..
window.URL.revokeObjectURL(blobUrl);
```

## 브라우저 지원 확인

Blob 객체가 브라우저에서 지원 가능한지 확인하려면 다음과 같이 작성할 수 있습니다.

```js
const blobSupported = new Blob(['ä']).size === 2;  // Boolean
```

## AJAX를 이용한 Blob 수신 예제

Promise를 반환하는 `loadXHR` 함수를 추가하고,
요청한 Blob 객체를 수신해,
이미지 태그 `src`에 URL로 삽입하는 예제입니다.

```js
function loadXHR(url) {
  return new Promise((resolve, reject) => {
    try {
      const xhr = new XMLHttpRequest();
      xhr.open("GET", url);
      xhr.responseType = "blob";
      xhr.onerror = event => {
        reject(`Network error: ${event}`);
      };
      xhr.onload = () => {
        if (xhr.status === 200) {
          resolve(xhr.response);
        } else {
          reject(`XHR load error: ${xhr.statusText}`);
        }
      };
      xhr.send();
    } catch (err) {
      reject(err.message);
    }
  });
}
```

```js
loadXHR('https://avatars3.githubusercontent.com/u/16679082?s=460&v=4')
  .then(blob => {
    const url = window.URL.createObjectURL(blob)
    document.getElementById('image').src = url;
    return url;
  })
  .then(url => {
    // After DOM updates..
    process.nextTick(() => {
      window.URL.revokeObjectURL(url);  
    });
  });
```

<script src="https://gist.github.com/WebReflection/2953527.js"></script>

## 참고 자료(References)

https://developer.mozilla.org/ko/docs/Web/API/Blob#%EC%86%8D%EC%84%B1
https://github.com/eligrey/Blob.js/blob/master/Blob.js
https://firejune.com/1788/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%97%90%EC%84%9C%EC%9D%98+BLOB+%EA%B0%9D%EC%B2%B4
https://taegon.kim/archives/5078
http://blog.naver.com/PostView.nhn?blogId=horajjan&logNo=220976788530
