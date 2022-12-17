<template>
  <header>
    <h1>Vue3 vue-router</h1>
    <p>CDNだけでSPAを実現</p>
  </header>
  <div class="main-container">
    <nav>
      <router-link class="router" to="/">CDNを使用する</router-link><br />
      <router-link class="router" to="/about">VueRouterの設定①</router-link
      ><br />
      <router-link class="router" to="/aboutHtml">VueRouterの設定②</router-link
      ><br />
      <router-link to="/template">実装コード</router-link><br />
    </nav>

    <router-view></router-view>
  </div>
</template>

<script setup></script>

<style>
header {
  z-index: 999;
  padding: 10px 20px;
  width: 100%;
  line-height: 3rem;
  padding-left: 1rem;
  display: flex;
  background-color: rgb(210, 191, 227);
  position: fixed;
}
h1 {
  margin: 0;
  margin-right: 2rem;
  font-size: 32px;
}

p {
  margin: 0;
  font-size: 20px;
  line-height: 1.5rem;
}
nav {
  background-color: rgb(244, 240, 236);
  font-size: 20px;
  line-height: 3rem;
  padding-top: 5rem;
  padding-left: 2rem;

  /* これがスクロールのもと */
  position: sticky;
  top: 0;

  /*横半分25%　縦を100vhにする*/
  width: 250px;
  height: 85vh;
}

.router {
  text-decoration: none;
}
.router:hover {
  background-color: pink;
  border-radius: 4px;
}

.main-container {
  display: flex;
  background-color: rgb(247, 245, 245);
}
</style>
