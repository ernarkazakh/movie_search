
<template>
<div>
  
    <!-- <el-input
  placeholder="Введите название фильма"
  v-model.lazy="input"
  v-debounce="200"
  clearable @change="fetch_data();">
</el-input> -->

<el-autocomplete
  v-model="input"
  :fetch-suggestions="fetch_data"
></el-autocomplete>
<el-row  v-if="results.length > 0">
  <el-col :span="24" v-for="(result, index) in results[0]" :key="result.id">
        {{result.title}}
        Ранк из 10 : {{result.vote_average}} из {{result.vote_count}} проголосовавших  
  </el-col>
</el-row>
</div>

</template>

<script>
import debounce from '../index.js'
import axios from 'axios';

var api_key = "207c757c9a4417cbfd27b7de3ffb7080"

export default {
  data() {
    return {
      initialImageUrl: 'hhttps://image.tmdb.org/t/p/w500/kqjL17yufvn9OVLyXYpvtyrFfak.jpg',
      input: null,
      results: []
    }
  },
    directives: {debounce},
  methods:{
       fetch_data: function(){
           this.results = []
           let that = this
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
        fetch_image: function(){
            for (var i = 0; i < this.results[0].length> 1;i++){

            }
            
        },
       

            // display_data: function(keyword){


            // }
      
  },
  
}
</script>

<style>
 .el-col {
    border-radius: 4px;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .el-row {
    margin-bottom: 20px;
    &:last-child {
      margin-bottom: 0;
    }
  }

</style>
