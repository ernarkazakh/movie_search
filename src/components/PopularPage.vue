<template>
<el-row  v-if="results.length > 0">
  <el-col :span="8" v-for="(result, index) in results[0]" :key="index">
    <div class="grid-content bg-purple">
        
        {{result.title}}
        <br>
        <br>
        {{result.poster_path}}
        <!-- {{result.overview}} -->
        {{url}}
        <img v-bind:src="url + result.poster_path    ">
    </div>
  </el-col>
</el-row>

</template>

<script>

import axios from 'axios';

var api_key = "207c757c9a4417cbfd27b7de3ffb7080"


export default {
    data() {
    return {
      url: 'https://image.tmdb.org/t/p/w300',
      results: []
    }
  },
    created: function (){
            let that = this
            axios.get('https://api.themoviedb.org/3/movie/popular',{
              params: {
                  api_key: api_key,
                  language: 'ru-Ru',
              }
          })
            .then(function(response){
               that.results.push(response.data.results)
            })
            .catch(function(error){
                console.log(error)
            })
        },
    
    
}
</script>
