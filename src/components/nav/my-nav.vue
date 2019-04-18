<template>
  <!-- 导航组件 -->
  <div class="my-nav">
    <div class="nav-left">cR</div>
    <div class="nav-right"></div>
  </div>
</template>
<script>
  export default {

  };
</script>
<style lang="less">
  .my-nav{
    width: 100%;
    height: 60px;
    line-height: 60px;
    color: #fff;
    font-size: 24px;
    background: rgba(7,17,27,0.5);
    cursor: default;
    .nav-left{
      float: left;
      margin-left: 30px;
    }
    .nav-right{
      float: right;
    }
  }
</style>