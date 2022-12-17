<template>
  <section>
    <h1>実装見本</h1>
    <br />
    <h2>
      <a href="https://goohayami.github.io/vue-router-template/"
        >GitHub Pages</a
      >
    </h2>
    <p>GitHubのPagesで公開している実装見本です。</p>
    <p>2022年12月17日現在、うまく作動しています。</p>

    <br /><br />
    <h2>
      <a href="https://github.com/goohayami/vue-router-template"
        >gitHubソース</a
      >
    </h2>
    <p>ソースコードです。</p>
    <br /><br />
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
h2 {
  margin: 0;
}
</style>
