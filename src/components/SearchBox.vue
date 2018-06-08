<template>
    <div>
    <el-input
  placeholder="Please input"
  v-model.lazy="input"
  clearable @change="fetch">
</el-input>

<ul v-if="results.length > 0">
            <li v-for="(result, index) in results[0]" :key="index">{{result.overview}}</li>
            <li>Test rabotaet</li>
        </ul>
</div>
</template>

<script>
import axios from 'axios';

var api_key = "207c757c9a4417cbfd27b7de3ffb7080"

export default {
  data() {
    return {
      input: null,
      results: []
    }
  },
  methods:{
       fetch: function(){
           this.results = []
           var that = this
          axios.get('https://api.themoviedb.org/3/search/movie?',{
              params: {
                  api_key: api_key,
                  language: 'ru-Ru',
                  query: this.input
              }
          })
            .then(function(response){
                that.results.push(response.data.results)
                // console.log(results)
            })
            .catch(function(error){
                console.log(error)
            })
            },
            display_data: function(keyword){


            }
      
  },
  
}
</script>