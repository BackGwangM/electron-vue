# 전역 구성

electron-vue는 전처리, 번들링, 그리고 앱을 빌드할 때 [webpack](https://github.com/webpack/webpack)을 사용합니다. 기본 설정은 일반적인 것이므로 대부분의 요구 사항을 충족해야합니다. 빠른 수정을 위해 루트 디렉토리에 `confing.js`가 생깁니다. 
`webpack.main.config.js`와 `webpack.renderer.config.js`를 직접 수정함으로써 원하는 대로 커스터마이징을 할 수 있습니다.

#### `config.js`
**참고**: 일부 옵션은 `vue-cli` 초기설정에 따라 다를 수 있으니 유의하시기 바랍니다.
Some options may differ based on the settings choosen during `vue-cli` scaffolding.

```js
{
  // electron 애플리케이션의 이름
  // 프로덕션 빌드에 사용됩니다.
  name: 'app',

  // ESLint 사용 유무
  // `.eslintrc.js`에서 더 많은 변경이 가능합니다.
  eslint: true,

  // webpack-dev-server의 포트
  port: 9080,

  // electron-packager 옵션
  // `당신의 앱을 만들어보세요!(building_your_app)`에서 더 많은 정보를 볼 수 있습니다.
  building: {
    arch: 'x64',
    asar: true,
    dir: path.join(__dirname, 'app'),
    icon: path.join(__dirname, 'app/icons/icon'),
    ignore: /\b(src|index\.ejs|icons)\b/,
    name: pkg.name,
    out: path.join(__dirname, 'builds'),
    overwrite: true,
    platform: process.env.PLATFORM_TARGET || 'all'
  }
}
```
