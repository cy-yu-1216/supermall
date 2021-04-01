<template>
  <div class="tab-bar-item">
    <div v-if="isActive" @click="itemClick">
      <slot name="item-ico"></slot>
    </div>
    <div v-else>
      <slot name="item-active-ico"></slot>
    </div>
    <div :style="isText">
      <slot name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name:'TabBarItem',
  props: {
      path: String,
      activeColor:{
        type:String,
        default:'red'
      }
  },
  computed: {
    isActive(){
      // console.log("1"+this.path);
      return this.$route.path.indexOf(this.path)==-1
    },
    isText(){
      // return this.isActive ? {color: this.activeColor} : {} 
        return this.isActive ? {} : {color: this.activeColor}

    }
  },
  methods: {
    itemClick() {
      // console.log("2"+this.path);
      // console.log("1"+this.path);
      this.$router.replace(this.path);
      // console.log("3"+this.path);
    }
  }
}
</script>

<style>
.tab-bar-item{
  flex:1;
  text-align: center;
  font-size: 14px;
  height: 49px;

}
.tab-bar-item img{
  width: 24px;
  height: 24px;
  vertical-align: middle;
  margin-top: 2px;
}

</style>