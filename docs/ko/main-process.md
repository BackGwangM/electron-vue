# Main Process

> Electron에서 `package.json`의 `main` 스크립트를 실행하는 프로세스를 **메인 프로세스**라고 부릅니다. 메인 프로세스에서 실행되는 스크립트는 웹 페이지를 만들어서 GUI를 표시 할 수 있습니다.

**출처 -**  [**Electron Documentation**](http://electron.atom.io/docs/tutorial/quick-start/#main-process)

---

`main` 프로세스는 본질적으로 완전한 Node 환경이기 때문에 초기 프로젝트 구조를 보면 파일이 두 개밖에 없습니다.

#### `src/main/index.js`

이 파일은 애플리케이션의 중요한 파일이며 `electron`이 부팅되는 파일입니다. 또한 `webpack`의 entry file로 사용됩니다. 모든 `main` 프로세스 작업은 여기서부터 시작해야합니다.

#### `app/src/main/index.dev.js`

이 파일은 `electron-debug`와 `vue-devtools`를 설치하기 때문에 개발할 때만 사용됩니다.
이 파일은 수정할 필요는 없지만 개발 요구 사항을 확장하는 데 사용할 수 있습니다.

## `__dirname` 와 `__filename`을 사용할 때

`main`프로세스가 `webpack`을 사용하여 번들로 제공되기 때문에 `__dirname`과 `__filename`을 사용하면 산출물에서 기대되는 값을 얻을 수 없습니다. [**File Tree**](/file-tree.md)문서를 보면, 앱을 빌드하는 과정에서 `main.js`가 `dist/electron` 폴더에 위치한다는 것을 알 수 있습니다. 이 것을 바탕으로 적절하게 `__dirname` 과 `__filename` 을 사용하세요.

**만약 `static/` 디렉토리에 대한 경로가 필요하다면 [**Using Static Assets**](/using-static-assets.md)를 읽어서 `__static` 변수에 대해 알아보세요**

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



