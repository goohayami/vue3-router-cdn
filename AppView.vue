<template>
  <p>Vue3 CDNでVue-routerを使う！</p>
  <h1>Hello App!</h1>
  <nav>
    <router-link to="/">Go to Home</router-link> |
    <router-link to="/about">Go to About</router-link>
  </nav>

  <router-view></router-view>
</template>

<style>
nav{
  background-color: bisque;
  
}
</style>
