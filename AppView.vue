<template>
  <div class="title">
    <h1>Hello Vue3!</h1>
    <p>Vue3 CDNでVue-routerを使う!</p>
  </div>
  <div class="main-container">
    <nav>
      <router-link to="/">CDNリンク</router-link> <br />
      <router-link to="/about">Go to About</router-link><br />
    </nav>
    <router-view></router-view>
  </div>
</template>

<style>
.title {
  height: 50px;
  line-height: 3rem;
  padding-left: 1rem;
  display: flex;
  background-color: blueviolet;
}
h1 {
  margin: 0;
  margin-right: 2rem;
  font-size: 32px;
}

p {
  margin: 0;
  font-size: 20px;
}
nav {
  background-color: bisque;
  width: 250px;
  height: 600px;
  font-size: 20px;
  line-height: 3rem;
  padding-top: 1rem;
  padding-left: 0.5rem;
}
.main-container {
  display: flex;
}
</style>
