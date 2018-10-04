
<template>
<div>
<h2>Добро пожаловать в Movie Database API. Чтобы найти фильм прошу ввести слово</h2>
<el-autocomplete
  v-model="input"
  :fetch-suggestions="fetch_data"
  :trigger-on-focus=true
  :debounce="300"
></el-autocomplete>
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
                return that.results
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


</style>
