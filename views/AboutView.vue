<template>
  <section>
    <h1>VueRouterの設定①</h1>
    <p>まずはindex.htmlのスクリプトタグの中でVueRouterの設定を行います。</p>
    <br />
    <h3>JavaScript</h3>
    <p>公式の見本</p>
    <code>
      <ul>
        <li style="color: aqua">
          const Home = { template: '&lt;div&gt;Home&lt;/div&gt;' }
        </li>
        <li style="color: aqua">
          const About = { template: '&lt;div&gt;About&lt;/div&gt;' }
        </li>
        <br />
        <li style="color: aqua">const routes = [</li>
        <li style="color: aqua">&nbsp;&nbsp;{ path: '/', component: Home },</li>
        <li style="color: aqua">
          &nbsp;&nbsp;{ path: '/about', component: About },
        </li>
        <li style="color: aqua">]</li>
      </ul>
    </code>
    <p>コンポーネントの内容をオブジェクトの中で指定する形です。</p>
    <p>
      しかし、これではページというよりは、メッセージの変遷にしかなりません。
    </p>
    <br />
    <p>そこで.vueファイルを作成して</p>
    <img style="width: 40%" :src="img03Path" /><br /><br />
    <p>vue3_sfc_loaderから.vueファイルを読みとり</p>
    <p>コンポーネントのtemplateとして定義します。</p>

    <code class="code-container">
      <ul>
        <li>const routes = [</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path: "/",
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component:
          <span>() =&gt;</span>
        </li>
        <li>
          <span
            >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadModule("./views/HomeView.vue",
            vue3_sfc_loader_options),</span
          >
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;path:
          "/about",
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component:
          <span> () =&gt;</span>
        </li>
        <li>
          <span
            >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadModule("./views/AboutView.vue",
            vue3_sfc_loader_options),</span
          >
        </li>

        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;];</li>
      </ul>
    </code>
    <br />
    <p>vue3_sfc_loaderの設定では以下のサイトを参考にしました。</p>
    <a href="https://qiita.com/shima-218/items/0830ee555a16e4a39ecb"
      >Qiita shima-218さん</a
    >
    <br />
    <a
      href="https://github.com/FranckFreiburger/vue3-sfc-loader/issues/14#issuecomment-908849863"
      >github.com</a
    >
    <br /><br />
    <p>モジュールのインポート</p>
    <code>
      <ul>
        <li>
          import { loadModule } from
          "https://cdn.jsdelivr.net/npm/vue3-sfc-loader@0.8.4/dist/vue3-sfc-loader.esm.js";
        </li>
        <li></li>
      </ul>
      >
    </code>

    <br /><br />
    <p>実装コード</p>
    <code>
      <ul>
        <li>const vue3_sfc_loader_options = {</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;moduleCache: { vue:
          Vue },
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;getFile(url) {</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;url =
          /.*?\.js|.mjs|.css|.less|.vue$/.test(url) ? url : `${url}.vue`;
        </li>
        <br />
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
      </ul></code
    >

    <br /><br />
    <p>最後にrouter定義をして、スクリプト側は終わりです。</p>
    <code>
      <ul style="color: aqua">
        <li>const router = VueRouter.createRouter({</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;history:
          VueRouter.createWebHashHistory(),
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;routes,</li>

        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;});</li>
      </ul>
      <br /><br />
    </code>
    <br /><br />
  </section>
</template>

<script>
export default {
  data() {
    return {
      img03Path: "assets/03.png",
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
