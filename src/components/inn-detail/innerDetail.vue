<template>
  <div class="inn-detail-container">
    <div class="inn-content">
      <div class="inn-name"><span class='inn-name-title'>{{hotelDetail.name}}</span><span class='word-qi'>起</span> <span class='inn-price'>￥{{hotelDetail.price}}</span>  </div>

      <div class="inn-img"  ref='innImg'>

        <swiper :options="swiperOptionTop" class="gallery-top" ref="swiperTop">
          <swiper-slide v-for='item in hotelDetail.pictures' ><img :src="item" alt=""  :style='{height:height+"px"}'></swiper-slide>
<!--           <swiper-slide ><img src="http://139.129.118.14:8887/group1/M00/00/04/i4F2Dln6xxOAF-kMAAcqOc14jz8969.png" alt=""></swiper-slide>
          <swiper-slide ><img src="http://139.129.118.14:8887/group1/M00/00/04/i4F2Dln6xxOAF-kMAAcqOc14jz8969.png" alt=""></swiper-slide>
          <swiper-slide ><img src="http://139.129.118.14:8887/group1/M00/00/04/i4F2Dln6xxOAF-kMAAcqOc14jz8969.png" alt=""></swiper-slide>
          <swiper-slide ><img src="http://139.129.118.14:8887/group1/M00/00/04/i4F2Dln6xxOAF-kMAAcqOc14jz8969.png" alt=""></swiper-slide> -->

          <div class="swiper-button-next swiper-button-white" slot="button-next"></div>
          <div class="swiper-button-prev swiper-button-white" slot="button-prev"></div>
        </swiper>
        <!-- swiper2 Thumbs -->

<!--         <div class='img-lists-right'>
          <ul>
            <li>
              <img src="./img/01.png" alt="">
            </li>
            <li>
              <img src="./img/01.png" alt="">
            </li>
            <li>
              <img src="./img/01.png" alt="">
            </li>
          </ul>
        </div> -->
      </div>

      <div class="inn-describe"> 

        <div>
          <p class="inn-intro-title">酒店地址</p>
          <p class='inn-address'>{{hotelDetail.address}}</p> 
        </div>

        <div>
          <p class="inn-intro-title">酒店介绍</p>
          <p class='inn-address'>{{hotelDetail.description}}</p>  
        </div>

        <div>
          <p class="inn-intro-title">酒店设施</p>
          <ul class='inn-intro-service'>
            <li>免费停车场</li>
            <li>吹风机</li>
            <li>行李寄存</li>
            <li>叫醒服务</li>
            <li>24小时热水</li>
            <li>餐厅</li>
            <li>免费洗漱用品</li>
          </ul>
        </div>

        <div>
          <p class="inn-intro-title">服务条款</p>
          <ul class='condition inn-intro-service'>
            <li>  <span>入住和离店</span>   <span>入住时间：14:00以后      离店时间：12:00以前</span></li>
            <li>  <span>儿童政策 </span> <span>不接受18岁以下客人单独入住</span></li>
            <li>  <span>膳食安排</span> <span>自助早餐 RMB 28</span></li>
            <li>  <span>宠物</span> <span>不可携带宠物</span></li>
          </ul>
        </div>        



      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

import Vue from 'vue'

import VueAwesomeSwiper from 'vue-awesome-swiper'

import 'swiper/dist/css/swiper.css'

Vue.use(VueAwesomeSwiper)

import { swiper, swiperSlide } from 'vue-awesome-swiper'



export default {
  name: 'app',
  data() {
      return {
        swiperOptionTop: {
          notNextTick: true,
          nextButton: '.swiper-button-next',
          prevButton: '.swiper-button-prev',
          spaceBetween: 10
        },
        hotelDetail:{},
        height:""
        // ,
        // swiperOptionThumbs: {
        //   notNextTick: true,
        //   spaceBetween: 10,  //  slider间的间距
        //   // centeredSlides: true,  // slider  是否居中
        //   // slidesPerView: 3,  //  展示的数量
        //   touchRatio: 0.2,
        //   slideToClickedSlide: true,
        //   direction : 'vertical'
        // }
      }
    },
    mounted() {
      const swiperTop = this.$refs.swiperTop.swiper
      // const swiperThumbs = this.$refs.swiperThumbs.swiper
      // swiperTop.params.control = swiperThumbs
      // swiperThumbs.params.control = swiperTop

      let height=this.$refs.innImg.clientWidth/1.7
      this.height=height
      let that=this;
      window.onresize=function(){
        that.height=that.$refs.innImg.clientWidth/1.7
      }
    },

  created() {
    let id=this.$route.params.id;
    this.getHotelDetail(id)
  },  
  methods:{
    getHotelDetail(id){
      axios.get("http://139.129.118.14:8082/WestBoundA/hotel_getHotelById.json",{
        params:{
          hotelId:id
        }
      }).then((res)=>{
        // console.log(res)



        this.hotelDetail=res.data.hotel
        // console.log(this.hotelDetail)

        if(this.hotelDetail.pictures.indexOf(',')!=-1){
          this.hotelDetail.pictures=this.hotelDetail.pictures.split(",")
          console.log(1)
        }

        else{
          let pictures=[]
          pictures.push(this.hotelDetail.pictures)
          this.hotelDetail.pictures=pictures

          console.log(2)

        }


        console.log("hotelDetail",this.hotelDetail)


      })
    }
  },
  components:{
    swiper,
    swiperSlide,
  }
}
</script>

<style lang='less'>
p.inn-address{
  padding-top:21px;
  font-weight:300;
  padding-left:15px;
}

a{
  text-decoration:none;
  /*color:#000;*/
}

ul,li{
  padding:0;
  margin:0;
  list-style: none;
}

.inn-detail-container{
  width:66%;
  margin:0 auto;
  padding-bottom:367px;
}

.inn-content{
  margin-top:42px;
  .inn-name{
    font-size:36px;
    margin-bottom:24px;

  .word-qi{
    float: right;
    font-size: 18px;
    color: #000;
    display: inline-block;
    padding: 10px;
    font-weight: 600;

    }
    .inn-price{
        float:right;
        color: #50bbdb;
        font-size:28px;
        font-weight:600;
        line-height: 36px;
    }

    .inn-name-title{
      font-weight:600;
    }
  }

  .inn-describe{
    margin-top:50px;


    div{
      margin-bottom:53px;
      .inn-intro-title{
        color: #221815;
        font-size:26px;
        padding-bottom:23px;
        border-bottom:1px solid rgba(229, 229, 229, 1);
        font-weight:600;
        padding-left:15px;
      }
      p{
        color: #959595;
      }

      ul{
        li{
          display: inline-block;
          width:200px;
          list-style: #000;
          padding:10px;
          // list-style-type:circle;
          position: relative;
          font-weight:300;
          color: #959595;
        }
        li::before{
          font-weight: 900;
          content:'·';
          position: absolute;
          display: inline-block;
          margin-left:-20px;

        }
      }

      ul.condition{
        li{
          display: block;
          width:100%;
          span:nth-child(1){
            display: inline-block;
            width:300px;
            color:#000;
          }
          span{
            color: #959595;
          }
        }
      }

    }
  }
}


.inn-img{
  // height:500px;
  display: flex;
  width:100%;
}
  .swiper-container {
    background-color: #000;
  }
  .swiper-slide {
    background-size: cover;
    background-position: center;
  }
  .gallery-top {
    height: 100%;
    // width: 80%!important%;
    flex:4;
    // display: inline-block;
  }
  .img-lists-right {
    // width: 20%!important;
    flex:1;
    box-sizing: border-box;
    display: inline-block;
    display: flex;
    flex-direction:column;
    background: rgba(0,0,0,.2);

  }
  .img-lists-right .swiper-slide {
    width: 100%;
    height:25%;
    // height: 100%;
    opacity: 0.4;
    flex:1;
  }
  .img-lists-right .swiper-slide-active {
    opacity: 1;
  }
.gallery-top img{
  width:100%;
  height: 100%;
  max-height: 500px;
  // max-width: 
}

.img-lists-right img{
    width:100%;
}

.inn-intro-service{
  padding-top:24px;
  padding-left:20px;
}

</style>
