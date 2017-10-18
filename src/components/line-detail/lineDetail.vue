<template>
  <div class="line2-container">
    <div class="day-list">
      <ul>
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

                <p class="line2-btn">查看详情</p>
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
        </li>


      </ul>
    </div>
  </div>
</template>

<script>


export default {
  name: 'LineDetail',
  // router,
  components: {



  }
}
</script>

<style lang='less'>
a{
  text-decoration:none;
  /*color:#000;*/
}

ul,li{
  list-style: none;
  padding:0;
  margin:0;
}
.line2-container{
  width:60%;
  margin:0 auto;

  .day-list{
    ul{
      li.day-step{
         margin-top:60px;
        .day-wrapper{
          display: flex;
          position: relative;
          margin-top:60px;



          img{
            // position: absolute;
            flex:1;
            // bottom:0;


          }
          .day-content{
            flex:2;
            padding:40px 60px;
            box-shadow:1px 1px 1px 2px #ccc;
            margin-left:40px;
            margin-top:-100px;
            z-index: 100;
            background: #fff;

            .day-title{
              color:#000;
              font-size:30px;
            }

            p{
              font-size:18px;
              color: #959595;
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
    }
  }
}
</style>
