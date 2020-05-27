<template>
  <div id="app">
    Привет
    https://unpkg.com/axios/dist/axios.mi..
    <br>
    {{i}}
    <br>
    {{HT}}
    <br>
    <button @click="loadHT">Загрузим loadHT</button>
    <br>
    <button @click="MyFetch">Загрузим MyFetch</button>
    <br>
    <button @click="MyXHR">Загрузим MyXHR</button>

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
        Citys:'https://dka-develop.ru/api?type=city',
        DronRef:'https://api.dron.digital/apee/referrals-f88a20cc-757e-11ea-8c9a-00155d020612',
        DronCitys:'http://cms.rc.dron.digital/api/v1/cities?country_id=1',
        BB:'https://bookingboard.ru/plan/?order_id=6D037E09-C536-483A-9979-A0145410F688&city_id=1'
      }
    }
  },
  methods: {
      loadHT() {
        this.i++;
        axios.get(this.url.DronRef).then( (response)=> {
          this.HT=response.data;
        });
        this.i++;
      },
      myPost() {
        {
          axios.post(this.url.BB, {
              "action": "books_get",
              "params": {
                "tableName": "CorpRD",
                "searchText": "ива"
              },
              "token": "7E7E8B19-9CD6-4DB4-B510-0DFE48DB327B",
              "version": 1
          }).then ((response)=> {
            this.HT=response.data;
          })
}
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
