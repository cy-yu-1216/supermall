<template>
  <div class="title">
    <div v-for="item,index in title" :key="index" class="item" @click="cColor(index)" :class="{'active':index==curIndex}">
      <span>{{item}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabScoll",
  data(){
    return {
      curIndex: 0
    }
  },
  props: {
    title: {
      type: Array,
      default(){
        return []
      }
    }
  },
  methods: {
    cColor(index){
      this.curIndex = index;
      this.$emit('getCurIndex',this.curIndex)
    },
    
  }
}
</script>

<style>
.title{
  display: flex;
  /* display: sticky; */
  background-color: #ffff;
  text-align: center;
  padding: 5px;
}
.item{
  flex:1;
}
.active{
  color: var(--color-high-text);
}
.active span{
  padding: 5px;
   border-bottom: 3px solid var(--color-high-text);
 
}
</style>