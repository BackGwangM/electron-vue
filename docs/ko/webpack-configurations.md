# Webpack Configurations

electron-vue는 `.electron-vue/` 디렉토리에있는 세 개의 webpack 구성 파일로 압축되어 제공됩니다. `web` 출력을 선택적으로 사용하는 것 외에도, `main`과 `renderer`의 설정은 비슷합니다. Both make use of `babel-preset-env` to target `node@7` features, use `babili`, and treat all modules as `externals`.

### `.electron-vue/webpack.main.config.js`

electron의 `main` process를 설정합니다. 초기 설정은 다소 모자라지만 일반적인 `webpack` 사례들을 포함합니다.

### `.electron-vue/webpack.renderer.config.js`

electron의 `renderer` process를 설정합니다. 이 파일은 Vue 애플리케이션을 설정합니다. `vue-loader`와 공식 `vuejs-templates/webpack` 표준 문안에 사용할 수 있는 다른 많은 설정이 있습니다.

##### White-listing Externals

이 설정에 대해 고려해야 할 한 가지 중요한 점은 Webpack이 특정 모듈을 Whitelist로 지정하여 Webpack `externals`로 취급하지 않게끔 할 수 있다는 것입니다. 이 기능이 필요한 Use case는 많지 않지만 원시 `*.vue` 컴포넌트를 제공하는 Vue UI 라이브러리의 경우에는 화이트리스트가 필요하므로 `vue-loader`가 그것들을 컴파일 할 수 있습니다. 다른 Use Case로는 `vue`를 설정하여 전체 컴파일러 + 런타임 빌드를 가져오는 것처럼 webpack의 `alias`를 사용하는 것입니다. 이 때문에 `vue`는 whitelist에 이미 있습니다.

### `.electron-vue/webpack.web.config.js`

브라우저를 위한 `renderer`프로세스 소스 코드를 빌드 하는 것을 목표로 합니다. 이 설정은 웹을 퍼블리싱할 때 좋은 출발 기반으로 제공됩니다. **electron-vue 는 제공되는 것 이상으로 Web 출력을 지원하지 않습니다** 웹 출력에 관련된 문제는 지연되거나 닫힐 가능성이 높습니다.

