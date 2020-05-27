<template>
  <div id="app">
    Привет
    https://unpkg.com/axios/dist/axios.mi..
    <br>
    {{i}}
    <br>
    {{HT}}
    <br>
    <button @click="loadHT">Загрузим хэштеги</button>

  </div>
</template>

<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>

<script>

export default {
  name: 'App',
  data() {
    return {
      i:5,
      HT:[],
      url: {
        HT:'https://dka-develop.ru/api?type=hashtag',
        Citys:'https://dka-develop.ru/api?type=city'
      }
    }
  },
  methods: {
      loadHT() {
        this.i++;
        console.log(this.url.HT);
        axios.get(this.url.HT).then( (response)=> {
          this.HT=response.data;
        });
        this.i++;
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
