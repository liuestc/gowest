<template>
  <div class='line-container'>
    <div class="line-title">
      <p class="title">成都-康定-色达</p>
      <p class="sub-title">5日自驾</p>
    </div>
    <div class="line-swiper">
          <swiper :options="swiperOptionTop" class="gallery-top" ref="swiperTop">
            <swiper-slide ><img src="./img/00.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/00.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/00.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/00.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/00.png" alt=""></swiper-slide>

            <div class="swiper-button-next swiper-button-white" slot="button-next"></div>
            <div class="swiper-button-prev swiper-button-white" slot="button-prev"></div>
          </swiper>
          <!-- swiper2 Thumbs -->
          <swiper :options="swiperOptionThumbs" class="gallery-thumbs" ref="swiperThumbs">
            <swiper-slide ><img src="./img/02.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/03.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/04.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/05.png" alt=""></swiper-slide>
          </swiper>
    </div>

    <div class="line-intro">
      <!-- <div class="intro-title"> -->
        <ul class="title-list">
          <li>必去景点</li>
          <li>当地美食</li>
          <li>文化风俗</li>
        </ul>

        <ul class='content-list'>
          <li>温江幸福田园</li>
          <li>温江幸福田园</li>
          <li>温江幸福田园</li>
          <li>温江幸福田园</li>
          <li>温江幸福田园</li>
        </ul>
      <!-- </div> -->
    </div>

    <div class="line-more"> 
      <div class="more-title">更多路线  ></div>

      <div class="more-specialty">
        <!-- <div class="more-food-title">当地美食  <span class='food-en'>Local Delicacy   </span></div> -->

        <div class="food-content">

          <ul class="food-lists">
            <li class='list'>
              <img src="./img/06.png" alt="">
              <p class="list-name"> 温江-西昌 </p>
              <p class="specialty-desc">
                时间：9月底
              </p> 
              <p>地点：哈哈哈</p>
              <p>行程：3天2夜</p> 
              <p class="line-detail">查看详情</p>          
            </li>
            <li class='list'>
              <img src="./img/03.png" alt="">
              <p class="list-name"> 温江-西昌 </p>
              <p class="specialty-desc">
                时间：9月底
              </p> 
              <p>地点：哈哈哈</p>
              <p>行程：3天2夜</p> 
              <p class="line-detail">查看详情</p>


            </li>
            <li class='list'>
              <img src="./img/02.png" alt="">
              <!-- <p class="list-name">   好吃的  </p> -->
              <p class="list-name"> 温江-西昌 </p>
              <p class="specialty-desc">
                时间：9月底
              </p> 
              <p>地点：哈哈哈</p>
              <p>行程：3天2夜</p> 
              <p class="line-detail">查看详情</p>           
            </li>
            <li class='list'>
              <img src="./img/04.png" alt="">
              <p class="list-name"> 温江-西昌 </p>
              <p class="specialty-desc">
                时间：9月底
              </p> 
              <p>地点：哈哈哈</p>
              <p>行程：3天2夜</p> 
              <p class="line-detail">查看详情</p>
            </li>
            <li class='list'>
              <img src="./img/05.png" alt="">
              <!-- <p class="list-name">  好吃的   </p> -->
              <p class="list-name"> 温江-西昌 </p>
              <p class="specialty-desc">
                时间：9月底
              </p> 
              <p>地点：哈哈哈</p>
              <p>行程：3天2夜</p>       
              <p class="line-detail">查看详情</p>       
            </li>                               
          </ul>
        </div>
      </div>

    </div>
  </div>
</template>

<script>

import 'normalize.css/normalize.css'
import Vue from 'vue'

import VueAwesomeSwiper from 'vue-awesome-swiper'

Vue.use(VueAwesomeSwiper)

import { swiper, swiperSlide } from 'vue-awesome-swiper'


export default {
  name: 'Line',
  data() {
      return {
        swiperOptionTop: {
          notNextTick: true,
          nextButton: '.swiper-button-next',
          prevButton: '.swiper-button-prev',
          spaceBetween: 10
        },
        swiperOptionThumbs: {
          notNextTick: true,
          spaceBetween: 10,
          centeredSlides: true,
          slidesPerView: 'auto',
          touchRatio: 0.2,
          slideToClickedSlide: true
        }
      }
    },
    mounted() {
      const swiperTop = this.$refs.swiperTop.swiper
      const swiperThumbs = this.$refs.swiperThumbs.swiper
      swiperTop.params.control = swiperThumbs
      swiperThumbs.params.control = swiperTop
    },
  // router,
  components:{
    swiper,
    swiperSlide,
  }



}
</script>

<style lang='less'>
ul,li{
  list-style: none;
  padding:0;
  margin:0;
}
  a{
    text-decoration:none;
    /*color:#000;*/
  }
  .line-container{
    width:60%;
    margin:0 auto;
    .line-title {
      font-size:30px;
      padding:80px 0 48px;
      .title{

      }
      .sub-title{
        font-size:20px;
        color: #959595;
      }
    }

    .line-intro{
      padding-top:80px;
      .title-list{
        text-align: center;
        li{
          display: inline-block;
          font-size:22px;
          padding:10px 0;
          margin:0 20px;
          text-align: center;
        }
        
      }

      .content-list{

        li{
          display: inline-block;
          width:23%;
          font-size: 18px;
          color: #959595;
          text-align: center;
          padding:20px 0px;
        }

        li::before{
          content:"·";
          color: rgba(80, 187, 219, 1);
          display: inline-block;
          padding-right:10px;
          font-weight:900;
          font-size: 36px;
          vertical-align: middle;
          line-height: 18px;


        }


      }
    }

    .line-more{

      .more-title{
         margin-top:140px;
         font-size:22px;
         padding:10px 0;
         border-bottom:1px solid #ccc;
      }
      .more-specialty{
       
        .more-food-title{
          font-size:36px;
          color: #221815;
          padding:0 20px;
          border-left:5px solid rgba(80, 187, 219, 1);
          margin-bottom:60px;

          .food-en{
            color:#959595;
            font-size:24px;
          }
        } 

        .food-content{

          .food-active{
            display: flex;
            img{
              flex:1;
              min-width: 400px;
              max-width:600px;

            }
            .food-info{
              flex:1;
              display: inline-block;
              padding:50px 100px 0 90px;

              .food-name{
                font-size:26px;
                padding-bottom:1em;
                border-bottom:1px solid rgba(229, 229, 229, 1)

              }

              .food-describe{
                padding-top:1em;
                font-size: 20px;
                color:#959595;
              }
            }
          }

          .food-lists{
            display: flex;
            flex-wrap:wrap;
            width:100%;
            min-width: 600px;
            max-width:1400px;
            
              li.list{
                img{
                  width:100%;
                }
                flex:0 1 25%;
                box-sizing: border-box;
                // padding-right:10px;
                // margin-right:24px;
                margin-top:24px;
                // text-align: center;
                // box-shadow: -1px 3px 10px 0px #ccc;
                padding-right:20px;

                .list-name{
                  padding:10px 0;
                  font-size:20px;
                  color: #221815;
                }
                p{
                  font-size: 16px;
                  font-weight: normal;
                  font-style: normal;
                  font-stretch: normal;
                  // line-height: 30px;
                  letter-spacing: 0px;
                  color: #959595; 
                  // padding:0 40px;
                  text-align: left;
                  padding:0;
                  padding-top:10px; 
                  margin:0;          
                }
                .line-detail{
                  border:1px solid #000;
                  padding:2px 10px;
                  display: inline-block;
                  margin-top:20px;
                  color:#000;
                }
              }
            
          }
        } 
      }      
    }

  }

  .swiper-container {
    background-color: #000;
  }
  .swiper-slide {
    background-size: cover;
    background-position: center;
  }
  .gallery-top {
    height: 80%!important;
    width: 100%;
  }
  .gallery-thumbs {
    height: 20%!important;
    box-sizing: border-box;
    padding: 10px 0;
  }
  .gallery-thumbs .swiper-slide {
    width: 25%;
    height: 100%;
    opacity: 0.4;
  }
  .gallery-thumbs .swiper-slide-active {
    opacity: 1;
  }


</style>
