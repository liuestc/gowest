<template>
  <div class='line-container'>
    <div class="line-title">
      <p class="line-title-content">{{middlePoint}}</p>
      <p class="sub-title">{{dayNum}}日自驾</p>
    </div>
    <div class="line-swiper" ref='lineSwiper' :style='{height:height+"px"}'>
          <swiper :options="swiperOptionTop" class="gallery-top" ref="swiperTop">
            <swiper-slide v-for='item in lines'><router-link :to='{name:"lineDetail",params:{id:item.id}}' ><img :src="item.cover" alt=""></router-link></swiper-slide>
            <div class="swiper-button-next swiper-button-white" slot="button-next"></div>
            <div class="swiper-button-prev swiper-button-white" slot="button-prev"></div>
          </swiper>
          <!-- swiper2 Thumbs -->
          <swiper :options="swiperOptionThumbs" class="gallery-thumbs" ref="swiperThumbs">
            <swiper-slide v-for='item in lines'><img :src="item.cover" alt=""></swiper-slide>
          </swiper>
    </div>

    <div class="line-intro">
      <!-- <div class="intro-title"> -->
        <ul class="title-list">
          <li class='province' v-for='(item,index) in labelsList' @click='toggleLabel(item,index)'  :class="{activeLabel:item.isActive}">{{item.name}}</li>
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
      <div class="more-title" >更多路线 ></div>

      <div class="more-specialty">
        <!-- <div class="more-food-title">当地美食  <span class='food-en'>Local Delicacy   </span></div> -->

        <div class="food-content">

          <ul class="food-lists" ref='imgWidth'>
            <li class='list'  v-for='item in lines'>
              <img :src="item.cover" alt=""  v-bind:style="{  height: clientHeight + 'px' }">
              <p class="list-name"> {{item.origin}} -{{item.end}} </p>
              
              <div class="line-intro-wrapper">
                <p class="specialty-desc">
                  时间：{{item.journeySchedule}}
                </p> 
                <p>地点：{{item.origin}}</p>
                <p class='day-num'>行程：{{item.dayNum}}</p> 
                <router-link class="line-detail" tag="div"  :to='{name:"lineDetail",params:{id:item.id}}'>查看详情</router-link>                    
              </div>

      
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

import axios from 'axios'

const self=this
export default {
  name: 'Line',
  data() {
      return {
        index:"",
        labelsList:[{name:"必去景点"},{name:"当地美食"},{name:"文化风俗"}],
        swiperOptionTop: {
           // loop:true,
          // autoplay:true,
          // notNextTick: true,
          // speed:2000,
          nextButton: '.swiper-button-next',
          prevButton: '.swiper-button-prev',
          // spaceBetween: 10,
          onSlideChangeEnd :(swiper)=> {
            let index2=swiper.activeIndex
            // console.log(swiper)
            // console.log(index2)
            // this.index=index
            // console.log("self",this.lines)
            // console.log("this",this)
            this.middlePoint=this.lines[swiper.activeIndex].middlePoint

          }
        },
        swiperOptionThumbs: {
          notNextTick: true,
          spaceBetween: 10,
          centeredSlides: false,
          slidesPerView: 7,
          touchRatio: 0.2,
          slideToClickedSlide: true,
          nextButton: '.swiper-button-next',
          prevButton: '.swiper-button-prev',
          centeredSlides: 'center'      
        },
        lines:{},
        middlePoint:"四川-马尔康-色达",
        dayNum:"5",
        isActive:true,
        food:[{name:"大碗茶"},{name:"九小碗"},{name:'龙抄手'}],
        clientHeight:"",
        flag:true,
        height:"",
        clientWidth:""
      }
    },
    mounted() {
      
      const swiperTop = this.$refs.swiperTop.swiper
      const swiperThumbs = this.$refs.swiperThumbs.swiper
      swiperTop.params.control = swiperThumbs
      swiperThumbs.params.control = swiperTop

      console.log("line mounted",swiperTop)
      console.log("line mounted",swiperThumbs)

      axios.get("http://139.129.118.14:8082/WestBoundA/route_listRoutes.json").then(res=>{
        let linesAll=res.data.routes;
        console.log("lines",linesAll)
        this.lines=linesAll
      })

      // this.getMoreLine()
      let height=this.$refs.lineSwiper.clientWidth/2
      this.height=height


      this.clientHeight = (this.$refs.imgWidth.clientWidth-80)/(4*1.3);
      this.$nextTick(() => {

        const that = this;
        window.onresize = function temp() {
            that.clientHeight = (that.$refs.imgWidth.clientWidth-80)/(4*1.3);
   

            that.height=that.$refs.lineSwiper.clientWidth/2
        };
      })

    },
    created(){
        this.labelsList.forEach((item,index)=>{
          Vue.set(item,"isActive",false)
        })
        this.labelsList[0].isActive=true
    },

    methods:{
      getMoreLine(){
        if(this.flag){
          this.lines.splice(0,4)
        }
        console.log(this.lines)
      },
      toggleLabel(curItem,curIndex){
        console.log("id",curItem.id)
        console.log("index",curIndex)


        this.labelsList.forEach(function(v,i){
          i==curIndex?v.isActive=true:v.isActive=false
        })

        // this.getLabelCelebrity(curItem.id)

      }
    },
  components:{
    swiper,
    swiperSlide,
  }

}
</script>

<style lang='less'>
.activeLabel{
  // transition:all .5s ease;
  color:#000 !important;
  border-bottom:4px solid rgba(80, 187, 219, 1);
  font-weight:600!important;
}

div,li{
  cursor:default
}

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
    padding-bottom:500px;
    .line-title {
      font-size:30px;
      padding:50px 0 32px;
      .line-title-content{
        font-weight:600;
      }
      .sub-title{
        font-size:20px;
        padding-top:18px;
        color: #959595;
        font-weight:300;
      }
    }
    .line-swiper{
      // height:500px;
        .gallery-top {
          height: 80%!important;
          width: 100%;

          img{
            height:100%;
            width:100%;
          }
        }

    }

    .line-intro{
      padding-top:50px;
      .title-list{
        text-align: center;
        li{
          display: inline-block;
          font-size:20px;
          padding:10px 0;
          margin:0 20px;
          text-align: center;
          font-weight:300;
        }
        
      }

      .content-list{
        margin-top:30px;
        li{
          display: inline-block;
          width:23%;
          font-size: 18px;
          color: #959595;
          text-align: center;
          padding:10px 0px;
          font-weight:300;
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
      margin-left:-15px;
      .more-title{
        margin-top: 30px;
        font-size: 18px;
        padding: 10px 0;
        border-top: 1px solid #ccc;
        padding-top: 40px;
        font-weight:600;
        padding-left:15px;
      }
      .more-specialty{
       padding-left:15px;
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
                position: relative;
                margin-bottom:20px;
                img{
                  width:100%;
                  // height:110px;
                }
                flex:0 1 25%;
                box-sizing: border-box;
                margin-top:6px;
                padding-right:20px;

                .list-name{
                  padding:10px 0;
                  font-size:20px;
                  color: #221815;
                  margin-bottom:116px;
                  font-weight:600;
                }

                .line-intro-wrapper{
                  position: absolute;
                  bottom:0;
                  p{
                    font-size: 14px;
                    font-weight: 300;
                    font-style: normal;
                    font-stretch: normal;
                    // line-height: 30px;
                    letter-spacing: 0px;
                    color: #959595; 
                    text-align: left;
                    padding:0;
                    padding-top:6px; 
                    margin:0;          
                  }
                  p.day-num{
                    margin-bottom:10px;
                  }
                  .line-detail{
                    border:1px solid #000;
                    padding:6px 16px;
                    display: inline-block;
                    margin-top:12px;
                    color:#000;
                    font-weight:300;
                    font-size:14px;
                    // position: absolute;
                    // bottom:0;
                  }                  
                }

              }
            
          }
        } 
      }      
    }

  }

  .swiper-container {
    background-color: #fff!important;
  }
  .swiper-slide {
    background-size: cover;
    background-position: center;
  }

  .gallery-thumbs {
    height: 20%!important;
    box-sizing: border-box;
    padding: 10px 0;
    img{
      width:100%;
      height:100%;

    }
  }
  .gallery-thumbs .swiper-slide {
    width: 25%;
    height: 100%;
    // opacity: 0.4;
  }
  .gallery-thumbs  {
    opacity: 1;
  }


.swiper-button-prev.swiper-button-disabled, .swiper-button-next.swiper-button-disabled{
      // /* opacity: 0.35; */
    cursor: auto;
    pointer-events: auto!important;
   
}

</style>
