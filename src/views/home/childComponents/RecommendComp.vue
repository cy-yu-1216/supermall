<template>
  <div class="recommend">
    <div v-for="item,key in recommend" :key="key" class="context"> 
      <a :href="item.link">
        <img :src="item.image" alt="">
        <div>{{item.title}}</div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "RecommendComp",
  props: {
    recommend: {
      type: Array,
      default() {
        return []
      }
    }
  }
}
</script>

<style>
.recommend{
  display: flex;
  font-size: 10px;
  text-align: center;
  width: 100%;
  padding: 10px 0px 20px 0px;
  border-bottom: 5px solid #eee;
}
.context{
  flex: 1;
}
.context img{
  width: 70px;
  height: 70px;
  margin-bottom: 5px;
}

</style>