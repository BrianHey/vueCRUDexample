<template>
  <div class="hello">
    <input type="checkbox" v-model="mostrar" /> <br />
    <img v-if="mostrar" width="400" :src="imgSrcFront" alt="" />
    <img v-else width="400" :src="imgSrcBack" alt="" />
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HelloWorld",
  props:["msg"],
  data() {
    return {
      mostrar: true,
      imgSrcFront: "",
      imgSrcBack: "",
    };
  },
  async mounted() {
    try {
      const { data } = await axios.get("https://pokeapi.co/api/v2/pokemon/25");
      const { sprites } = data;
      const { front_default, back_default } = sprites;
      this.imgSrcFront = front_default;
      this.imgSrcBack = back_default;
    } catch (e) {
      console.log(e);
    }
  },
};
</script>

<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
