<template>
  <section>
    <h1>CDN の Vue を使用する</h1>
    <p>script タグで CDN から直接 Vue3、vue-router を使用できます</p>
    <!-- <img :src="imgPath" /><br /> -->
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
      </ul></code
    >
    <br />
    <p>ここはテキスト</p>

    <p>ここはテキスト</p>
    <p>ここはテキスト</p>
    <p>ここはテキスト555555</p>
    <p>ここはテキスト555555</p>
    <p>ここはテキスト555555</p>
    <p>ここはテキスト555555</p>
    <p>ここはテキスト555555</p>

    <p>ここはテキスト555555</p>

    <p>ここが最後の行ですから、ちゃんと見えているのかな？</p>
  </section>
</template>

<script>
export default {
  data() {
    return {
      imgPath: "../assets/01.png",
    };
  },
};
</script>

<style scoped>
section {
  margin-left: 4%;
  margin-right: auto;
  padding-top: 5.5rem;
}
p {
  font-size: 16px;
  color: rgb(19, 2, 2);
}

img {
  width: 60%;
  border-radius: 2px;
}
a {
  text-decoration: none;
}
a:hover {
  background-color: pink;
  border-radius: 4px;
}
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
  background-color:black;
  color:wheat;
  margin-left: 8px;
  padding-left: 8px;
  border-radius: 4px;
}
</style>
