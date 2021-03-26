<template>
  <div id="app">
    {{ mainText }}
  </div>
</template>

<script>

export default {
  name:       'App',
  components: {},
  data() {
    return {
      mainText: '',
    };
  },
  methods: {
    async loadFastifyData() {
      let result = await this.axios.get('http://127.0.0.1:3050/hello');
      this.mainText = result.data.hello;
    },
  },
  mounted() {
    this.loadFastifyData()
  }
};
</script>

<style>
#app {
  font-family:             Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing:  antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align:              center;
  color:                   #2c3e50;
  margin-top:              60px;
}
</style>
