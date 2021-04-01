<template>
  <div class="list">
    <goods-list-item v-for="item,index in goods" :key="index" :goods-item="item"/>
  </div>
</template>

<script>
import GoodsListItem from './GoodsListItem.vue'
export default {
  components: { GoodsListItem },
  name: "GoodsList",
  props: {
    goods:{
      type: Array,
      default(){
        return []
      }
    }
  }
}
</script>

<style>
.list{
   display: flex;
   /* 根据宽度决定一行中塞多少个 默认是flex-wrap： nowrap 所以要设置图片宽读 */
   flex-wrap: wrap;
    padding: 5px;
    /* 均等分 中间空隙距离相等  最两边空袭加起来等于中间空隙*/
    justify-content: space-around;
}

</style>