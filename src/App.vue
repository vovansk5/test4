<template>
  <div id="app">
    {{i}}
    <br>
    {{webResponse}}
    <br>
    <button @click="loadDronRef">Загрузим loadDronRef</button>
    <br>
    <br>
    <button @click="myPost">Post запрос BB Free </button>
    <br>
    <br>
    <button @click="postTypicode">Post запрос на postTypicode</button>

    <br>
    <br>
    <button @click="postBB">Post запрос на postBB</button>



    <br>
    <br>
    <button @click="myGet">Get запрос на RC.BB</button>
    <br>

    <br>
    <br>
    <button @click="getHTTPDron">Get запрос на getHTTPDron</button>
    <br>



</div>

</template>


<script>
import {HTTP} from './components/http-common';
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      i:5,
      webResponse:[],
      url: {
        HT:'https://dka-develop.ru/api?type=hashtag',
        Citys:'https://dka-develop.ru/api?type=city',

        DronRef:'https://api.dron.digital/apee/referrals-f88a20cc-757e-11ea-8c9a-00155d020612',
        BB:'https://rc.bb.direct/plan/?order_id=952FF47B-9A99-43B4-951A-B38697124EB4&city_id=1'
      },
      postBodyFree:'',
      postBodyBB: `{
              "action": "books_get",
              "params": {
                "tableName": "CorpRD",
                "searchText": "ива"
              },
              "token": "68141BA7-1941-4E59-9B10-7EB08E2539F",
              "version": 1
              }`
    }
  },
  methods: {
      loadDronRef() {
        this.i++;
        axios.get(this.url.DronRef).then( (response)=> {
          this.webResponse=response.data;
        });
        this.i++;
      },
      myGet() {
        this.i++;
        axios.get(this.url.BB).then( (response)=> {
          this.webResponse=response.data;
        });
        this.i++;
      },      
      myPost() {
          this.webResponse='';
          axios.post(`http://rc.bb.direct/plan`, this.postBodyFree
          ).then ((response)=> {
            this.webResponse=response.data;
          })
      },
      postTypicode() {
          HTTP.get(`posts`) 
          .then (response=> {
            this.webResponse=response.data;
          })
      },

      getHTTPDron() {
          HTTP.post(``,this.postBodyBB) 
          .then ((response)=> {
            this.webResponse=response.data;
          })
      },

      postBB() {
          this.webResponse='';
          axios.post(this.url.BB, this.postBodyBB
          ).then ((response)=> {
            this.webResponse=response.data;
          })
      }      
  }
}
</script>

<style>

</style>
