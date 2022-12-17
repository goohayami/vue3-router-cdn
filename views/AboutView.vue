<template>
  <section>
    <h1>VueRouterの設定</h1>
    <p>まずはindex.htmlのスクリプトタグの中でVueRouterの設定を行います。</p>
    <br />
    <h3><span>JavaScript</span></h3>

    <p>routes path指定</p>
    <code class="code-container">
      <ul>
        <li>const routes = [</li>
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
          "/about",
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;component:
          () =&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;loadModule("./views/AboutView.vue",
          vue3_sfc_loader_options),
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;];</li>
      </ul>
    </code>

    <p>router定義</p>
    <code>
      <ul>
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
  color: wheat;
}

span {
  color: red;
}
h3 {
  margin: 0;
  padding: 0;
}
</style>
