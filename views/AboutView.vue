<template>
  <section>
    <h1>VueRouterの設定</h1>
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
    <p>そこで【vue3-sfc-loader】を使って.vueファイルを読み込みます。</p>
    <br />

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

    <br /><br /><br /><br />
    <p>router定義</p>
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
    </code>
    <br /><br />
  </section>
</template>

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
