<template>
  <section>
    <h1>VueRouterの設定②</h1>
    <p>まずはindex.htmlのスクリプトタグの中でVueRouterの設定を行います。</p>
    <br />
    <h3>App.vue</h3>
    <code>
      <ul>
        <li>&lt;template&gt;</li>
        <li>&nbsp;&nbsp;&lt;header&gt;&lt;/header&gt;</li>
        <li>&nbsp;&nbsp;&lt;div class="main-container"&gt;</li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;nav&gt;</li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-link class="router"
          to="/"&gt;&lt;/router-link&gt;&lt;br /&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-link class="router"
          to="/about"&gt;&lt;/router-link&gt;&lt;br /&gt;
        </li>
        <li>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-link class="router"
          to="/aboutHtml"&gt;&lt;/router-link&gt;&lt;br /&gt;
        </li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;/nav&gt;</li>
        <li></li>
        <li>&nbsp;&nbsp;&nbsp;&nbsp;&lt;router-view&gt;&lt;/router-view&gt;</li>
        <li>&nbsp;&nbsp;&lt;/div&gt;</li>
        <li>&lt;/template&gt;</li>
      </ul>
    </code>
    <p>ナビをサイドバーにするために、linkとviewをdivで囲っていますが</p>
    <p>
      そのままだとnavの部分が上部ヘッダーとなり、router-viewでページの変遷がなされます。
    </p>
  </section>
</template>

<script></script>

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
