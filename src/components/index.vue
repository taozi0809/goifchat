<template>
  <div class="index">
    <div class="header">
      <div class="logo-box">
        <img :src="obj.logoImgUrl" alt="">
      </div>
      <div class="menu-box">
        <ul>
          <li>
            <a href="javascript:;">{{obj.menu.a1}}</a>
          </li>
          <li>
            <a href="javascript:;">{{obj.menu.a2}}</a>
          </li>
          <li @click="changeLanguageFun">
            <a href="javascript:;" :class="isLanguage">{{isLanguage=='ko'?'KR':'CN'}}</a>
          </li>
        </ul>
      </div>

    </div>
    <div class="banner">
      <swiper :options="swiperOption" ref="mySwiper">
        <!-- slides -->
        <swiper-slide>
          <div class="item item1 ">
            <img :src="obj.banner.item1.imgurl" alt="">
            <div class="des">
              <p>{{obj.banner.item1.des1}}</p>
              <p>{{obj.banner.item1.des2}}</p>
            </div>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="item item2">
            <img :src="obj.banner.item2.imgurl" alt="">
            <div class="des">
              <p>{{obj.banner.item2.des1}}</p>
              <!--<p>{{obj.banner.item2.des2}}</p>-->
            </div>
          </div>
        </swiper-slide>
        <swiper-slide>
          <div class="item item3">
            <img :src="obj.banner.item3.imgurl" alt="">
            <div class="des">
              <p>{{obj.banner.item3.des1}}</p>
              <p>{{obj.banner.item3.des2}}</p>
            </div>
          </div>
        </swiper-slide>

        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
    <div class="goifchat">
      <h2 class="goifchat-title">{{obj.goifchat.title}}</h2>
      <p class="goifchat-title-des">{{obj.goifchat.titleDes}}</p>
      <div class="app-img">
        <img :src="obj.goifchat.appImgUrl" alt="">
      </div>
      <div class="bot">
        <img :src="obj.goifchat.botBgImgUrl" alt="" class="bot-bg">

        <a :href="obj.downloadUrl" target="_blank" class="download-btn">
        <!--<a href="/static/pdf/bwingolf_whitepaper_kr.pdf" target="_blank" class="download-btn">-->
          <img :src="obj.goifchat.downloadImgUrl" alt="">
          <span>{{obj.goifchat.downloadBtnTxt}}</span>
        </a>
        <div class="footer">
          <img :src="obj.goifchat.botLogoImgUrl" alt="">
          <p>{{obj.goifchat.copy}}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { swiper, swiperSlide } from 'vue-awesome-swiper'
// import data from '../json/data'

export default {
  name: 'Index',
  data () {
    return {
      isLanguage: 'ko',//默认韩语
      swiperOption: {//swiper 配置
        initialSlide: 0,//默认第一页
        direction: 'horizontal',//横向滚动
        loop: false,//是否循环
        speed: 300,//滚动动画时间
        autoplay: {//自动滚动
          delay: 5000,
          stopOnLastSlide: false
        },
        pagination: {//小圆点
          el: '.swiper-pagination',
          clickable: true
        }
      }
    }
  },
  created: function created() {
    this.readContent();
  },
  components: {
    swiper,
    swiperSlide
  },
  computed: {
    mySwiper () {
      return this.$refs.mySwiper.swiper
    }
  },
  methods: {


    readContent: function () {
      var chObj = {
          logoImgUrl: require('../assets/img/logo.png'),
          downloadUrl:'./static/pdf/bwingolf_whitepaper_cn.pdf',
          menu: {
            a1: 'Goifchat',
            a2: '白皮书',
          },
          banner: {
            item1: {
              imgurl: require('../assets/img/banner/1.png'),
              des1: '高尔夫与区块链结合',
              des2: '重新定义高尔夫的精彩'
            },
            item2: {
              imgurl: require('../assets/img/banner/2.png'),
              des1: '高尔夫币支付果岭费',
              des2: 'Golf Coin Payment Green Fee'
            },
            item3: {
              imgurl: require('../assets/img/banner/3.png'),
              des1: '高尔夫币上交易所',
              des2: '球友共享高尔夫经济'
            }
          },
          goifchat: {
            title: 'GOLF CHAT',
            titleDes: '聚焦高尔夫球友社群球友的沟通工具，数字货币的钱包支持存储及转账。',
            appImgUrl: require('../assets/img/ko-app.png'),
            botBgImgUrl: require('../assets/img/bot-bg.png'),
            downloadImgUrl: require('../assets/img/download-logo.png'),
            downloadBtnTxt: 'WhitePaper  Download',
            botLogoImgUrl: require('../assets/img/bot-logo.png'),
            copy: 'Copyright © 2014-2018 www.bwingolf.com  All Rights Reserved'
          }
        };
      var koObj = {
        logoImgUrl: require('../assets/img/logo.png'),
        downloadUrl:'./static/pdf/bwingolf_whitepaper_kr.pdf',
        menu: {
          a1: 'Goifchat',
          a2: '白皮书',
        },
        banner: {
          item1: {
            imgurl: require('../assets/img/banner/1.png'),
            des1: '골프와 블록체인의 결합,',
            des2: '골프매력에 대한 재정의。'
          },
          item2: {
            imgurl: require('../assets/img/banner/2.png'),
            des1: '골프 코인으로 그린 피 결제',
            // des2: 'Golf Coin Payment Green Fee'
          },
          item3: {
            imgurl: require('../assets/img/banner/3.png'),
            des1: '골프코인 ICO, 골퍼들이 함께하는 골프경제',
            // des2: '球友共享高尔夫经济'
          }
        },
        goifchat: {
          title: 'GOLF CHAT',
          titleDes: '골프 동호회를 겨냥한 커뮤니케이션 도구, 가상화폐 지갑으로써 저축과 계좌이체 가능',
          appImgUrl: require('../assets/img/ko-app.png'),
          botBgImgUrl: require('../assets/img/bot-bg.png'),
          downloadImgUrl: require('../assets/img/download-logo.png'),
          downloadBtnTxt: '화이트 페이퍼 다운로드',
          botLogoImgUrl: require('../assets/img/bot-logo.png'),
          copy: 'Copyright © 2014-2018 www.bwingolf.com  All Rights Reserved'
        }
      };
     // console.log(data)

      this.obj = this.isLanguage == 'ch' ? chObj : koObj;
    },
    changeLanguageFun: function() {
      this.isLanguage = this.isLanguage == 'ko'?'ch':'ko'
      this.readContent()
    },

  }
}
</script>

<style lang="scss" scoped >
  @import "../lib/index.scss";
</style>
