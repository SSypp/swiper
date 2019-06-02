<template>
  <div id="app">

    <Swiper :swiperImg='childImg'/>
  </div>
</template>

<script>
import Swiper from './components/Swiper'

export default {
  name: 'App',
  components: {
    Swiper
  },
  data () {
    return {
      childImg: []
    }
  },
  mounted () {
    this.$axios.get('/api/images.json')
    .then(
      res => {
        //console.log(res.data.swiperImg)
        this.childImg = res.data.swiperImg
        //console.log(this.childImg)
    })
    .catch(
      err => {
        console.log(err)
      }
    )
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
