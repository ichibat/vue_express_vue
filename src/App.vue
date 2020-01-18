<template>
<div class="hello">
    <form action>
      <input type="text" placeholder="text" v-model="text">
      <input type="submit" value="decide" @click="submitClick">
    </form>
  </div>
</template>

<script>
import Axios from "axios";
export default {
  name: "HelloWorld",
  data() {
    return {
      text: null
    };
  },
  methods: {
    submitClick() {
      const body = {
        text: this.text
      };
      Axios.get(`http://localhost:3000/hoge/${this.text}`)
        .then(res => {
          console.log(res.data.name)
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
