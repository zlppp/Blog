### state
* 保存共享数据
* 不推荐直接修改共享数据 ` this.$store.state.count = 1 ` ，如果多个组件都修改了共享数据，后期如果发生错误，则需要把修改共享数据的组件都要检查一遍
* 单向数据流

```js
  cosnt stroe = new Vuex.store({
    state: {
      count: 0
    },
    mutations: { // 修改state
      add (state, num) {
        state.count = state.count + num
      }
    },
    getters: { // 计算state
      format (state) {
        return '共' + state.count + '次‘
      }
    },
    actions: { // 异步修改state，还是需要commit，调用mutatios方法去修改
      fn (store, data) {
        return new Promise((resolve, reject) => {
          
        })
        setTimeout (() => {
          store.commit('add', data)
        }, 2000)
      }
    }
  })

  this.$store.state.count
```

### getters
* 保存计算属性，缓存计算结果，对数据进行计算



### mutations
* 用于保存修改共享数据的方法
* 在 `mutaions` 中定义方法，会自动传入 `state` 参数, `state`中就保存了共享数据
* 通过 `commit` 调用方法

```js
  this.$store.commit('add')
```


### actions
* 异步修改 `state`,但是还是需要 `commit` 到 `mutations` 中，本质也是函数
* 通过调用 `dispath` 调用 `actions` 中的异步方法

```js
  actions: {
    actionsA () {
      return new Promise((resolve, reject) => {
        commit('add')
        resolve()
      })
    }
  }

  this.$store.dispath('fn', 11)
```

### modules
* 将store分割成模块，每个模块拥有自己的 `state`, `mutaion`, `action`, `getter`
```js
  const moduleA = {
    state: {},
    mution: {},
    action: {},
    getter: {}
  }
```

### 辅助函数
```js
import { mapState, mapGetter, mapMutation, mapActions } from 'vuex'

...
computed: {
  ...mapState([
    ...
  ]),
  ...mapGetter([
    ...
  ])
},
methods: {
  ...mapMutation([
    ...
  ]),
  ...mapAcions([
    ...
  ])
}
```
