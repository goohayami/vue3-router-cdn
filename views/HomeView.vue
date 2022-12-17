<template>
  <section>
    <h1>CDNを使用する</h1>
    <p>script タグで CDN から直接 Vue3、vue-router を使用できます。</p>

    <code>
      <ul>
        <p><a href="https://ja.vuejs.org/">Vue.js公式</a></p>
        <li>
          &lt;script
          src="https://unpkg.com/vue@3/dist/vue.global.js"&gt;&lt;/script&gt;
        </li>

        <p><a href="https://router.vuejs.org/">Vue Router公式</a></p>
        <li>
          &lt;script src="https://unpkg.com/vue-router@4"&gt;&lt;/script&gt;
        </li>
      </ul>
    </code>
    <br />
    <p>
      index.htmlのheaderタグに上記のスクリプトを埋め込み、vue-routerの設定を行います。
    </p>
    <img style="width: 80%" :src="img01Path" /><br />
    <br />
    <p>フォルダの構成</p>
    <img style="width: 40%" :src="img02Path" /><br />
    <p>index.jsは作成せず、index.htmlにまとめました。</p>
    <br />
  </section>
</template>

<script>
export default {
  data() {
    return {
      img01Path: "assets/01.png",
      img02Path: "assets/02.png",
    };
  },
};
</script>

<style scoped>
ul {
  width: 600px;
  margin: 0;
  padding: 0;
  list-style: none;
  font-size: 16px;
}

li {
  height: 20px;
  line-height: 1.2rem;
  background-color: black;
  color: wheat;
  margin-left: 8px;
  padding-left: 8px;
  border-radius: 4px;
}
</style>
