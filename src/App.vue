
<template>
  <el-container>
    <el-header>
      <!-- <SearchBox/> -->
    </el-header>
    <el-main>
      <PopularPage/>
    </el-main>
    <el-footer>
    </el-footer>


  </el-container>

</template>








<script>

import SearchBox from './components/Searchbox.vue'
import PopularPage from './components/PopularPage.vue'

export default {
  name: 'App',
  components: {
    SearchBox,
    PopularPage
  }
}
</script>

<style>
html, body {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  margin-top: 16px;
  margin-bottom: 16px;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
