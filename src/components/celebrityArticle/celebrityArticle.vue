<template>
  <div class="info-detail">
      <div class='article-info'>
        <img :src="article.cover" alt="" class="cover">
        <div class="info-content"  tag='div' >
          <div class="info-time"><span class='month'>{{getTime(article.publishTime).m}}</span> <span class='day'>{{getTime(article.publishTime).d}}</span></div>
          <div class="info-summary">
            <p class="info-title">{{article.title}}</p>
            <p class='info-main'> {{article.summary}}</p>

            <p class="info-publisher">{{article.publisher}}</p>
          </div>



        </div>
      </div>

       <div v-html='article.content'  class='article-content'></div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      article:''
    }
  },
  created(){
    let id=this.$route.params.id;
    this.getInfoDetail(id)

  },
  methods:{
    getInfoDetail(id){
      axios.get("http://139.129.118.14:8082/WestBoundA/bigShot_getBigShotArticleById.json",{
        params:{
          bigShotArticleId:id
        }
      }).then((res)=>{
        console.log("article",res)
        this.article=res.data.article
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

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='less'>
.info-detail{
    width:60%;
    margin:0 auto;
    padding-bottom:600px;
    .article-info{
      // height:100%;
      margin-top:44px;
      height:800px;
      height:100%;
      img.cover{
        width:100%;
        max-height:400px;
      }

      .info-content{
        // overflow: hiden;
        margin-top:20px;
        display: flex;
        .info-time{
          flex: 80px;
          border:1px solid #000;
          broder-right:none;
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
          }
          .info-main{
            font-size:15px;
            color: #959595;
            line-height: 22px;
          }
          .info-publisher{
            margin-top:20px;
          }
        }
      }

    }
    .article-content{
      margin-top:60px;
      // width:100%;
      padding-left:100px;

      img{
        width:100%;
        max-height:263px;
      }
    }
}


</style>
