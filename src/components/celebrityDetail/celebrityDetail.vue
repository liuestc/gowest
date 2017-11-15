<template>
  <div class='celebrity-detail'>
    <div class="celebrity-intro">
       <img :src="info.cover" alt="" class='bg-img' ref='imgCover' :style='{height:height+"px"}'>

      <div class="celebrity-wrappper">
        <img :src="info.headPortrait" alt="" class='head-img' ref='headImg' v-bind:style="{  height: clientHeight + 'px',width: clientHeight + 'px' }">
        <div class="celebrity-content">
          <div class="name">
            <span class='nickname'>{{info.name}}</span><span class='tag'>{{info.profession}}</span>
          </div>
          <p class="cele-describe">{{info.describe}}</p>
          <p class='skill'>技能：{{info.skill}}</p>
          <p class='skill-num'>文章：({{info.articleNum}})</p>
          <p class='skill-num'>行程：({{info.journeyNum}})</p>
          <!-- <p>{{info.skill}}</p>   -->
        </div>
      </div>

      <div class="article-list">
        <ul>
<!--           <router-link tag='li'  class='list-cover' v-for='item in article' :to='{name:"celebrityArticle",pramas:{id:item.id}}'><img :src="item.cover" alt=""></router-link> -->

        <div class="article-flex">
          <div class="flex-left">
            <router-link tag='div' :to='{name:"celebrityArticle",pramas:{id:article0.id}}'class="flex-left-four">
              <img :src="article0.cover" alt="">
            </router-link>
            <router-link tag='div' :to='{name:"celebrityArticle",pramas:{id:article1.id}}'class="flex-left-four">
              <img :src="article1.cover" alt="">
            </router-link>
            <router-link tag='div' :to='{name:"celebrityArticle",pramas:{id:article2.id}}'class="flex-left-four">
              <img :src="article2.cover" alt="">
            </router-link>
            <router-link tag='div' :to='{name:"celebrityArticle",pramas:{id:article3.id}}'class="flex-left-four">
              <img :src="article3.cover" alt="">
            </router-link>            
          </div>
          <router-link tag='div' :to='{name:"celebrityArticle",pramas:{id:article4.id}}' class="flex-right" >
            <img :src="article4.cover" alt="">
          </router-link>
        </div>


        <div class="article-flex fan">
          <div class="flex-left">
            <router-link tag='div' :to='{name:"celebrityArticle",pramas:{id:article5.id}}' class="flex-left-four" >
              <img :src="article5.cover" alt="" >
            </router-link>
            <div class="flex-left-four">
              <img src="http://139.129.118.14:8887/group1/M00/00/07/i4F2DloEWGaANJyRAAHTHDLHYKQ131.png" alt="">
            </div>
            <div class="flex-left-four">
              <img src="http://139.129.118.14:8887/group1/M00/00/07/i4F2DloEWGaANJyRAAHTHDLHYKQ131.png" alt="">
            </div>
            <div class="flex-left-four">
              <img src="http://139.129.118.14:8887/group1/M00/00/07/i4F2DloEWGaANJyRAAHTHDLHYKQ131.png" alt="">
            </div>            
          </div>
          <div class="flex-right">
             <img src="http://139.129.118.14:8887/group1/M00/00/07/i4F2DloEWGaANJyRAAHTHDLHYKQ131.png" alt="">
          </div>
        </div>        


        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios  from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      article:'',
      info:"",
      clientHeight:"",
      height:"",
      article0:"",
      article1:"",
      article2:"",
      article3:"",
      article4:"",
      article5:"",
      article6:"",
      article7:"",
      article8:"",
      article8:"",
    }
  },
  created(){
    let id=this.$route.params.id;
    console.log("artID",id)
    this.getArticle(id)

    axios.get("http://139.129.118.14:8082/WestBoundA/bigShot_getBigShotById.json",{
      params:{
        bigShotId:id
      }
    }).then((res)=>{
      console.log("jjjjjj",res.data)
      this.info=res.data.bigShot
      console.log("da ka",res.data)
    })
  },
  mounted(){
    let id=this.$route.params.id;
    console.log("artID",id)
    this.getArticle(id)    
  },
  methods:{
    getArticle(id){
      axios.get("http://139.129.118.14:8082/WestBoundA/bigShot_listBigShotArticle.json",{
        params:{
          bigShotId:id
        }
      }).then((res)=>{
        console.log("article",res.data.articles)

        // this.info=res.data.articles[0].bigShot
        console.log("info",this.info)

        this.article=res.data.articles

         this.article0=res.data.articles[0]?res.data.articles[0]:""

        // console.log("article0",article0)
         this.article1=res.data.articles[1]?res.data.articles[1]:""
         this.article2=res.data.articles[2]?res.data.articles[2]:""
         this.article3=res.data.articles[3]?res.data.articles[3]:""
        this.article4=res.data.articles[4]?res.data.articles[4]:""
        this.article5=res.data.articles[5]?res.data.articles[5]:""
        this.article6=res.data.articles[6]?res.data.articles[6]:""
        this.article7=res.data.articles[7]?res.data.articles[7]:""
        this.article8=res.data.articles[8]?res.data.articles[8]:""
        this.article9=res.data.articles[9]?res.data.articles[9]:""

      })
    }
  },
  mounted(){
    let height=this.$refs.imgCover.clientWidth/3
    console.log(height)
    this.height=height
      this.$nextTick(() => {
        const that = this;
        window.onresize = function temp() {

            that.height = that.$refs.imgCover.clientWidth/3
            // console.log("clientHeight",that.clientHeight)
        };
      })      
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='less'>

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
}

a {
  color: #42b983;
}

.celebrity-detail{
  width:60%;
  margin:0 auto;
  padding-bottom:600px;
  .celebrity-intro{
    margin-top:44px;
    .bg-img{
      width:100%;
      max-height:328px;
    }

    .celebrity-wrappper{
    position: relative;
    /* margin: 0 60px; */
    transform: translateY(-42%);
    width: 100%;
    box-sizing: border-box;
    border: 1px solid #ccc;
    padding-bottom: 22px;
    padding-left: 60px;
    border-top: none;
    border-radius: 4px;

      // position: relative;
      // // top:-170px;
      // margin:0 60px;
      // transform: translateY(-50%);
      .head-img{
        width:220px;
        height:220px;
        display: inline-block;
        margin-right:65px;

      }
      .celebrity-content{
        display: inline-block;
        .name{
          .nickname{
            font-size: 20px;
            color: #333333;
            display: inline-block;
            margin-right:16px;
            vertical-align: middle;
            font-weight:600;
          }
          .tag{
            display: inline-block;
            vertical-align: middle;
            background:rgba(80, 187, 219, 1);
            font-size: 14px;
            border-radius:20px;
            padding:4px 10px;
            text-align: center;
            color:#fff;
          }
        }
        p.skill{
          padding:2px 0;
          font-weight:500;
          font-size:14px;
          // color: #959595;
        }
        p.cele-describe{
          color:#959595;
          padding:10px 0;
          font-weight:300;
          max-width:400px;
          display: -webkit-box;
          -webkit-box-orient: vertical;
          -webkit-line-clamp: 2;
          overflow: hidden;
          line-height: 20px;
          padding-bottom: 0;          
        }

        p.skill-num{
          display: inline-block;
          font-weight:500;
          font-size:14px;
          padding-right:10px;
        }

      }
    }

    .article-list{
      margin-top:-100px;
      ul{
        display: flex;
        padding:0;
        margin-top:16px;
        flex-wrap:wrap;
        li.list-cover{
          flex:0 1 30%;
          margin-bottom:20px;
          img{
            // width:100%;
            width:200px;
            height:200px;

          }
        }
      }
    }
  }
}

@media(max-width:1060px){
  .celebrity-detail .celebrity-intro .celebrity-wrappper .head-img{
    width:180px;
    height:180px;
    margin-right:10px;
  }
  .celebrity-detail .celebrity-intro .celebrity-wrappper .celebrity-content .name .nickname{
    font-size:18px;
  }
  .celebrity-detail .celebrity-intro .celebrity-wrappper .celebrity-content p{
    font-size:12px;
  }
  .celebrity-detail .celebrity-intro .celebrity-wrappper .celebrity-content p.skill{
    padding:6px 0;
  }
  .celebrity-detail .celebrity-intro .celebrity-wrappper .celebrity-content .name .tag{
    font-size:12px;
  }
  .celebrity-detail .celebrity-intro .bg-img{
    height:250px;
  }

  .celebrity-detail .celebrity-intro .article-list ul li.list-cover img{
    width:180px;
    height:180px;
  }
}

@media(min-width:1300px){
  .celebrity-detail .celebrity-intro .article-list ul li.list-cover img{
    width:240px;
    height:240px;
  }
}


.article-flex{
  display: flex;
  .flex-left{
    flex:1;
    display: flex;
    flex-wrap:wrap;
    box-sizing: border-box;
    // padding-right:30px;
    .flex-left-four{
      flex:50%;
      box-sizing: border-box;
      padding:10px;
      img{
        width:100%;
        height:100%;
      }

    }
  }

  .flex-right{
    flex:1;
    padding:10px 0;
    padding-left:10px;
    box-sizing:border-box;

    img{
      // width:100%;
      height:100%;
    }
  }
}

.article-flex.fan{
  flex-direction:row-reverse;

  .flex-right{
    // padding:0;
    padding-right:10px;
  }

  .flex-left{
    padding-left:0;
    transform: translateX(-14px);
  }
}
</style>
