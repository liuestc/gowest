<template>
  <div class="inn-detail-container">
    <div class="inn-content">
      <div class="inn-name">成都如家大酒店</div>

      <div class="inn-img">
<!--         <swiper :options="swiperOptionTop" class="gallery-top" ref="swiperTop">
            <swiper-slide ><img src="./img/01.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/02.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/03.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/04.png" alt=""></swiper-slide>


            <div class="swiper-button-next swiper-button-white" slot="button-next"></div>
            <div class="swiper-button-prev swiper-button-white" slot="button-prev"></div>
          </swiper> -->

          <div class="img-active">
            <img src="./img/02.png" alt="">
          </div>

          <div class="img-list">
            <ul>
              <li><img src="./img/01.png" alt=""></li>
              <li><img src="./img/03.png" alt=""></li>
              <li><img src="./img/04.png" alt=""></li>
            </ul>
          </div> 



<!-- 
          <swiper :options="swiperOptionThumbs" class="gallery-thumbs column" ref="swiperThumbs">
            <swiper-slide ><img src="./img/01.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/03.png" alt=""></swiper-slide>
            <swiper-slide ><img src="./img/04.png" alt=""></swiper-slide>
          </swiper> -->
      </div>
    </div>
  </div>
</template>

<script>
// import 'normalize.css/normalize.css'
// import Vue from 'vue'

// import VueAwesomeSwiper from 'vue-awesome-swiper'

// Vue.use(VueAwesomeSwiper)

// import { swiper, swiperSlide } from 'vue-awesome-swiper'


export default {
  name: 'app',
  // data() {
  //     // return {
  //     //   swiperOptionTop: {
  //     //     notNextTick: true,
  //     //     nextButton: '.swiper-button-next',
  //     //     prevButton: '.swiper-button-prev',
  //     //     spaceBetween: 10
  //     //   },
  //     //   swiperOptionThumbs: {
  //     //     notNextTick: true,
  //     //     spaceBetween: 10,  //  slider间的间距
  //     //     // centeredSlides: true,  // slider  是否居中
  //     //     slidesPerView: 3,  //  展示的数量
  //     //     touchRatio: 0.2,
  //     //     slideToClickedSlide: true,
  //     //     direction : 'vertical'
  //     //   }
  //     // }
  //   },
    mounted() {
      // const swiperTop = this.$refs.swiperTop.swiper
      // const swiperThumbs = this.$refs.swiperThumbs.swiper
      // swiperTop.params.control = swiperThumbs
      // swiperThumbs.params.control = swiperTop
    },
  // router,
  components:{
    // swiper,
    // swiperSlide,
  }
}
</script>

<style lang='less'>
a{
  text-decoration:none;
  /*color:#000;*/
}

ul,li{
  padding:0;
  margin:0;
  list-style: none;
}


.swiper-container {
    // background-color: #000;
  }
  .swiper-slide {
    background-size: cover;
    background-position: center;
  }
  .gallery-top {
    height: 80%!important;
    width: 100%;
    img{
      width:100%;
      height:400px;
    }
  }
  .gallery-thumbs {
    height: 20%!important;
    box-sizing: border-box;
    padding: 10px 0;
    img{
      height:160px;
    }
  }
  .gallery-thumbs .swiper-slide {
    width: 25%;
    height: 100%;
    opacity: 0.4;
  }
  .gallery-thumbs .swiper-slide-active {
    opacity: 1;
  }


.gallery-thumbs.column{
  flex-direction:column;
}
.inn-detail-container{
  /*font-size:20px;*/
  width:60%;
  margin:0 auto;  
  .inn-content{
    .inn-img{
      display: flex;
      align-items:  stretch;
      // width:100%;
      .gallery-top{
        display: 3;
      }

      .img-active{
        padding-right:10px;
        height:100%;
        flex:2;

        img{
          width:100%;
        }
      }

      .img-list{
        flex:1;
        ul{
          li{
            padding-bottom:10px;
            img{
              width:100%;
            }


          }

          li:last-child{
            padding-bottom:0;
          }
        }
      }



      .gallery-thumbs{
        display: 1;
      }
    }
  }

}
</style>
