# 작성 가이드

- `id`, `filename` 속성은 최종 검토 이후 게시 직전에 자동 생성되므로, 따로 작성하지 않아야 합니다.
- `author` 속성은 작성자의 GitHub ID를 작성하세요.
- 최상위 제목(`<h1>`, `#`)은 '목차'로 인식하지 않습니다.
- 최상위 제목은 처음 1개만 작성하고, 2개 이상 작성하지 마세요.
- `createdAt`, `updatedAt` 속성은 `YYYY-MM-DD` 형식의 날짜 정보입니다.
- `description` 속성(간단한 설명)은 200자 이하로 작성하세요.

## 메타데이터

마크다운 게시글 최상단에 작성하는 메타데이터(Metadata 혹은 Front Matter)는 게시글의 외적인 정보를 포함합니다.  
메타데이터는 다음과 같은 형식(Type)으로 작성합니다.

```ts
interface PostMeta {
  id?: string // 자동 생성
  filename?: string // 자동 생성
  title: string
  createdAt: string
  updatedAt?: string // 생성 후 수정한 경우만 작성
  group: string
  author: string[]
  tags: string[]
  description: string
}
```

### 시작 템플릿

```markdown
---
title: <최상위 제목>
createdAt: <최초 작성일>
group: <그룹(카테고리)>
author: 
  - <작성자(복수)>
tags: 
  - <태그(복수)>
description: 
  <간단한 설명>
---

# <최상위 제목>

<내용>
```

### 작성 예시

```markdown
---
title: CSS Flex 완벽 가이드
createdAt: 2018-11-24
updatedAt: 2023-11-05
group: CSS
author: 
  - ParkYoungWoong
tags:
  - CSS
  - Flex
description:
  CSS Flex는 효율적인 레이아웃 설계를 위한 기술로, 컨테이너 내 항목의 공간 배분과 정렬을 유연하게 관리합니다. 이를 통해 반응형 디자인 레이아웃이 쉬워지고 복잡한 계산 없이도 요소를 원하는 대로 배치할 수 있습니다.
---

# CSS Flex 완벽 가이드

대부분 사이트는 전체 레이아웃이 수직 구성이며 '위-아래'로 스크롤 하여 사용합니다.
레이아웃을 구성할 때 가장 많이 사용하는 요소(Elements)들이 기본적으로 블록(Block) 개념으로 표시(Display)되며 이는 뷰(View)에 수직(위에서 아래로)으로 쌓이기 때문에 수직 구성은 상대적으로 쉽게 만들 수 있습니다.
...
```