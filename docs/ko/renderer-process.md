# Renderer process

> Electron은 웹페이지를 보여주기 위해 Chromium을 사용하고, 그렇기에 Chromium의 멀티 프로세스 아키텍쳐 또한 사용됩니다. 각각의 Electron 웹페이지는 자체 프로세스로 동작하고 이것을 the renderer process라고 부릅니다.
> 
> 일반적인 브라우저에서 웹 페이지는 대개 샌드박스 환경에서 실행하고 네이티브 리소스에 액세스 할 수 없습니다. 그러나 Electron 유저들은 Node.js APIs 의 낮은 수준의 운영체제 상호 작용을 허용하는 웹 페이지에서 힘이 있다.

**출처 -** [**Electron Documentation**](http://electron.atom.io/docs/tutorial/quick-start/#renderer-process)

---

## `vue`와 `vuex`

### vue components

만약 Vue components에 익숙하지 않다면 [이것](https://kr.vuejs.org/v2/guide/single-file-components.html)을 읽어보시기 바랍니다. components를 사용하면 복잡한 대규모 애플리케이션을 보다 체계적으로 구성 할 수 있습니다. 각 component에는 자체 CSS, template,javascript를 캡슐화 하는 기능이 있습니다. 

Components는 `src/renderer/components`에 저장됩니다. 하위 components를 만들 때 상위 components의 이름이 있는 새 폴더 안에 배치하는 것이 일반적인 프로젝트 구성 방식입니다. 이 방식은 다른 경로로 조정할 때 유용합니다.

```
src/renderer/components
├─ ParentComponentA
│  ├─ ChildComponentA.vue
│  └─ ChildComponentB.vue
└─ ParentComponentA.vue
```

### vue routes

`vue-router`에 대한 더 자세한 정보는 [여기](https://router.vuejs.org/)를 클릭하십시오. 요컨대 싱글 페이지 애플리케이션을 만드는 것이 electron 애플리케이션을 만들 때 훨씬 더 실용적이므로 `vue-router`를 사용하는 것이 좋습니다. 다수의 BrowserWindows 를 관리하고 모든 정보를 교환하고 싶나요? 아마 그러고 싶지 않을 것입니다.

Routes는 `src/renderer/router/index.js` 에 있고 아래와 같이 정의 되어있습니다.

```js
{
  path: '<routePath>',
  name: '<routeName>',
  component: require('@/components/<routeName>View')
}
```

...여기서 `<routePath>` 와 `<routeName>`는 변수입니다. 이 routes는 `src/renderer/App.vue`의 `<router-view>`라는 지시어를 사용하여 component tree와 연결합니다.

##### Notice

`vue-router`를 사용할 때, [**HTML5 History Mode**](https://router.vuejs.org/kr/essentials/history-mode.html)를 사용하지 마십시오!. 이 모드를 엄밀히 말하면 `http`프로토콜을 통해 파일을 제공하기 위한 것이고 production builds에서 Electorn이 파일을 제공하는 `file`프로토콜에서는 제대로 작동하지 않으니 유의하길 바랍니다! 기본 `hash`모드는 필요한 것입니다.

### vuex modules

`vuex`에 대해 설명하는 것은 쉬운 일이 아닙니다. 그러므로 어떤 문제를 해결하거나 그것이 어떻게 작동하는지 더 잘 이해하려면 [이것](http://vuex.vuejs.org/kr/intro.html)을 읽는 것을 추천합니다. 

electron-vue는 `vuex`의 module 구조를 이용하여 다중 데이터 저장소를 만들고 `src/renderer/store/modules`에 저장합니다.

여러 데이터 저장소를 보유하면 조직에 적합할 수는 있습니다만 각각의 데이터 저장소를 하나씩 가져오는 것은 작업이 성가실 수 있습니다. 그러나 걱정마세요! `src/renderer/store/modules/index.js`가 우리를 위해 힘든 일을 대신 할 것입니다! 이 작은 scriptsms `src/renderer/store/index.js` 의 모듈을 한꺼번에 가져옵니다. 만약 이해가 되지 않는다면 주어진 `Counter.js` module을 쉽게 복제 할 수 있다는 것을 알기만 한다면 그것은 "마술처럼" 로드 될 것입니다   :)