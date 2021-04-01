<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name:"Scroll",
  data(){
    return {
      scroll:null
    }
  },
  mounted(){
    this.scroll=new BScroll(this.$refs.wrapper, {
      // click: true,
      observeDOM: true,
      probeType: 3
    })
    // this.scroll.scrollTo(0,0)
    this.scroll.on('scroll',(position) => {
      console.log(position);
    })
  },
  methods: {
    // scrollTo(x, y, time=300){

    // }
  }
}
</script>

<style>

</style>