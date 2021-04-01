<template>
  <div class="back-top" @click="backClick">
    <img src="~assets/img/common/top.png" alt="">
  </div>
</template>

<script>
export default {
  name: "BackTop",
  methods: {
    backClick() {
      console.log(111);
    }
  }
}
</script>

<style scoped>
.back-top{
  position: fixed;
  right: 10px;
  bottom:50px;
}
.back-top img{
  height: 55px;
  width: 55px;
}

</style>