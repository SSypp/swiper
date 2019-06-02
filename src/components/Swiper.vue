<template>
  <div>
    <!-- swiper top -->
      <swiper :options="swiperOptionTop" class="gallery-top" ref="swiperTop">
        <swiper-slide class="slide-1" v-for="itemImg of swiperImg" :key="itemImg.id">
          <img :src="itemImg.largeImg" :alt="itemImg.title">
        </swiper-slide>
      </swiper>
      <!-- swiper Thumbs -->
      <swiper :options="swiperOptionThumbs" class="gallery-thumbs" ref="swiperThumbs">
        <swiper-slide class="slide-1" style='{width:226px;height:154px;}' v-for="itemImg of swiperImg" :key="itemImg.id">
          <div class="imgItem">
            <img :src="itemImg.largeImg" :alt="itemImg.title">
          </div>
        </swiper-slide>
      </swiper>
  </div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import {swiper, swiperSlide} from 'vue-awesome-swiper'
export default {
  name: 'Swiper',
  props:['swiperImg'],
  components:{
    swiper,
    swiperSlide
  },
  data () {
    return {
      swiperOptionTop: {
        spaceBetween: 10,
        effect: 'fade',
        loop: true,
        loopedSlides: 5
      },
      swiperOptionThumbs: {
        spaceBetween: 18,
        loop: true,
        slidesPerView: 5,
        slideToClickedSlide: true,
        watchSlidesVisibility: true
      },
    }
  },
  mounted() {
   this.$nextTick(() => {
     const swiperTop = this.$refs.swiperTop.swiper
     const swiperThumbs = this.$refs.swiperThumbs.swiper
     swiperTop.controller.control = swiperThumbs
     swiperThumbs.controller.control = swiperTop
   })
 }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.swiper-container{
   background-color:#fff;
 }
 .gallery-top {
   height: 660px!important;
   width: 1200px;
   margin:0 auto;
 }
 .gallery-top .swiper-slide img{
   width:100%;
   height:100%;
 }
 .gallery-thumbs {
   height: 154px!important;
   box-sizing: border-box;
   width: 1200px;
   margin-top: 40px;
   margin-bottom: 32px;
 }
 .gallery-thumbs .swiper-slide {
   width: 226px;
   height: 154px;
   cursor: pointer;
   opacity:0.6;
 }
 .gallery-thumbs .swiper-slide img{
   width:226px;
   height:154px;
 }
 .gallery-thumbs .swiper-slide-active{
   opacity: 1;
 }
</style>
