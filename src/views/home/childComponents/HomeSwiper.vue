<template>
  <Swiper>
    <swiper-item v-for="(item,key) in banners" :key="key">
      <a :href="item.link">
        <img :src="item.image" alt="">
      </a>
    </swiper-item>
  </Swiper>
</template>

<script>
import {Swiper , SwiperItem} from 'components/common/swiper'
export default {
  name: "HomeSwiper",
  components: {
    Swiper,
    SwiperItem  
  },
  props: {
    banners: {
      type:Array,
      default() {
        return []
      }
    }
  }
}
</script>

<style>

</style>