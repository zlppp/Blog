### 问题
- 将用户信息存储在local中，同时登录两个用户，local中token会替换为最新登录用户的token
- 我去更改旧用户的密码等，会直接更改了新用户的密码
- 因为此时的token为新用户的token，而页面展示的用户信息还是旧用户的登录信息

### 解决思路
### 1、当前登录用户token备份一份到session中
- 每次进入页面前都存储当前用户token在session中
- 请求接口时，先取session中的token，再取local中的

```js
// router.js
router.beforEach((to, from, next) => {
  // 每次进入页面前都存一份当前用户token
  store.commit('SET_CURRENT_TOKEN', userInfo.accessToken)
})

// http.js
// token不一致则表示同时登录了两个用户，刷新页面
if ((session.getItem('currentToken') && local.getItem('accessToken')) && session.getItem('currentToken') !== local.getItem('accessToken')) {
  window.location.href = '/'
}


// 不需要token的接口数组
const notTokenMethod = [
  'com.fshows.lifecircle.college.login'
]
if (!urlMethod.includes(notTokenMethod)) {
  if (!(session.getItem('currentToken') || local.getItem('accessToken'))) {
    throw new Error('')
  }
}

```