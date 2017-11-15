<template>
  <div class="info-container">
    <ul class="info-list">
      <li v-for='item in infoList' >
        <img :src="item.cover" alt="" class="cover" v-bind:style="{  height: clientHeight + 'px' }">
        <router-link class="info-content"  tag='div'  :to='{name:"infoDetail",params:{id:item.id}}' >
          <div class="info-time"><span class='month'>{{getTime(item.createTime).m}}</span> <span class='day'>{{getTime(item.createTime).d}}</span></div>
          <div class="info-summary">
            <p class="info-title">{{item.title}}</p>
            <p class='info-main'> {{item.summary}}</p>

            <p class="info-publisher"><span class='info-publisher-from'>源自</span> <span class="publisher2">{{item.publisher}}</span>  <span class='info-view-more'>查看详情&nbsp;></span></p>
          </div>
        </router-link>
      </li>
    </ul> 
  </div>
</template>

<script>

import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      infoList:[],
      clientHeight:[]
    }
  },
  created(){
    this.getInfoList()
  },
  mounted(){
    // this.clientHeight = `${document.documentElement.clientWidth}px`;

    // const that = this;
    // window.onresize = function temp() {
    //     that.clientHeight = (`${document.documentElement.clientWidth}`*0.6
    //     console.log("clientHeight",that.clientHeight)
    // }
  this.clientHeight = `${document.documentElement.clientWidth}px`;

    const that = this;
    window.onresize = function temp() {
        that.clientHeight = (`${document.documentElement.clientWidth}`*.6)/2.2
        console.log("clientHeight",that.clientHeight)
    };

  },
  methods:{
    getInfoList(){
      axios.get("http://139.129.118.14:8082/WestBoundA/news_listNews.json").then((res)=>{
        console.log("infolist",res.data)
        this.infoList=res.data.newses
      })
    },
    getTime(time){
      var date = new Date(time);
      // Y = date.getFullYear()
      let  M = (date.getMonth()+1 < 10 ? '0'+(date.getMonth()+1) : date.getMonth()+1) 
      let  D = date.getDate()


      return {
        m:M,
        d:D
      }
    }    

  },
  computed:{

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='less'>


*, ul ,li{
  list-style-type: none;
  padding: 0;
  margin:0;

}

a {
  color: #42b983;
}

.publisher2{
  display: inline-block;
  padding:0 10px;
}

.info-container{
  width:60%;
  margin:0 auto;
  padding-bottom:460px;

  .info-list{
    li{
      // height:100%;
      margin-top:60px;
      height:800px;
      height:100%;
      width:100%;
      img.cover{
        width:100%;
        // max-height:400px;
      }

    .info-content{
      // overflow: hiden;
      margin-top:20px;
      display: flex;
      .info-time{
        flex: 80px;
        border:1px solid #000;
        // border-bottom:none;
        width:80px;
        height:70px;
        text-align: center;
        // vertical-align: middle;
        .month{
          font-size:34px;
          display: block;
          padding-top:6px;

        }

        .day{
          display: block;
          font-size:18px;
        }

      }
      .info-summary{
        // display: inline-block;
        // float: left;
        box-sizing: border-box;
        flex:100%;
        padding:0 30px;
        .info-title{
          margin-bottom:18px;
          font-size:18px;
          font-weight:600;
        }
        .info-main{
          font-size:15px;
          color: #959595;
          line-height: 22px;
          font-weight:300;
        }
        .info-publisher{
          margin-top:20px;
          border-left: 2px solid #000;
          padding-left: 10px;
        }
      }
    }

    }
  }
}

.info-view-more{
  float: right;
  font-weight: 400;
  font-size:14px;

}

      .info-view-more:hover{
        color:#50bbdb;
      }

span.info-publisher-from{
  color:#959595;
  font-weight:300;
}
</style>
