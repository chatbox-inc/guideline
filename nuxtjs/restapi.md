# Nuxt.js における REST API の通信

必ず、`@nuxtjs/axios` を用いて API 通信を行うこと。

単体の axios を導入して、オリジナルの axios プラグインを自作するよりも 
axios モジュールのほうが高機能で便利なため。

## Axios

- axios モジュール自体の拡張も可能 [ref](https://axios.nuxtjs.org/extend)
- API アクセスは全て Store を経由させること。
- 可能な限り依存はサービスクラスを経由刺せる。
- ページコンポーネントやPlugins内で $axios へのアクセスを行わず、
  Store Action 経由でのみ Axios を利用すること。

```js
{
  actions: {
    async getIP ({ commit }) {
      const ip = await this.$axios.$get('http://icanhazip.com')
      commit('SET_IP', ip)
    }
  }
}
```
