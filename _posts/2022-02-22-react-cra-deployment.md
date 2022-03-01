---
title: "리액트 CRA의 배포 방법들"
layout: post
tags: [ReactJS, CRA, 배포]
---
(작성중...)

　요새 다양한 사용자의 앱 구동환경에 대해서 고민하던 중, ReactJS 특히 CRA의 배포방법들 대해서 정리가 필요하겠다싶어 포스팅을 하게됐다. 요새 IDE들이 너무 잘되어있어서 프로젝트만들면 알아서 서버만들고 서빙 잘되길래 자세히 알아보려고 하지도않았던 것 같다. 이번 기회에 대충 알고있었던 도큐먼트를 정독하면서 내용을 확인했다. CRA 도큐먼트에 [Deployment](https://create-react-app.dev/docs/deployment/){:target="blank"} 관련하여 잘 정리되어있다. 본 포스트는 원문과는 많이 다르게 현재 내가 필요한 내용 위주로 생략·편집 그리고 의역하여 작성했다.
<!--more-->
<hr/>
 **배포방법들** <br/>
 - serve를 활용한 Static Server
 - Static Server 서빙
 - 상대경로를 설정하여 빌드
<hr/>

　`npm run build`를 활용하여 PROD용 빌드를 한다. 생성된 `build` 디렉토리의 `index.html`를 서빙하면되는데, 스프링이던 닷넷이던 서버 소프트웨어의 제약이 없으므로 원하는 HTTP 서버에 해당 `index.html`파일과 정적 캐시파일(`/static/js/main.<hash>.js` 등...)들을 요청할 수 있도록 셋업하면된다. 각 캐시파일에 대한 자세한 설명은 이 [섹션](https://create-react-app.dev/docs/production-build/){:target="blank"}을 참조하면된다.

<hr/>

## serve를 활용한 Static Server 서빙
```sh
npm install -g serve
serve -s build
serve -h
```
　가장 간단한 방법이다. [serve](https://github.com/vercel/serve) 패키지를 깔고 돌리면, **3000**번 포트로 정적사이트가 서빙된다. 포트 옵션을 커맨드로 바꾸고 싶다면, `-l` 혹은 `--listen` 플래그를 활용하면된다.
<hr/>

## Static Server 서빙
　다음은 [Node](https://nodejs.org/)와 [Express](https://expressjs.com/)를 활용한 서빙방법이다.

```javascript
const express = require('express');
const path = require('path');
const app = express();

app.use(express.static(path.join(__dirname, 'build')));

app.get('/', function (req, res) {
  res.sendFile(path.join(__dirname, 'build', 'index.html'));
});

app.listen(9000);
```
 앞서말했듯이 서버 소프트웨어 제약이 없다. 우리의 CRA는 완전히 `platform-agnostic`🧐이기때문에, 굳이 Node로 정적서버를 구성할 필요도 없다. `build` 폴더로 나오는 정적에셋들이 CRA의 유일한 아웃풋이다.
<hr/>


### Serving the Same Build from Different Paths

> Note: this feature is available with `react-scripts@0.9.0` and higher.

`pushState`와 같은 history API 나 or client-side routing 사용하고 있지않다면, Clinet-Side Routing에서 했던거처럼 URL을 명세할 필요가없다. `package.json`에 `"homepage": "."` 속성을 추가/편집해준다.

<p align="center" style="color:gray">
  <img src="/public/img/react-page-00.PNG" style="border:1px solid #eeeeee;padding: 1rem;margin:1rem;">
</p>

　이건 모든 에셋이 `index.html`의 위치로 부터 상대경로로 참조하게 만든다. Github Pages로 배포할때는, Github Pages의 Base URI를 적어넣고 gh-pages 패키지를 이용하여 deploy 하면된다. 자세한 내용은 이 [섹션](https://create-react-app.dev/docs/deployment/#github-pages){:target="blank"} 참조. `npm run build`해서 마무리해준다.

<p align="center" style="color:gray">
  <img src="/public/img/react-page-01.PNG" style="border:1px solid #eeeeee;padding: 1rem;margin:1rem;">
</p>

  


