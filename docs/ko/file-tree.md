# 파일 구조

### 개발하면서 볼 수 있는 파일들

**주의**: 일부 파일 / 폴더는 `vue-cli`의 초기 설정에서 선택한 옵션에 따라 다를 수 있다는 점을 참고하시기 바랍니다.

```
my-project
├─ .electron-vue
│  └─ <build/development>.js files
├─ build
│  └─ icons/
├─ dist
│  ├─ electron/
│  └─ web/
├─ node_modules/
├─ src
│  ├─ main
│  │  ├─ index.dev.js
│  │  └─ index.js
│  ├─ renderer
│  │  ├─ components/
│  │  ├─ router/
│  │  ├─ store/
│  │  ├─ App.vue
│  │  └─ main.js
│  └─ index.ejs
├─ static/
├─ test
│  ├─ e2e
│  │  ├─ specs/
│  │  ├─ index.js
│  │  └─ utils.js
│  ├─ unit
│  │  ├─ specs/
│  │  ├─ index.js
│  │  └─ karma.config.js
│  └─ .eslintrc
├─ .babelrc
├─ .eslintignore
├─ .eslintrc.js
├─ .gitignore
├─ package.json
└─ README.md
```

#### 최종으로 앱을 빌드 하고 나서의 파일 구조

```
app.asar
├─ dist
│  └─ electron
│     ├─ static/
│     ├─ index.html
│     ├─ main.js
│     └─ renderer.js
├─ node_modules/
└─ package.json
```

여러분이 볼 수 있듯이, 많은 파일들이 최종적으로 앱을 제작할때 제거됩니다. 사용자가 용량이 큰 소프트웨어를 다운로드하는 것을 꺼려하기 때문에 앱을 배포할 때는 거의 필수적으로 해야합니다.