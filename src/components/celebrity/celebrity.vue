<template>
  <div class="celebrity">
    <ul class="province-tog">
      <!-- <li class='province' ></li> -->
      <li class='province' v-for='(item,index) in labelsList' @click='toggleLabel(item,index)'  :class="{activeLabel:item.isActive}">{{item.name}}</li>
    </ul>


    <paginate  name="languages" :list="celebrity" :per="9" class="celebrity-lists" ref="paginator">
    <!-- <ul class="celebrity-lists" ref='celebrityWidth'> -->
      <li   v-for="item in paginated('languages')" >
        <img :src="item.headPortrait" alt="" v-bind:style="{  height: clientHeight + 'px' }">
        <p class="name">{{item.name}}</p>
        <p class='other'>擅长：{{item.profession}}</p>
        <p class='other'>  特长：{{item.skill}}</p>
        <p class='other'>文章:&nbsp;&nbsp;{{item.articleNum}}</p>

        <router-link :to='{name:"celebrityDetail",params:{id:item.id}}' tag='p' class="view-more">查看详情&nbsp;></router-link>
      </li>
    </paginate>



    <div class="paginate-wrapper">
      <div class="all-page">共 <span class='list-num-wrapper'>{{listNums}}</span>条</div>
      <paginate-links for="languages" :show-step-links="true"  >
      </paginate-links>
      <div class='page-input'><span>前往</span><input type="text" v-model='pages' @change="goToPage"><span>页</span></div>
    </div>

  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VuePaginate from 'vue-paginate'

Vue.use(VuePaginate)
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',

      list:"",
      labelsList:"",
      isActive:true,
      celebrity:[],
      clientHeight:"",
      paginate: ['languages'],
      listNums:"",
      pages:""
    }
  },

  created(){
    this.getLabels();
  },
  mounted(){

      this.clientHeight = (`${document.documentElement.clientWidth}`*.6-60)/(3*1.6)
      this.$nextTick(() => {
        const that = this;
        window.onresize = function temp() {

            that.clientHeight = (`${document.documentElement.clientWidth}`*.6-60)/(3*1.6)
            console.log("clientHeight",that.clientHeight)
        };
      })    
  },
  methods:{
    goToPage(){
      // console.log("page",this.pages)
      if (this.$refs.paginator) {
          this.$refs.paginator.goToPage(this.pages)
      }
    },    

    getLabels(){
      axios.get('http://139.129.118.14:8082/WestBoundA/label_listBigShotLabel.json').then((res)=>{
        console.log("labelsList",res.data.labels)
        this.labelsList=res.data.labels
        this.labelsList.unshift({
          createTime:1508810666000,
          id:666,
          name:"全部",
          type:2
        })

        this.labelsList.forEach((item,index)=>{
          Vue.set(item,"isActive",false)
        })
        this.labelsList[0].isActive=true


        this.getLabelCelebrity(this.labelsList[0].id)

        console.log("labelsList",this.labelsList)

      })
    },
    toggleLabel(curItem,curIndex){
      console.log("id",curItem.id)
      console.log("index",curIndex)


      this.labelsList.forEach(function(v,i){
        i==curIndex?v.isActive=true:v.isActive=false
      })

      this.getLabelCelebrity(curItem.id)

    },
    getLabelCelebrity(label){
      if(label==666){
        axios.get("http://139.129.118.14:8082/WestBoundA/bigShot_listBigShot.json").then((res)=>{
          this.celebrity=res.data.bigShots

          this.listNums=this.celebrity.length
        })
      }


      else{
        axios.get("http://139.129.118.14:8082/WestBoundA/bigShot_getBigShotsByLabel.json",{
          params:{
            labelId:label
          }
        }).then((res)=>{
          this.celebrity=res.data.bigShots
          console.log("celebrity",this.celebrity)
          this.listNums=this.celebrity.length
        })        
      }

    }

  },
  components:{
    // wrapper
  }
}
</script>

<style lang='less'>

li.activeLabel{
  // transition:all .5s ease;
  color:#000 !important;
  border-bottom:4px solid rgba(80, 187, 219, 1);
  font-weight:600 !important;
}
.celebrity{
  width:60%;
  margin:0 auto;
  padding-bottom:420px;
  ul.province-tog{
    margin:30px auto;
    text-align: center;
    li.province{
      display: inline-block;
      margin: 0 18px 0px 18px;
      padding-bottom: 10px;
      font-size: 18px;
      color:#959595;
      font-weight:300;
    }
  }

  ul.celebrity-lists{
    display: flex;
    flex-wrap:wrap;

    li{
      flex:0 1 33%;
      box-sizing: border-box;
      max-width: 370px;
      padding:0 10px;
      margin-bottom:40px;

      img{
        width:100%;
        // height: 140px;
      }
      p.other{
        padding:3px 0;
        font-size:14px;
        color: #959595;
        font-weight:300;
        
      }

      p.name{
        padding:12px 0;
        font-size: 20px;
        color:#333333;
        font-weight:600;
      }
      p.view-more{
        padding-top:12px;
        font-weight:400;
        font-size:14px;
      }
      p.view-more:hover{
        color:#50bbdb;
      }
    }
  }
}

p{
  margin:0;
}
ul {
  list-style-type: none;
  // padding: 0;
}

  .paginate-wrapper{


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
        border:1px solid #ccc;
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
        padding:4px;
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


.celebrity{
  .paginate-wrapper{
    position: relative;
    text-align: center;
    margin-top:10px!important;
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
        padding:5px;
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
}
</style>
