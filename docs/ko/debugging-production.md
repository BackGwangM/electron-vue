# 디버깅

### 메인 프로세스

개발중인 애플리케이션을 실행할 때 `메인` 프로세스에서 원격 디버거가 언급되는 메세지가 표시될 수 있습니다. `electron@^1.7.2`가 나온 이후로 Inspect API를 통한 원격 디버깅이 도입 되었으며 구글 크롬에서 제공되는 링크나 Visual Studio Code와 같이 기본포트 5858을 사용하여 프로세스에 원격으로 연결할 수 있는 다른 디버거 을 통해서 제공된 링크를 통해 쉽게 접근 할 수 있습니다.

```bash
┏ Electron -------------------

  Debugger listening on port 5858.
  Warning: This is an experimental feature and could change at any time.
  To start debugging, open the following URL in Chrome:
      chrome-devtools://devtools/bundled/inspector.html?experiments=true&v8only=true&ws=127.0.0.1:5858/22271e96-df65-4bab-9207-da8c71117641

┗ ----------------------------
```

### 프로덕션 빌드

###### 주의

 다 만들어진 애플리케이션을 디버깅 하는 것이 가능할 지라도 개발 과정에서 발견된 것과 비교하여 프로덕션 코드가 최소화되어 읽기 어렵다는 것을 알아두셨으면 좋겠습니다.

##### `renderer` 프로세스

여기까지는 개발하는데 큰 차이점이 별로 없습니다. [`BrowserWindow` APIs](https://electron.atom.io/docs/api/web-contents/#contentsopendevtoolsoptions)를 사용하여 개발자 도구를 실행할 수 있습니다. electron-vue의 초기 설정을 사용한다면 `src/main/index.js`에 코드 스니펫들을 추가한 뒤에 `new BrowserWindow`를 구성하고, 시작할 때 개발자 도구를 열면 됩니다.

```js
mainWindow.webContents.openDevTools()
```

##### `main` 프로세스

위에서 언급한 것과 비슷하게  애플리케이션을 원격으로 디버깅하기위해 `main`프로세스에  외부 디버거를 연결할 수도 있습니다. 프로덕션의 디버거를 실행하기 위하여 `src/main/index.js`에서 `app`을 가져온 다음 follow snippet을 추가할 수 있습니다. 그러면 Google Chrome에서 `chrome://inspect`를 접속하여 연결할 수 있습니다.

```js
app.commandLine.appendSwitch('inspect', '5858')
```



