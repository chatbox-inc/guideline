## Vuex Store 

- Vuex Store の各要素は ページコンポーネント内でのみ参照が可能.
  - `components` フォルダ内の各種コンポーネントは、 Vuex を利用しない。
- mutations は action からのみ参照される。

## Vuex の参照方法

- 注入された Vuex Store を利用する方法
- モジュール毎に mapper を公開する方法
- モジュール毎に モジュール名を公開する方法

### 注入された Vuex Store を利用する方法

もっとも一般的な手法で Vue 内部に注入された `store` から Vuex にアクセスする。

```js: hoge
export default {
    computed:{
        user(){
            return this.$store.state.user
        }
    },
    methods: {
        login(){
            this.$store.dispatch("LOGIN")
        }
    }
}
```

モジュール単位でのアクセスにも 名前空間を利用して `/` などの文字列でアクセスする。

### モジュール毎にMapper を公開する方法 

mapperを利用して Vuex への参照を利用する方法

- アプリケーション内で`$store` 文字列を利用しない。
- 代わりにモジュールから公開されたmapper を利用して Vuex Store を参照する。



### モジュール内でモジュール名を公開する方法

モジュールからモジュール名を取得して、
vuex 共通の mapperを利用したて参照を利用する方法

- アプリケーション内で`$store` 文字列を利用しない。
- 代わりにモジュールから公開されたモジュール名と Vuex の Mapper を利用して Vuex Store を参照する。

## Vuex 同士の依存関係

- vuex モジュール同士の依存関係は vue コンポーネント側で解決する。
  - rootStateの参照は 許容するが、 rootState 経由で他のモジュールにアクセスしないいこと
  - どうしても他のモジュールから照会される要素は、ルートモジュールに置く
