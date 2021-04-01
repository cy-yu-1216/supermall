<template>
<div class="wrapper" ref="aa">
  <div class="content">
<ul>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
      <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
      <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
      <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
      <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
    <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
    <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
   <li>1</li>
 </ul>
  </div>
</div>
 
</template>

<script>
  import BScroll from 'better-scroll'

  export default {
    name:"Category",
    data() {
      return {
        scroll: null
      }
    },
    mounted(){
    //  this.scroll = new BScroll(document.querySelector('.wrapper'),{

    //   })
      this.scroll = new BScroll(this.$refs.aa,{
         probeType: 2,
         pullUpLoad: true
      })
      this.scroll.on('scroll',(position) => {
        // console.log(position);
       })
      this.scroll.on('pullingUp',() => {
        console.log("上拉加载更多");
       })
    },
    method: {

  },
  created() {
      // this.scroll = new BScroll(this.$ref.aa,{

      // })
    }
  }
</script>

<style>
.wrapper
{
  height: 150px;
  background-color: aqua;

  overflow: hidden;
  /* overflow-y: scroll; */
}</style>