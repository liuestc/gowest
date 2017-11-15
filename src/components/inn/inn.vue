<template>
  <div class="inn-container">
    <div class="more-specialty">
      <!-- <div class="more-food-title">当地美食  <span class='food-en'>Local Delicacy   </span></div> -->

      <div class="food-content">

        <!-- <ul class="food-lists"> -->

        <paginate  name="languages" :list="hotels" :per="4" ref="paginator" class="food-lists">  
          <li class='list' v-for='item in paginated("languages")'>
            <router-link :to='{name:"innDetail",params:{id:item.id}}'> <img :src="item.cover" alt=""  v-bind:style="{  height: clientWidth + 'px' }"></router-link>
            <p class="list-name"> {{item.name}} </p>
            <div class="list-desc-wrapper">
             
              <p class="specialty-desc" >{{item.type.name}}</p>
              <p class="specialty-desc" v-if='item.isParking'>
                停车场
              </p> 
              <p class="specialty-desc" v-if='item.haveHotWater'>热水</p>
              <p class="specialty-desc" v-if='item.haveWashSupplies'>洗浴保健</p> 
              <p class="specialty-desc" v-if='item.isHaveWIFI' >免费wifi</p> 
              <p class="specialty-desc" v-if='item.isDiscount' >优惠促销</p> 
              <p class="specialty-desc" v-if='item.luggage' >行李寄存</p>               
            </div>
                    
            <div class="price-container">
              <p class="inn-price">价格 ： <span class='inn-price-content'> ￥{{item.price}}</span>/day</p>
              <p class="line-detail"><router-link :to='{name:"innDetail",params:{id:item.id}}'>查看酒店详情</router-link></p> 
            </div>
          </li>
        </paginate>
<!--         </ul> -->

        <div class="paginate-wrapper">
          <div class="all-page">共 <span class='list-num-wrapper'>{{listNums}}</span>条</div>
          <paginate-links for="languages" :show-step-links="true"  >
              </paginate-links>
          <div class='page-input'><span>前往</span><input type="text" v-model='pages' @change="goToPage"><span>页</span></div>
        </div>

      </div>
    </div>
  </div>
</template>

<script>

import Vue from 'vue'
// import ImgWrapper from './components/ImgWrapper/imgWrapper'
import VuePaginate from 'vue-paginate'

Vue.use(VuePaginate)

import axios from 'axios'
export default {
  name: 'Inn',
  components: {

  },
  created(){
    this.getAllHotel()
  },
  data(){
    return{
      hotels:[],
      listNums:"",
      pages:"",
      paginate: ['languages'],
      clientWidth:""
    }
  },
  methods:{
    goToPage(){
      // console.log("page",this.pages)
      if (this.$refs.paginator) {
          this.$refs.paginator.goToPage(this.pages)
      }
    },  

    getAllHotel(){
      axios.get('http://139.129.118.14:8082/WestBoundA/hotel_listHotel.json').then(res=>{
        console.log("hotel",res)
        this.hotels=res.data.hotels;
        this.listNums=this.hotels.length
      })
    }
  },
  mounted(){

      this.clientWidth = (`${document.documentElement.clientWidth}`*.6-40)/(2*2)
      this.$nextTick(() => {

        const that = this;
        window.onresize = function temp() {

            that.clientWidth = (`${document.documentElement.clientWidth}`*.6-40)/(2*2)
            console.log("clientWidth",that.clientWidth)
        };
      })     
  }
}
</script>

<style lang='less'>
a{
  text-decoration:none;
}

ul,li{
  list-style: none;
}

.inn-container{
  width:60%;
  margin:0 auto;
  padding-bottom:500px;
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

      .food-lists{
        display: flex;
        flex-wrap:wrap;
        width:100%;
        min-width: 600px;
        max-width:1400px;
        margin-top:26px;
        
          li.list{
            position: relative;
            img{
              width:100%;
              // height:160px;
              // max-height:290px;
              // max-width:570px;
            }
            flex:0 1 50%;
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
              display: block;
              font-weight:600;
            }
            .list-desc-wrapper{
              margin-bottom:100px;
              p.specialty-desc{
                width:49%;
                text-align: center; 
                display: inline-block;
                font-size: 14px;
                font-weight: 300;
                font-style: normal;
                font-stretch: normal;
                // line-height: 30px;
                letter-spacing: 0px;
                color: #959595; 
                // padding:0 40px;
                text-align: left;
                padding:0;
                padding-top:6px; 
                margin:0;

              }
              p.specialty-desc::before{
                content:"·";
                display:inline-block;
                padding-right:20px;
                vertical-align: middle;
              }
            }


            .price-container{
              position: absolute;
              bottom:0;
              width:88%;
              display: block;
              padding:10px;
              margin:20px 0;
              border-top:1px solid rgba(228, 228, 228, 1);
              border-bottom:1px solid rgba(228, 228, 228, 1);
              .inn-price{
                text-align: left;
                font-size: 14px;
                display: inline-block;
                width:49%;
                color:#959595;
                .inn-price-content{
                  font-weight:600;
                  font-size:22px;
                  color:#000;
                }
              }

              .line-detail{
                border:1px solid rgba(80, 187, 219, 1);
                padding:8px 20px;
                display: inline-block;
                color:#fff;
                display: inline-block;
                text-align: right;
                background: rgba(80, 187, 219, 1);
                transform: translateX(25%);
                a{
                  color:#fff;
                  font-weight:300;
                  font-size:14px;
                }
              }
            }

          }
        
      }
    } 
  } 
}

  .paginate-wrapper{
    position: relative;
    text-align: center;
    margin-top:80px;
    font-size:12px;

    .all-page{
      display: inline-block;
      span.list-num-wrapper{
        display: inline-block;
        padding:0 10px;
      }
    }
    .paginate-links.languages{
      display: inline-block;

      margin:0 auto;
      text-align: center;
      li{
        display: inline-block;
        padding:7px 12px;
        border:1px solid #ccc;
        border-left:none;
        // color:#fff;
      }
      li:nth-child(1){
        border-left:1px solid #ccc;
      }
      li.active{
        border:1px solid #50bbdb;
        a{
          color:#fff;
        }

      }
    }

    .page-input{
      // position: absolute;
      margin-left:-6px;
      display: inline-block;
      input{
        width:20px;
        padding:6px;
      }

      span{
        display: inline-block;
        padding:7px ;
        // border:1px solid #ccc;
        border-left:none;
      }

      span:nth-child(1){
        border-right:none;
      }
    }   
  }
</style>
