<template>
  <div class="line2-container">
    <div class="day-list">
      <ul>
        <li class='day-step'  v-for='(item,index)s in lineDetail '>
          <img class='day-main' :src="item.bigPic" alt="">

          <div class='day-wrapper'>
              <div class="day-sub-wrapper">
                 <img class='day-sub' :src="item.ltlPic" alt="">
              </div>
             

              <div class="day-content">
                <p class="day-title">Day-{{index+1}}</p>
                <p class='days-name-steps'>{{item.name}}</p>
                <p class='day-step-desc'>{{item.describe}}</p>

                <!-- <p class="line2-btn"><router-link to='/destination'>查看详情</router-link></p> -->
              </div>            
          </div>
        </li>

<!--         <li class='day-step'>
          <img class='day-main' src="./img/m1.png" alt="">

          <div class='day-wrapper'>
              <img class='day-sub' src="./img/p1.png" alt="">

              <div class="day-content">
                <p class="day-title">Day-1</p>
                <p>成都-康定</p>
                <p>康定，一座享誉世界的历史文化名城；一座跑马山，名扬五洲四海.
                康定市具有悠久灿烂的历史文化，是川藏咽喉、茶马古道重镇、藏汉交汇中心。
              自古以来就是康巴藏区政治、经济、文化、商贸、信息中心和交通枢纽。
            全市幅员面积1.16万平方公里，是以藏族为主，汉、回、彝、羌等多民族聚居的城市。</p>
              </div>            
          </div>
        </li>


        <li class='day-step'>
          <img class='day-main' src="./img/m1.png" alt="">

          <div class='day-wrapper'>
              <img class='day-sub' src="./img/p1.png" alt="">

              <div class="day-content">
                <p class="day-title">Day-1</p>
                <p>成都-康定</p>
                <p>康定，一座享誉世界的历史文化名城；一座跑马山，名扬五洲四海.
                康定市具有悠久灿烂的历史文化，是川藏咽喉、茶马古道重镇、藏汉交汇中心。
              自古以来就是康巴藏区政治、经济、文化、商贸、信息中心和交通枢纽。
            全市幅员面积1.16万平方公里，是以藏族为主，汉、回、彝、羌等多民族聚居的城市。</p>
              </div>            
          </div>
        </li> -->


      </ul>
    </div>
  </div>
</template>

<script>

// import getData from  '../../assets/getData.js'
import axios from 'axios'


export default {
  name: 'LineDetail',
  data(){
    return {
      lineDetail:{},
      article0:""
    }
  },
  // router,
  components: {

  },
  created(){
    let id=this.$route.params.id;
    console.log("路线id",id)

    // let test=getData("route_listScheduleInRoute.json","routeId",id)
    // console.log("test",test)
    this.getLineDetail(id)
  },
  methods:{
    getLineDetail(id){
      axios.get("http://139.129.118.14:8082/WestBoundA/route_listScheduleInRoute.json",{
        params:{
          routeId:id
        }
      }).then(res=>{
        console.log("线路详情",res.data.schedules)
        this.lineDetail=res.data.schedules


        // article10=res.data.schedules[10]?res.data.schedules[0]:""
        // article0=res.data.schedules[0]
        // article0=res.data.schedules[0]
        // article0=res.data.schedules[0]




      })
    }
  }
}
</script>

<style lang='less'>
a{
  text-decoration:none;
  /*color:#000;*/
}

.days-name-steps{
  padding:2px 0 18px 0;
  color:#000!important;
  font-weight: 300;
}
.day-step>img{
  width:100%;
  // height:300px;
}

ul,li{
  list-style: none;
  padding:0;
  margin:0;
}
.line2-container{
  width:60%;
  margin:0 auto;
  padding-bottom:500px;

  .day-list{
    ul{
      li.day-step{
         width:100%;
         margin-top:60px;
         width:100%;
        .day-wrapper{
          display: flex;
          position: relative;
          margin-top:44px;
          align-items:flex-end;
          justify-content: space-between;
          box-sizing: border-box;
          padding-left:40px;
          .day-sub-wrapper{
             flex:0 0 200px;
             img{     
                width:100%;
                height:100%;
                max-height: 400px;
              }
          }

          .day-content{
            flex:0 0 300px;
            padding:33px 60px;
            box-shadow: 0px 5px 11.6px 1.4px  rgba(4, 0, 0, 0.05);
            margin-left:53px;
            margin-top:-100px;
            z-index: 100;
            background: #fff;
            margin-right: 100px;

            .day-title{
              color:#000;
              font-size:30px;
              font-weight:600!important;
            }

            p{
              font-size:18px;
              color: #959595;
              line-height:1.5;
              word-wrap:break-word;

              word-break:break-all;
            }
            .line2-btn{
              mrigin-topp:20px;
              padding:8px 16px;
              color:#fff;
              background:rgba(80, 187, 219, 1);
              display: inline-block;
            }
          }
        }
      }

      li.day-step:nth-child(even){
        .day-wrapper{
          // flex-direction:row-reverse;
          flex-direction: row-reverse;
          box-sizing: border-box;
          padding-right: 100px;
          padding-left: 0;
        }
      }
    }
  }
}

p.day-step-desc{
  font-weight:300;
}
</style>
