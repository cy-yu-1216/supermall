<template>
<div id="home">
  <nav-bar class="home-nav"><div slot="center">cy购物街</div></nav-bar>
  <scroll class="content">
    <home-swiper :banners="banners"></home-swiper>
    <recommend-comp :recommend="recommend"></recommend-comp>
    <feature/>
    <tab-scoll :title="title" v-on:getCurIndex="getCurIndex"></tab-scoll>
    <goods-list :goods="showType"/>
  </scroll>
  <back-top/>
</div>
</template>

<script>
import HomeSwiper from './childComponents/HomeSwiper'
import RecommendComp from './childComponents/RecommendComp'
import Feature from './childComponents/Feature.vue'

import NavBar from 'components/common/navbar/NavBar'
import Scroll from 'components/common/scroll/Scroll'

import TabScoll from 'components/content/tabScoll/TabScoll.vue'
import GoodsList from 'components/content/goods/GoodsList.vue'
import BackTop from 'components/content/backTop/BackTop'



import {getHomeMultidata,getProductData} from 'network/home'

export default {
  name:"Home",
  components: {
    NavBar,
    HomeSwiper,
    RecommendComp,
    Feature,
    TabScoll,
    GoodsList,
    Scroll,
    BackTop
    
  },
  data(){
    return {
      banners: [],
      recommend: [],
      title: ['流行','新款','精选'],
      goods: {
        'pop':{page: 0,list: []},
        'new': {page: 0, list: []},
        'sell': {page: 0, list: []},
      },
      type:'pop'
    }
  },
  created() {
    this.getHomeMultidata();
    this.getProductData('pop');
    this.getProductData('new');
    this.getProductData('sell');

  },
  computed: {
    showType(){
      return this.goods[this.type].list
    }
  },
  methods: {
    // 网络请求的方法  请求数据
    //请求轮播的数据
    getHomeMultidata(){
      getHomeMultidata().then(res =>{
        this.banners = res.data.banner.list;
        this.recommend = res.data.recommend.list;
      })
    },
    //请求列表的数据
    getProductData(type){
        const page1=this.goods[type].page+1;
      getProductData(type, page1).then(res => {
        //把数组内容依次放到另外一个数组
        this.goods[type].list.push(...res.data.list);
        this.goods[type].page=page1;
        // console.log(res);
      })
    },

    
    // 时间监听方法

    getCurIndex(data){
      // Object.keys(this.goods) 获取["pop",'new',sell]
      this.type=Object.keys(this.goods)[data];
    }
  }

}
</script>

<style scoped>
#home{
  padding-top: 44px;
  /* vh就是当前屏幕可见高度的1%，也就是说

height:100vh == height:100%;

但是当元素没有内容时候，设置height:100%，该元素不会被撑开，此时高度为0，

但是设置height:100vh，该元素会被撑开屏幕高度一致。 */
  height: 100vh;
  position: relative;
}
.home-nav{
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  background-color: var(--color-tint);
  color: aliceblue;
  z-index: 111;
}
.content{
  overflow: hidden;
  position: absolute;
  top: 44px;
  bottom: 49px;
  left: 0;
  right: 0;
}
</style>