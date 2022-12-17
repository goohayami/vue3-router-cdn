<template>
  <section>
    <h1>実装コード</h1>
    <h3>ファイル構成</h3>
    <img style="width: 60%" :src="img04Path" /><br />

    <h3>index.html</h3>
    <code>
      <ul>
        <li>&lt;!DOCTYPE html&gt;</li>
        <li>&lt;html lang="en"&gt;</li>
        <li>&nbsp;&nbsp;&lt;head&gt;</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&lt;script
          src="https://unpkg.com/vue@3/dist/vue.global.js"&gt;&lt;/script&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&lt;script
          src="https://unpkg.com/vue-router@4"&gt;&lt;/script&gt;
        </li>
        <li>&nbsp;&nbsp;&lt;/head&gt;</li>
        <li>&nbsp;&nbsp;&lt;body&gt;</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;div id="app"&gt;&lt;/div&gt;</li>
        <li></li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;script type="module"&gt;</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// vue3_sfc_loaderモジュール
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;import { loadModule } from
          "https://cdn.jsdelivr.net/npm/
          vue3-sfc-loader@0.8.4/dist/vue3-sfc-loader.esm.js";
        </li>
        <br /><br />
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// 設定</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;const vue3_sfc_loader_options = {
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;moduleCache: { vue:
          Vue },
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;getFile(url) {</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;url =
          /.*?\.js|.mjs|.css|.less|.vue$/.test(url) ? url : `${url}.vue`;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;const type
          = /.*?\.js|.mjs$/.test(url)
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;?
          ".mjs"
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:
          /.*?\.vue$/.test(url)
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;?
          ".vue"
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:
          /.*?\.css$/.test(url)
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;?
          ".css"
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:
          ".vue";
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;const
          getContentData = (asBinary) =&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fetch(url).then((res)
          =&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;!res.ok
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;?
          Promise.reject(url)
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:
          asBinary
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;?
          res.arrayBuffer()
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;:
          res.text()
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;);
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return {
          getContentData: getContentData, type: type };
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;addStyle(textContent)
          {
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;let
          styleElement = document.createElement("style");
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.head.insertBefore(
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Object.assign(styleElement,
          { textContent }),
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;document.head.getElementsByTagName("style")[0]
          || null
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;);</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;handleModule(type,
          getContentData, path, options) {
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;switch
          (type) {
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;case
          ".css":
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return
          options.addStyle(getContentData(false));
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;case
          ".less":
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;console.error(".......");
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;log(type, ...args) {
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;console.log(type,
          ...args);
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};</li>
        <li></li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// Vue.js
          アプリケーションインスタンス
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;const routes = [</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path: "/",
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component:
          () =&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadModule("./views/HomeView.vue",
          vue3_sfc_loader_options),
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path:
          "/add1",
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component:
          () =&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadModule("./views/AddPage_1.vue",
          vue3_sfc_loader_options),
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path:
          "/add2",
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component:
          () =&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadModule("./views/AddPage_2.vue",
          vue3_sfc_loader_options),
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path:
          "/add3",
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component:
          () =&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadModule("./views/AddPage_3.vue",
          vue3_sfc_loader_options),
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;];</li>
        <li></li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;const router =
          VueRouter.createRouter({
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;history:
          VueRouter.createWebHashHistory(),
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;routes,</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//
          ここからページトップに戻る操作
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scrollBehavior(to,
          from, savedPosition) {
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return {
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;top:
          0,
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// ここまで</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//
          https://into-the-program.com/vue-router-set-scroll-position-to-top/
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// Into the Program
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;});</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;const app = Vue.createApp({</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;components: {</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;App:
          Vue.defineAsyncComponent(() =&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadModule("./AppView.vue",
          vue3_sfc_loader_options)
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;),</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;template:
          `&lt;App/&gt;`,
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;});</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;app.use(router);</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;app.mount("#app");</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;/script&gt;</li>
        <li>&nbsp;&nbsp;&lt;/body&gt;</li>
        <li>&lt;/html&gt;</li>
        <li></li></ul
    ></code>
    <h3>App.vue</h3>
    <code>
      <ul>
        <li>&lt;template&gt;</li>
        <li>&nbsp;&nbsp;&lt;header&gt;&lt;/header&gt;</li>
        <li>&nbsp;&nbsp;&lt;div class="main-container"&gt;</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;nav&gt;</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-link class="router"
          to="/"&gt;HOME&lt;/router-link&gt;&lt;br /&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-link class="router"
          to="/add1"&gt;ADD1&lt;/router-link&gt;&lt;br /&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-link class="router"
          to="/add2"&gt;ADD2&lt;/router-link&gt;&lt;br /&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-link class="router"
          to="/add3"&gt;ADD3&lt;/router-link&gt;&lt;br /&gt;
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;/nav&gt;</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-view&gt;&lt;/router-view&gt;</li>
        <li>&nbsp;&nbsp;&lt;/div&gt;</li>
        <li>&lt;/template&gt;</li>
        <li></li>
        <li>&lt;script&gt;&lt;/script&gt;</li>
        <li></li>
        <li>&lt;style&gt;</li>
        <li>nav {</li>
        <li>&nbsp;&nbsp;display: flex;</li>
        <li>&nbsp;&nbsp;justify-content: space-between;</li>
        <li>&nbsp;&nbsp;padding: 5px 40px;</li>
        <li>&nbsp;&nbsp;background-color: azure;</li>
        <li>}</li>
        <li>&lt;/style&gt;</li>
        <li></li></ul
    ></code>
  </section>
</template>

<script>
export default {
  data() {
    return {
      img04Path: "assets/04.png",
    };
  },
};
</script>

<style scoped>
ul {
  width: 600px;
  margin: 0;
  padding-top: 8px;
  padding-bottom: 8px;
  list-style: none;
  font-size: 16px;
  background-color: black;
  border-radius: 4px;
}

li {
  height: 20px;
  line-height: 1.2rem;
  color: whitesmoke;
}

span {
  color: rgb(64, 224, 115);
}
h3 {
  color: red;
  margin: 0;
  padding: 0;
}
</style>
