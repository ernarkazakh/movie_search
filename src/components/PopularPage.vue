<template>
<el-row  v-if="results.length > 0">
  <el-col :span="8" v-for="(result, index) in results[0]" :key="index">
    <div class="grid-content bg-purple" v-on="">
        {{result.title}}
        <br>
        <br>
        <!-- {{result.overview}} -->
        <img v-bind:src="url + result.poster_path">
        <el-collapse>
          <el-collapse-item  title="Узнать больше"   >
            <div>{{result.overview}}</div>
            <br>
            <el-rate
  v-model="result.vote_average"
  disabled
  show-score
  :max="10"
  text-color="#ff9900">
</el-rate>
<div>Список из зарекомендовынных фильмов</div>
            <div>Из {{result.vote_count}} проголосовавших</div>
            <!-- <div>{{movie_recommendations}}
          </div> -->
          </el-collapse-item>
        </el-collapse>

          <br>
        <br>


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
      results: [],
      movie_recommendations: []
    }
  },
     methods:{
      get_recommended: function(){
        let id = 351286
        var that = this
        axios.get('https://api.themoviedb.org/3/movie/' + id + '/recommendations', {
          params: {
            api_key: api_key,
            language: 'ru-Ru'
          }
        })
        .then(function(response){
          console.log(response)
that.movie_recommendations.push(response.data.results)
        })
        .catch(function(error){
          console.log(error)
        })

      },
      generate_popular: function (){
            let that = this
            axios.get('https://api.themoviedb.org/3/movie/popular',{
              params: {
                  api_key: api_key,
                  language: 'ru-Ru',
              }
          })
            .then(function(response){
               that.results.push(response.data.results)
               for (let i = 0; i < response.data.results[0].length;i++){
                 alert('works' + i)

                 console.log(i)

               }
            })
            .catch(function(error){
                console.log(error)
            })
        }
    },
    beforeMount(){
      this.generate_popular()
      this.get_recommended()
    }
    // created: function (){
    //         let that = this
    //         axios.get('https://api.themoviedb.org/3/movie/popular',{
    //           params: {
    //               api_key: api_key,
    //               language: 'ru-Ru',
    //           }
    //       })
    //         .then(function(response){
    //            that.results.push(response.data.results)
    //         })
    //         .catch(function(error){
    //             console.log(error)
    //         })
    //     }

}
</script>
