## tailwindcssコーディング方法共通化 

基本的にはTailwindのクラスのみを使用する。    
position指定など、tailwindで実現しづらい場合のみコンポーネント内にcssを記述しても良い。

各セクションで使用されるボタンのような要素はコンポーネント化する。  
コンポーネントには役割に応じて先頭にprefixをつける。
UI系 UiButton.vue, UiTitle.vue  
Layout系 LHeader.vue, LFooter.vue

/components配下にあるコンポーネントはimport文を使用せずに読み込む事が出来ます。  
https://github.com/chatbox-inc/chatbox2020/issues/38
