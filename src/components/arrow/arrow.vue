<template>
  <!-- 向下箭头 -->
  <i class="icon-arrow_lift"></i>
</template>
<script>
  export default {

  };
</script>
<style lang="less">
  .icon-arrow_lift{
    position: absolute;
    bottom: 20px;
    left: 50%;
    margin-left: -20px;
    color: rgba(255,255,255,0.8);
    font-size: 24px;
    transform: rotate(-90deg);
    animation: roll 1.5s infinite;
    @media screen and (max-width: 500px) {
      margin-left: -12px;
    }
    @keyframes roll {
      0% { bottom: 20px; opacity: 1;}
      100% { bottom: 10px; opacity: 0;}
    }
  }
</style>