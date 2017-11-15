<template>
  <div class="about-container">
    <div class="about-content">
      <div class="about-content-img">
        <img src="./img/left1.png" alt="">
      </div>
      <div class="about-content-word">
        <p class="about-title">关于我们</p>
        <p class="about-des">
          成都西行起点自驾游网隶属于成都西行起点旅游资源开发有限公司，是一家从事西部自驾车旅游的专业公司，自公司成立以来致力于西部自驾车旅游的开发与服务，以悉心策划、全心服务、注重特色为理念，提供品质优良的全方位服务。我公司现已推出自驾产品十余款，拥有高素质的团队，并与西部地区多个俱乐部以及著名汽车论坛广为合作。 西部自由驾驭，畅途放飞自由心情！西行起点邀你一同出发！
        </p>
      </div>
    </div>

    <div class="about-content sec">
      <div class="about-content-img">
        <img src="./img/left1.png" alt="">
      </div>
      <div class="about-content-word">
        <p class="about-title">关于我们</p>
        <p class="about-des">
          成都西行起点自驾游网隶属于成都西行起点旅游资源开发有限公司，是一家从事西部自驾车旅游的专业公司，自公司成立以来致力于西部自驾车旅游的开发与服务，以悉心策划、全心服务、注重特色为理念，提供品质优良的全方位服务。我公司现已推出自驾产品十余款，拥有高素质的团队，并与西部地区多个俱乐部以及著名汽车论坛广为合作。 西部自由驾驭，畅途放飞自由心情！西行起点邀你一同出发！
        </p>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: ''
    }
  },
  mounted(){
    console.log(this.$route)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='less'>
  .about-container{
    padding-bottom:600px;
    width:66%;
    // margin-top:44px;
    margin:0 auto;
  }
  .about-content{
    display: flex;
    align-items:center;
    .about-content-img{
      flex:1;
      img{
        width:100%;
      }
    }
    .about-content-word{
      flex:1;
      box-sizing: border-box;
      padding:0 41px;
      .about-title{
        font-size:20px;
        font-weight: 600;
        margin-bottom:24px;
      }
      .about-des{
        font-size:16px;
        font-weight: 300;
        line-height: 1.5;
        color:#959595;
      }
    }
  }

  .about-content.sec{
    flex-direction:row-reverse;

    .about-content-word{
      padding:0;
      padding-right:24px;
      margin-right:24px;
    }
  }
</style>
