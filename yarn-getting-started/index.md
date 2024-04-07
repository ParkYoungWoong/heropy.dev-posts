---
id: ijqX9h
filename: yarn-getting-started
image: https://heropy.dev/postAssets/ijqX9h/main.jpg
title: Yarn 설치 및 사용법
createdAt: 2017-11-25
group: 시작하기
author:
  - ParkYoungWoong
tags:
  - Yarn
description:
  Meta(Facebook)에서 만든 자바스크립트 패키지 매니저인 Yarn을 사용해 봅시다.
---

Meta(Facebook)에서 만든 자바스크립트 패키지 매니저인 Yarn을 사용해 봅시다.

## Yarn 설치

Yarn은 다양한 OS의 설치를 지원합니다.

### macOS

[Homebrew](https://brew.sh/index_ko.html)를 사용하는 설치

```bash
$ brew install yarn
```

NVM 같은 버전 관리 툴을 사용해야 한다면 Node.js의 설치를 제외하도록 합니다.

```bash
$ brew install yarn --without-node
```

### Windows

[Chocolatey](https://chocolatey.org/)를 사용하는 설치

```bash
$ choco install yarn
```

[Scoop](http://scoop.sh/)를 사용하는 설치

```bash
$ scoop install yarn
```

### NPM

NPM으로 설치할 수도 있습니다.

```bash
$ npm install -g yarn
```

설치가 잘 되었는지 확인합니다.

```bash
$ yarn --version
```

설치 후 전역 사용에 문제가 있다면 Path 설정을 해줘야 합니다.

`.profile`, `.bash_profile`, `.bashrc`, `.zshrc` 등...

```bash
$ export PATH="$PATH:/opt/yarn-[version]/bin"
```

## Yarn 사용법

NPM을 사용한다면 어렵지 않습니다.

프로젝트를 시작할 때 초기화를 하려면(`package.json`을 생성합니다.)

```bash
$ yarn init
```

`package.json`으로부터 의존성 모듈을 설치하려면

```bash
$ yarn
# or
$ yarn install
```

의존성 모듈을 설치하려면

```bash
$ yarn add [package]
$ yarn add [package]@[version]
$ yarn add [package]@[tag]
```

`devDependencies`, `peerDependencies`, `optionalDependencies`와 같은 다른 범주의 의존성을 추가하려면

```bash
$ yarn add [package] --dev
$ yarn add [package] --peer
$ yarn add [package] --optional
```

의존성 모듈을 업그레이드하려면

```bash
$ yarn upgrade [package]
$ yarn upgrade [package]@[version]
$ yarn upgrade [package]@[tag]
```

의존성 모듈을 제거하려면

```bash
$ yarn remove [package]
```

## yarn.lock

`Yarn.lock` 파일은 설치된 모듈의 버전을 저장해 어디서나 같은 버전과 구조의 의존성을 가지게 합니다.
Yarn에서는 자동으로 `yarn install` 때 마다 yarn.lock이 생성됩니다.
`package-lock.json`와 같은 역할을 합니다.