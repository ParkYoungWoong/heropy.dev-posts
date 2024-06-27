---
id: QWrwz3
filename: sveltekit
image: https://heropy.dev/postAssets/QWrwz3/main.jpg
title: (초안) SvelteKit
createdAt: 2024-06-27
group: Svelte
author:
  - ParkYoungWoong
tags:
  - Svelte
  - SvelteKit
description:
  SvelteKit은 Svelte 프레임워크로, 서버 사이드 렌더링(SSR) 기반의 빠른 빌드 속도와 간편한 라우팅 시스템을 제공하며, SEO 최적화 등 성능 향상을 위한 여러 기능을 제공합니다.
---

## 개요

/// message-box --icon=error
이 글은 초안으로, 아직 작성 중인 문서입니다.
현재 블로그는 SvelteKit으로 제작했고, 관리 중에 파편화된 관련 내용을 꾸준히 정리하려고 합니다.
///

[SvelteKit](https://kit.svelte.dev/)은 [Svelte](https://svelte.dev/) 프레임워크로, 서버 사이드 렌더링(SSR) 기반의 빠른 빌드 속도와 간편한 라우팅 시스템을 제공하며, SEO 최적화 등 성능 향상을 위한 여러 기능을 제공합니다.
2021년, Svelte의 창시자인 [Rich Harris](https://github.com/Rich-Harris)가 [Vercel](https://vercel.com/) 팀에 합류하면서 더욱 Vercel 친화적으로 쉬운 사용성을 갖추게 되었습니다.

### 설치 및 구성

다음 명령으로 SvelteKit 프로젝트를 설치합니다.
TypeScript와 ESLint 그리고 Prettier를 사용합니다.

```bash
# npm create svelte@latest sveltekit-project
# npm create svelte@latest .
npm create svelte@latest <경로|프로젝트이름>
    ✔ Which Svelte app template? - SvelteKit demo app
    ✔ Add type checking with TypeScript? - Yes, using TypeScript syntax
    ✔ Select additional options (use arrow keys/space bar) - Select all
```

#### SCSS

SCSS를 사용하기 위해 다음 패키지를 설치합니다.
설치 후 바로 `*.scss` 파일을 사용할 수 있습니다.

```bash
npm i -D sass
```

```scss --path=/src/app.scss
html {
  --color-font: #333;
  body {
    color: var(--color-font);
  }
}
```

```svelte --path/src/routes/+layout.svelte --caption=SCSS 사용 예시
<script lang="ts">
  // ...
  import '../app.scss'
</script>
```

### 경로 별칭

새로운 경로 별칭이 필요하면, 다음과 같이 `alias` 옵션을 사용할 수 있습니다.

/// message-box --icon=warning
내장된 `$lib` 경로 별칭과 중복되지 않도록 주의하세요!
`$lib` 경로 별칭은 `config.kit.files.lib` 옵션에서 제어할 수 있습니다.
///

```js --path=/svelte.config.js --line-active=6-7,10 --line-error=5
// ...
const config = {
  kit: {
    alias: {
      // $lib: './src/lib',
      $components: './src/components',
      $store: './src/store'
    },
    files: {
      lib: './src/lib'
    }
  }
}
export default config
```

```svelte
<script lang="ts">
  import TextField from '$components/TextField.svelte'
  import { scrollPaddingTop } from '$store/page'
</script>
```

### 환경변수

```plaintext --path=/.env --caption=환경변수 예시
CREDENTIALS=1234
API_KEY=5678
PUBLIC_CLIENT_URL=https://heropy.dev
PUBLIC_DATABASE_ANON_KEY=abcd
```

환경변수는 기본적으로 서버 측에서만 사용할 수 있습니다.
`$env/static/private` 모듈에서 가져옵니다.

```ts
import { CREDENTIALS, API_KEY } from '$env/static/private'
```

클라이언트에서 사용할 환경변수는, `PUBLIC_` 접두사를 붙여야 합니다.
이는 해당 환경변수가 클라이언트에서 노출되어도 문제가 없다는 것을 명시적으로 표현하기 위함입니다.
`$env/static/public` 모듈에서 가져옵니다.

```ts
import { PUBLIC_CLIENT_URL, PUBLIC_DATABASE_ANON_KEY } from '$env/static/public'
```

필요하면, 원하는 접두사를 추가하거나 수정할 수 있습니다.

```js --path=/svelte.config.js --line-active=8 --line-error=7
// ...
const config = {
  kit: {
    env: {
      publicPrefix: 'PUBLIC_', // 기본값!
      privatePrefix: 'SECRET_'
    }
  }
}
export default config
```

```plaintext --path=/.env --caption=접두사를 추가한 환경변수 예시
SECRET_CREDENTIALS=1234
SECRET_API_KEY=5678
PUBLIC_CLIENT_URL=https://heropy.dev
PUBLIC_DATABASE_ANON_KEY=abcd
```

```ts
import { SECRET_CREDENTIALS, SECRET_API_KEY } from '$env/static/private'
import { PUBLIC_CLIENT_URL, PUBLIC_DATABASE_ANON_KEY } from '$env/static/public'
```

### 폰트 미리로드

`font-display: swap`을 사용해 폰트를 출력하지 못하는 상황(FOIT, Flash Of Invisible Text)을 방지할 수 있지만, 폰트 로드 후 시스템 폰트가 교체되는 현상(FOUT, Flash Of Unstyled Text)이 발생하므로, 다음과 같이 설치한 폰트를 가져와 미리로드 경로로 지정할 수 있습니다.

/// message-box --icon=warning
다른 로딩 프로세스가 차단되어 초기 로드가 매우 느려질 수 있으니, 페이지에서 사용하는 주요 폰트만 미리로드하세요!
///

```svelte --path=/src/+layout.svelte
<script lang="ts">
  import pretendard from '$lib/font/PretendardVariable.woff2'
  import '$lib/font/pretendardvariable.css'
</script>

<link
  rel="preload"
  href={pretendard}
  as="font"
  type="font/woff2"
  crossorigin="anonymous" />
```

폰트 사용을 잊지 마세요!

```css --path=/src/app.css
body {
  font-family: 'Pretendard Variable', Pretendard, -apple-system, BlinkMacSystemFont, system-ui,
    Roboto, 'Helvetica Neue', 'Segoe UI', 'Apple SD Gothic Neo', 'Noto Sans KR', 'Malgun Gothic',
    'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol', sans-serif;
}
```