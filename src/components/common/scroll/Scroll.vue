<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll, { PullUpLoad } from 'better-scroll'
export default {
  name:"Scroll",
  props: {
    probeType:{
      type: Number,
      dafault: 0
    },
    pullUpLoad: {
      type: Boolean,
      default: false
    }
  },
  data(){
    return {
      scroll: null
    }
  },
  mounted(){
    this.scroll=new BScroll(this.$refs.wrapper, {
      // click: true,
      //防止不会动
      observeDOM: true,
      click: true,
      // 监听滚动的位置时候要设置probeType： 0 1 2 3
      probeType: this.probeType,
      //上拉加载更多
      pullUpLoad: this.pullUpLoad
    })
    // this.scroll.scrollTo(0,0)
    //监听滚动的位置
    this.scroll.on('scroll',(position) => {
      // console.log(position);
      this.$emit("scroll",position)
    }),
    this.scroll.on('pullingUp', () => {
      this.$emit("pullingUp")
    })
  },
  methods: {
    // time300是一个默认值 返回最顶部
    scrollTo(x, y, time=300){
      //防止Home过来调用这个方法 scroll为空则会报错
      this.scroll && this.scroll,this.scrollTo && this.scroll.scrollTo(x,y,time)
    },
    // 上拉加载更多
    finishPullUp(){
      this.scroll.finishPullUp()
    },
    //返回scroll的刷新方法,重新计算图片的高度 防止滑动不下去的bug
    itemImageLoad(){
      this.scroll && this.scroll.refresh()
    }

  }
}
</script>

<style>

</style>