### storage

- vuex刷新页面存储的数据会清空，所以用storage存储
- [Vue-ls插件](https://www.jianshu.com/p/170aafb0b13c)

### 使用,设置token 存储时间
- 登录登出token处理
```
actions: {
    // 登录的token从接口返回
    Login ({ commit }, userInfo) {
      return new Promise((resolve, reject) => {
        login(userInfo).then(response => {
          const result = response.result
          // Vue.ls.set(name, value, expire)
          Vue.ls.set(ACCESS_TOKEN, result.token, 7 * 24 * 60 * 60 * 1000)
          commit('SET_TOKEN', result.token)
          resolve()
        }).catch(error => {
          reject(error)
        })
      })
    },
    // 登出
    Logout ({ commit, state }) {
      return new Promise((resolve) => {
        logout(state.token).then(() => {
          resolve()
        }).catch(() => {
          resolve()
        }).finally(() => {
          commit('SET_TOKEN', '')
          commit('SET_ROLES', [])
          Vue.ls.remove(ACCESS_TOKEN)
        })
      })
    }
```

### axios里 token 是同一个