<template>
  <!-- 竖直方向的导航 -->
  <div class="v-nav">
    <ul>
      <li v-for="(item,index) in items" :class="[item.className,{active: isShow(item.index)}]" class="item" @click="go(index)">
      </li>
    </ul>
  </div>
</template>
<script>
  export default {
    props: {
      index: {
        type: Number
      }
    },
    data() {
      return {
        items: [
          {
            className: 'icon-home',
            index: 1
          },
          {
            className: 'icon-user',
            index: 2
          },
          {
            className: 'icon-stack',
            index: 3
          },
          {
            className: 'icon-file-text',
            index: 4
          },
          {
            className: 'icon-price-tags',
            index: 5
          },
          {
            className: 'icon-dribbble',
            index: 6
          }
        ],
        pages: ['#page1', '#page2', '#page3', '#page4', '#page5', '#page6']
      };
    },
    methods: {
      // 判断小圆点是否隐藏
      isShow(itemIndex) {
        if (this.index === itemIndex) {
          return true;
        } else {
          return false;
        }
      },
      go(index) {
        location.replace(this.pages[index]);
        // 传回index给父组件判断是点击了第几个
        this.$emit('getIndex', index);
      }
    }
  };
</script>
<style lang="less">
  .v-nav{
    position: fixed;
    top: 32%;
    right: 5px;
    .item{
      width: 12px;
      height: 12px;
      text-align: center;
      line-height: 32px;
      border-radius: 50%;
      margin-top: 10px;
      position: relative;
      left: 10px;
      color: #fff;
      background: rgba(0,0,0,0.4);
      cursor: pointer;
      font-size: 0;
      &.active{
        width: 32px;
        height: 32px;
        font-size: 16px;
        left: 0;
      }
      &:hover{
        animation: navFade 1s;
        animation-fill-mode: forwards;
        @keyframes navFade {
          0% {}
          100% {width: 32px;height: 32px;font-size: 16px;left: 0;}
        }
      }
    }
  }
</style>