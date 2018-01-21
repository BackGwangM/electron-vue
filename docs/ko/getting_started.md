# 시작하기

## 초기 설정

이 공식 문서는 [vue-cli](https://github.com/vuejs/vue-cli)템플릿으로 만들어졌고 최종 설정 프로그램에 사용자 정의하는 옵션이 포함되어 있습니다. `node@^7`이상의 노드를 사용하여야 합니다. electron-vue는 [`yarn`](https://yarnpkg.org)을 공식적으로 권장합니다. 패키지 관리자가 의존성을 훨씬 더 잘 처리하고 `yarn clean`을 사용하면 최종 빌드 크기를 줄이는 데 도움이 되기 때문입니다.

```bash
# Install vue-cli and scaffold boilerplate
npm install -g vue-cli
vue init simulatedgreg/electron-vue my-project

# Install dependencies and run your app
cd my-project
yarn # or npm install
yarn run dev # or npm run dev
```

#### electron에 대해서...

개발자 여러분들의 선택이지만 프로젝트를 설정하고 electron 버전을 고정시키는 것이 좋습니다. 이렇게 하면 같은 프로젝트에서 작업하는 다른 개발자가 다른 electron버전으로 개발하는 것을 방지할 수 있기 때문입니다. Electron은 자주 배포되기 때문에 기능이 항상 변경될 수 있음을 잊지 말아주세요. [추가 정보](http://electron.atom.io/docs/tutorial/electron-versioning/).

#### 윈도우 사용자분들을 위한 메모

만약 `npm install`과정에서 `node-gyp`에 대해서 오류가 발생하면 시스템에 적절한 빌드 도구가 설치되어 있지 않은 것입니다.
빌드 도구에는 Python이나 Visual Studio등이 포함됩니다. 
이 과정을 해결하기 위한 몇가지 패키지가 있습니다. ([@felixrieseberg](https://github.com/felixrieseberg)님께 감사를 전합니다)

첫번째로 점검해야 할 항목은 npm 버전이 옛날 것인지 아닌지를 확인하는 것입니다. 이 부분은 [`npm-windows-upgrade`](https://github.com/felixrieseberg/npm-windows-upgrade)을 사용하여서 해결 할 수 있습니다. 만약 `yarn`을 사용한다면 건너뛰시면 됩니다. 

이것이 완료되면 필요한 빌드 도구를 계속 설정할 수 있습니다. [`windows-build-tools`](https://github.com/felixrieseberg/windows-build-tools)를 사용하면 대부분의 어려운 작업들이 완료됩니다. 그러면 Visual C++ 패키지, Python 등이 전역으로 설치가 됩니다. 

이 시점에서 모든 것이 성공적으로 설치가 되면 좋겠지만 만약 그렇지 않다면 Visual Studio를 새로 설치해야 합니다.
 이것들은 electron-vue 자체의 문제는 아닙니다. \(윈도우 자체 문제일수도 있습니다 ¯\\\_\(ツ\)\_/¯\).

