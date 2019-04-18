<template>
  <div class="page">
    <div class="content">
      <div class="section section1">
        <myNav></myNav>
        <div class="img-wrapper">
          <img src="./me.jpg" width="150" height="150">
        </div>
        <div class="text">
          <span>蔡位荣</span>
        </div>
        <div class="my-text-wrapper">
          <ul>
            <li v-for="item in items" class="item">
              {{item.text}}
            </li>
          </ul>
        </div>
        <arrow></arrow>
      </div>
      <div class="section section2">
        <div class="about-wrapper">
          <h1 class="title">关于我</h1>
          <ul>
            <li class="about-item" v-for="item in aboutItems">
              <i class="item-img" :class="item.name"></i>
              <span class="text">{{item.text}}</span>
            </li>
          </ul>
          <p class="about-text">
            一年互联网工作经验<br>
            自我评价：热爱前端，代码洁癖，完美主义者<br>
            积极向上、高度责任感、学习能力强<br>
            敢于接受挑战，愿意拼搏，具备较强的抗压能力。<br>
            有独立分析和解决问题的能力，以及良好的团队意识和协作精神
          </p>
        </div>
        <arrow></arrow>
      </div>
      <div class="section section3">
        <h1 class="title">技能栈</h1>
        <div class="skill-wrapper">
          <div class="left">
            <div class="out-circle">
              <div class="out-block" v-for="item in skillItems">{{item.text}}</div>
            </div>
            <div class="inner-circle">
              <div class="inner-block">vue</div>
              <div class="inner-block">es6</div>
            </div>
          </div>
<!--           <div class="right">
            <p class="text">
              熟练使用html5，ccs3，JQuery，Bootstrap，vue.js等技术<br>
              并且有java，Android基础<br>
              擅长组件开发，懂得MVVM模式<br>
            </p>
          </div> -->
        </div>
        <arrow></arrow>
      </div>
      <div class="section section4">
        <h1 class="title">经历</h1>
        <transition name="fade">
          <div class="slide-wrapper">
            <div class="left">
              <i class="logo" :class="companyInfos[companyIndex].logoClass"></i>
            </div>
            <div class="right">
              <h1 class="company">{{companyInfos[companyIndex].name}}</h1>
              <p class="time">{{companyInfos[companyIndex].time}}</p>
              <p class="job">{{companyInfos[companyIndex].job}}</p>
              <p class="job-content">
                {{companyInfos[companyIndex].jobContent}}
                <a href="http://www.sdj88.com/" class="address" target="_blank">{{companyInfos[companyIndex].address}}
                </a>
              </p>
              <p class="details" v-for="item in companyInfos[companyIndex].details">{{item.text}}</p>
            </div>
          </div>
        </transition>
        <div class="dots-wrapper">
          <span v-for="(dot,index) in dotsItems" class="dot" :class="{active: index===companyIndex}" @click="dotChange(index)"></span>
        </div>
        <arrow></arrow>
      </div>
      <div class="section section5">
        <h1 class="title">作品集</h1>
        <div class="works-wrapper">
          <div class="works" v-for="(item,index) in worksItems" v-show="showWorks(index)">
            <div class="name">{{item.title}}</div>
            <p class="text">{{item.text}}</p>
            <a class="link icon-link" :href="item.link" target="_blank"></a>
          </div>
        </div>
        <div class="github"><a href="https://github.com/mikeros147" target="_blank">github上查询更多</a></div>
        <div class="button-wrapper">
          <div class="pre icon-circle-left" @click="clickPrev"></div>
          <div class="next icon-circle-right" @click="clickNext"></div>
        </div>
        <arrow></arrow>
      </div>
      <div class="section section6">
        <h1 class="title">联系我</h1>
        <div class="text-wrapper">
          <ul>
            <li v-for="item in contactItems" class="contact-item" :class="item.color">{{item.text}}</li>
          </ul>
          <p class="text">
            不止一种语言的开发能力<br>
            注重效率，偏爱敏捷开发<br>
            喜欢尝试，期待新鲜事物<br>
            前端即兴趣，兴趣即未来<br>
            富有激情，用实力成就梦想<br>
            带上我吧，一起看到更大的世界
          </p>
          <ul>
            <a v-for="item in iconItems" :class="item.name" class="icon" :href="item.link" target="_blank">

            </a>
          </ul>
        </div>
        <div class="bottom">
          <p class="text">Made by 蔡位荣</p>
        </div>
      </div>
    </div>
    <v-nav :index="sectionIndex" @getIndex="getIndex"></v-nav>


  </div>
</template>

<script>
  import $ from 'jquery';
  import myNav from '../nav/my-nav';
  import arrow from '../arrow/arrow';
  import vNav from '../nav/v-nav';

  export default {
    name: 'page',
    data () {
      return {
        items: [
          {
            text: '深圳大学毕业'
          },
          {
            text: '前端开发工程师'
          },
          {
            text: '邮箱: 283670650@qq.com'
          },
          {
            text: '联系电话: 15811840818'
          }
        ],
        aboutItems: [
          {
            text: '年龄/23岁',
            name: 'icon-file-text'
          },
          {
            text: '学历/本科',
            name: 'icon-profile'
          },
          {
            text: '住址/深圳',
            name: 'icon-location2'
          },
          {
            text: '状态/在职',
            name: 'icon-star-empty'
          }
        ],
        skillItems: [
          {
            text: 'ccs3'
          },
          {
            text: 'git'
          },
          {
            text: 'html5'
          },
          {
            text: 'less'
          },
          {
            text: 'Bootstrap'
          },
          {
            text: 'JQuery'
          },
          {
            text: 'webpack'
          },
          {
            text: 'javaScript'
          }
        ],
        companyInfos: [
          {
            name: '学习内容',
            time: '2016年1月-至今',
            job: '学习前端',
            jobContent: 'html5，CSS3，JavaScript，vue.js，Bootstrap，JQuery，微信小程序等',
            logoClass: 'icon-onedrive',
            details: [
              {
                text: '1. 熟悉使用html5，css3，javaScript编写页面，对JavaScript有了进一步的了解'
              },
              {
                text: '2. 学习JQuery和Bootstrap，从而可以快速开发页面'
              },
              {
                text: '3. 学习vue.js，了解MVVM，能够独立完成模块化、组件式开发'
              },
              {
                text: '4. 实战应用所学知识'
              }
            ]
          }
        ],
        dotsItems: [
          {
            index: 0
          },
          {
            index: 1
          }
        ],
        worksItems: [
          {
            title: '项目名称：Vue.js 高仿饿了么外卖APP',
            text: '项目实现：使用Vue.js 2.0版本前端框架，仿照饿了么外卖APP搭建网页。使用git工具，用vue-cli脚手架搭建项目，用html5搭建基础，用less改变样式，使用mvvm模式和组件化方式开发页面。(移动端页面)',
            link: 'http://vuejssellapp.t.imooc.io/#!/'
          },
          {
            title: '项目名称：Bootstrap案例',
            text: '项目实现：使用了Bootstrap开发网站，Bootstrap包含了许多丰富的组件，可以使开发更快速。我使用了栅格布局和一些提供的组件来实现这个页面。网页是响应式的。',
            link: 'https://mikeros147.github.io/practise/'
          },
          {
            title: '项目名称：JQuery案例',
            text: '项目实现：使用了html5，css3，JQuery开发整个页面',
            link: 'https://mikeros147.github.io/JQuery-practise/'
          }
        ],
        contactItems: [
          {
            text: '热情',
            color: 'one'
          },
          {
            text: '技术',
            color: 'two'
          },
          {
            text: '灵感',
            color: 'three'
          },
          {
            text: '挑战',
            color: 'four'
          }
        ],
        iconItems: [
          {
            name: 'icon-github',
            link: 'https://github.com/mikeros147'
          },
          {
            name: 'icon-sina-weibo',
            link: 'https://www.weibo.com'
          }
        ],
        sectionIndex: 1,
        companyIndex: 0,
        clientWidth: document.body.clientWidth
      };
    },
    mounted() {
      const that = this;

      $('.content').fullpage({
        verticalCentered: false,
        anchors: ['page1', 'page2', 'page3', 'page4', 'page5', 'page6'],
        recordHistory: false,
        afterLoad: function(anchorLink, index) {
          that.sectionIndex = index;
        }
      });
      window.onresize = () => {
        return (() => {
          window.clientWidth = document.body.clientWidth;
          that.clientWidth = window.clientWidth;
        })();
      };
    },
    watch: {
      clientWidth(val) {
        if (!this.timer) {
          this.clientWidth = val;
          this.timer = true;
          let that = this;
          setTimeout(function() {
            that.timer = false;
          }, 400);
        }
      }
    },
    methods: {
      // 小圆点点击变换
      dotChange(index) {
        this.companyIndex = index;
      },
      showWorks(index) {
        if (this.clientWidth <= 500 && index !== 0) {
          return false;
        }
        return true;
      },
      getIndex(index) {
        // console.log(index);
      },
      clickPrev() {
        let prevItem = this.worksItems[this.worksItems.length - 1];
        for (let i = this.worksItems.length - 1; i > 0; i--) {
          this.$set(this.worksItems, i, this.worksItems[i - 1]);
        }
        this.$set(this.worksItems, 0, prevItem);
      },
      clickNext() {
        let nextItem = this.worksItems[0];
        for (let i = 0; i < this.worksItems.length - 1; i++) {
          this.$set(this.worksItems, i, this.worksItems[i + 1]);
        }
        this.$set(this.worksItems, this.worksItems.length - 1, nextItem);
      }
    },
    components: {
      myNav,
      arrow,
      vNav
    }
  };
</script>

<style lang="less">
  .page{
    font-family: Microsoft YaHei, sans-serif;
    .content{
      .section1{
        background: rgb(0,160,220);
        .img-wrapper{
          width: 150px;
          padding-top: 80px;
          margin: 0 auto;
          @media screen and (max-width: 500px) {
            padding-top: 20px;
          }
          img{
            width: 100%;
            border-radius: 50%;
          }
        }
        .text{
          width: 80%;
          height: 24px;
          margin: 30px auto 0 auto;
          padding: 20px 0;
          text-align: center;
          color: #fff;
          font-size: 24px;
          border-bottom: 1px solid rgba(255,255,255,0.5);
          cursor: default;
          span:hover{
            animation: sway 2s;
            animation-fill-mode: forwards;
            @keyframes sway {
              0%{font-size: 24px;}
              100%{font-size: 36px;}
            }
          }
        }
        .my-text-wrapper{
          width: 80%;
          margin: 30px auto 0 auto;
          text-align: center;
          color: #fff;
          font-size: 20px;
          .item{
            margin-top: 60px;
            animation: fade 3s;
            @keyframes fade {
              0% {opacity: 0}
              100% {opacity: 1}
            }
            @media screen and (max-width: 500px) {
              font-size: 16px;
              margin-top: 30px;
            }
          }
        }
      }
      .section2{
        background: #0f8d82;
        color: #fff;
        .about-wrapper{
          margin: 0 auto;
          width: 80%;
          text-align: center;
          .title{
            padding-top: 80px;
            text-align: center;
            font-size: 26px;
            @media screen and (max-width: 500px) {
              padding-top: 20px;
            }
          }
          .about-item{
            display: inline-block;
            margin: 80px 40px 0 40px;
            @media screen and (max-width: 500px) {
              margin: 40px 40px 0 40px;
            }
            .item-img{
              display: block;
              position: relative;
              left: 10px;
              width: 70px;
              height: 70px;
              line-height: 70px;
              background: #27988e;
              border-radius: 50%;
              cursor: pointer;
              border: 1px solid #27988e;
              font-size: 24px;
              &:after{
                content: '';
                position: absolute;
                left: 0;
                box-shadow: 0 0 0 2px rgba(255,255,255,0.1);
                opacity: 0;
                transform: scale(0.9);
                width: 70px;
                height: 70px;
                border-radius: 50%;
                @media screen and (max-width: 430px) {
                  width: 40px;
                  height: 40px;
                }
              }
              &:hover{
                transform: scale(0.9);
              }
              &:hover:after{
                animation: effect 1s ease-out 75ms;
                animation-fill-mode: forwards;
                @keyframes effect {
                  0% {
                    opacity: 0.3;
                  }
                  40% {
                    opacity: 0.5;
                    box-shadow: 0 0 0 2px rgba(255,255,255,0.1), 0 0 10px 10px #109085, 0 0 0 10px rgba(255,255,255,0.5);
                  }
                  100% {
                    box-shadow: 0 0 0 2px rgba(255,255,255,0.1), 0 0 10px 10px #109085, 0 0 0 10px rgba(255,255,255,0.5);
                    transform: scale(1.5);
                    opacity: 0;
                  }
                }
              }
              @media screen and (max-width: 500px) {
                width: 40px;
                height: 40px;
                font-size: 20px;
                line-height: 40px;
                left: 8px;
              }
            }
            .text{
              display: block;
              padding-top: 25px;
              font-size: 20px;
              @media screen and (max-width: 500px) {
                font-size: 12px;
              }
            }
          }
          .about-text{
            margin-top: 50px;
            line-height: 60px;
            font-size: 20px;
            @media screen and (max-width: 500px) {
                font-size: 12px;
                margin-top: 10px;
                line-height: 42px;
            }
          }
        }
      }
      .section3{
        background: #4a5b8b;
        color: #fff;
        .title{
            padding-top: 80px;
            font-size: 24px;
            text-align: center;
            @media screen and (max-width: 500px) {
              padding-top: 20px;
            }
          }
        .skill-wrapper{
          position: relative;
          margin: 100px auto 0 auto;
          width: 60%;
          display: flex;
          flex-wrap: wrap;
          justify-content: space-between;
          @media screen and (max-width: 500px) {
            margin-top: 50px;
          }
          .left{
            transform: scale(1.5);
            margin: 100px auto;
            @media screen and (max-width: 500px) {
              transform: scale(1);
              margin: 50px auto;
            }
            @media screen and (max-width: 375px) {
              margin-left: -4%;
            }
            .out-circle{
              position: relative;
              width: 242px;
              height: 242px;
              border-radius: 50%;
              border: 4px dashed rgb(147,153,159);
              .out-block{
                position: absolute;
                width: 60px;
                height: 60px;
                border-radius: 50%;
                text-align: center;
                line-height: 60px;
                opacity: 0.9;
                color: #fff;
                font-size: 12px;
                @media screen and (max-width: 500px) {
                  width: 40px;
                  height: 40px;
                  line-height: 40px;
                  font-size: 10px;
                }
                &:nth-child(1){
                  animation: outX 8s cubic-bezier(0.36,0,0.64,1) -4s infinite alternate, outY 8s cubic-bezier(0.36,0,0.64,1) 0s infinite alternate;
                  background: #97b9cc;
                }
                &:nth-child(2){
                  animation: outX 8s cubic-bezier(0.36,0,0.64,1) -6s infinite alternate, outY 8s cubic-bezier(0.36,0,0.64,1) -2s infinite alternate;
                  background: #a97b71;
                }
                &:nth-child(3){
                  animation: outX 8s cubic-bezier(0.36,0,0.64,1) -8s infinite alternate, outY 8s cubic-bezier(0.36,0,0.64,1) -4s infinite alternate;
                  background: #4b8f9c;
                }
                &:nth-child(4){
                  animation: outX 8s cubic-bezier(0.36,0,0.64,1) -10s infinite alternate, outY 8s cubic-bezier(0.36,0,0.64,1) -6s infinite alternate;
                  background: #8487b3;
                }
                &:nth-child(5){
                  animation: outX 8s cubic-bezier(0.36,0,0.64,1) -12s infinite alternate, outY 8s cubic-bezier(0.36,0,0.64,1) -8s infinite alternate;
                  background: #cdbf9f;
                }
                &:nth-child(6){
                  animation: outX 8s cubic-bezier(0.36,0,0.64,1) -14s infinite alternate, outY 8s cubic-bezier(0.36,0,0.64,1) -10s infinite alternate;
                  background: #434650;
                }
                &:nth-child(7){
                  animation: outX 8s cubic-bezier(0.36,0,0.64,1) -16s infinite alternate, outY 8s cubic-bezier(0.36,0,0.64,1) -12s infinite alternate;
                  background: #9e958c;
                }
                &:nth-child(8){
                  animation: outX 8s cubic-bezier(0.36,0,0.64,1) -18s infinite alternate, outY 8s cubic-bezier(0.36,0,0.64,1) -14s infinite alternate;
                  background: #475467;
                }
              }
            }
            .inner-circle{
              position: absolute;
              top: 66px;
              left: 72px;
              width: 102px;
              height: 102px;
              border-radius: 50%;
              border: 4px dashed rgb(147,153,159);
              @media screen and (max-width: 500px) {
                left: 84px;
              }
              @media screen and (max-width: 375px) {
                left: 72px;
              }
              .inner-block{
                position: absolute;
                width: 40px;
                height: 40px;
                border-radius: 50%;
                text-align: center;
                line-height: 40px;
                opacity: 0.9;
                font-size: 12px;
                &:nth-child(1){
                  animation: innerX 8s cubic-bezier(0.36,0,0.64,1) -4s infinite alternate, innerY 8s cubic-bezier(0.36,0,0.64,1) 0s infinite alternate;
                  background: #b4a6ab;
                }
                &:nth-child(2){
                  animation: innerX 8s cubic-bezier(0.36,0,0.64,1) -12s infinite alternate, innerY 8s cubic-bezier(0.36,0,0.64,1) -8s infinite alternate;
                  background: #6f626d;
                }
              }
            }
            @keyframes outX {
              0% {  left: -27px;  }
              100% {  left: 217px;  }
            }
            @keyframes outY {
              0% {  top: -27px;  }
              100% {  top: 217px;  }
            }
            @keyframes innerX {
              0% {  left: -22px;  }
              100% {  left: 82px;  }
            }
            @keyframes innerY {
              0% {  top: 82px;  }
              100% {  top: -22px;  }
            }
          }
          .right{
            // @media screen and (max-width: 500px) {
            //   padding-top: 50px;
            // }
            .text{
              font-size: 20px;
              line-height: 60px;
              @media screen and (max-width: 500px) {
                font-size: 12px;
                line-height: 30px;
              }
            }
          }
        }
      }
      .section4{
        background: #8f5949;
        .title{
          padding-top: 120px;
          text-align: center;
          color: #fff;
          font-size: 26px;
          @media screen and (max-width: 500px) {
            padding-top: 40px;
          }
        }
        .slide-wrapper{
          width: 760px;
          height: 450px;
          margin: 60px auto 0 auto;
          border-radius: 20px;
          background: #fff;
          box-shadow: 0 0 20px rgba(0,0,0,0.3);
          font-size: 0;
          opacity: 0.9;
          @media screen and (max-width: 500px) {
            width: 90%;
            height: 70%;
            margin-top: 30px;
          }
          &:hover{
            animation: change 1s linear;
            animation-fill-mode: forwards;
            @keyframes change {
              0% {opacity: 0.9;}
              100% {opacity: 1;}
            }
          }
          .left{
            width: 30%;
            height: 450px;
            text-align: center;
            display: inline-block;
            .logo{
              display: block;
              padding-top: 140px;
              color: #e44f28;
              font-size: 70px;
            }
          }
          .right{
            display: inline-block;
            width: 70%;
            height: 450px;
            vertical-align: top;
            .company{
              padding-top: 30px;
              color: #945c4c;
              font-size: 22px;
              font-weight: bold;
              @media screen and (max-width: 500px) {
                font-size: 15px;
              }
            }
            .time,.job-content{
              margin-top: 20px;
              color: #af7464;
              font-size: 16px;
              @media screen and (max-width: 500px) {
                font-size: 14px;
              }
              .address{
                color: red;
                text-decoration: underline;
                margin-left: 40px;
              }
            }
            .job-content{
              margin-bottom: 20px;
            }
            .job{
              margin-top: 20px;
              color: #af7464;
              font-size: 18px;
              @media screen and (max-width: 500px) {
                font-size: 14px;
              }
            }
            .details{
              color: #000;
              font-size: 16px;
              line-height: 36px;
              @media screen and (max-width: 500px) {
                font-size: 14px;
                line-height: 22px;
              }
            }
          }
        }
        .dots-wrapper{
          margin-top: 30px;
          text-align: center;
          font-size: 0;
          .dot{
            display: inline-block;
            width: 10px;
            height: 10px;
            margin-left: 40px;
            border-radius: 50%;
            background: #623c32;
            cursor: pointer;
            &.active{
              background: #af7164;
            }
            &:first-child{
              margin-left: 0;
            }
          }
        }
      }
      .section5{
        background: #48819b;
        .title{
          padding-top: 100px;
          text-align: center;
          color: #fff;
          font-size: 26px;
          @media screen and (max-width: 500px) {
            padding-top: 20px;
          }
        }
        .works-wrapper{
          display: flex;
          width: 90%;
          margin: 10px auto 0 auto;
          justify-content: space-between;
          flex-wrap: wrap;
          .works{
            width: 45%;
            height: 250px;
            background: #fff;
            border-radius: 10px;
            margin-top: 40px;
            opacity: 0.9;
            @media screen and (max-width: 500px) {
              width: 95%;
              height: 350px;
              margin: 20px auto 0 auto;
            }
            .name{
              padding: 30px 0 0 20px;
              color: #4985b4;
              font-weight: bold;
              font-size: 18px;
            }
            .text{
              padding: 30px 20px 0 20px;
              color: #000;
              font-size: 16px;
              line-height: 26px;
              letter-spacing: 1px;
            }
            .link{
              display: block;
              margin: 30px 0 0 20px;
              width: 180px;
              height: 30px;
              text-align: center;
              border-radius: 5px;
              line-height: 30px;
              border: 1px solid rgba(7,17,27,0.1);
              color: #e6e6e6;
              &:hover{
                cursor: pointer;
                animation: linkFade 2s;
                @keyframes linkFade {
                  0% {color: #e6e6e6;}
                  100% {color: #000;background: #e6e6e6;opacity: 0.8;}
                }
              }
            }
          }
        }
        .github{
          width: 80%;
          margin: 80px auto 0 auto;
          text-align: center;
          a{
            color: #fff;
            text-decoration: underline;
          }
          @media screen and (max-width: 500px) {
            margin: 20px auto 0 auto;
          }
        }
        .button-wrapper{
          width: 80%;
          margin: 30px auto 0 auto;
          display: none;
          @media screen and (max-width: 500px) {
            display: block;
          }
          .pre,.next{
            font-size: 30px;
            color: #fff;
          }
          .pre{
            float: left;
          }
          .next{
            float: right;
          }
        }
      }
      .section6{
        background: #c7937b;
        .title{
          padding-top: 100px;
          text-align: center;
          color: #fff;
          font-size: 26px;
          @media screen and (max-width: 500px) {
            padding-top: 20px;
          }
        }
        .text-wrapper{
          width: 60%;
          margin: 50px auto 0 auto;
          text-align: center;
          @media screen and (max-width: 386px) {
            margin-top: 20px;
          }
          .contact-item{
            display: inline-block;
            font-size: 22px;
            margin: 30px 80px 0 0;
            &:last-child{
              margin-right: 0;
            }
            &:nth-of-type(2),&:last-child{
              @media screen and (max-width: 386px) {
                margin-right: 20px;
              }
            }
            &.one{
              color: #ef0039;
            }
            &.two{
              color: #33ccff;
            }
            &.three{
              color: #4be594;
            }
            &.four{
              color: #e8ee80;
            }
          }
          .text{
            margin-top: 60px;
            line-height: 50px;
            color: #fff;
            font-size: 18px;
            @media screen and (max-width: 386px) {
              margin-top: 30px;
              font-size: 14px;
              line-height: 36px;
            }
          }
          .icon{
            display: inline-block;
            margin: 50px 30px 0 0;
            border: 1px solid #fff;
            border-radius: 50%;
            width: 42px;
            height: 42px;
            text-align: center;
            line-height: 42px;
            color: #fff;
            font-size: 22px;
            cursor: pointer;
            @media screen and (max-width: 500px) {
              margin-top: 10px;
            }
            &:last-child{
              margin-right: 0;
            }
          }
        }
        .bottom{
          position: absolute;
          bottom: 0;
          left: 0;
          width: 100%;
          height: 50px;
          border-top: 1px solid rgba(7,17,27,0.1);
          .text{
            color: rgba(7,17,27,0.3);
            font-size: 14px;
            text-align: center;
            line-height: 50px;
          }
        }
      }
    }
  }
</style>
