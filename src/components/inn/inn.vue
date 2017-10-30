<template>
  <div class="inn-container">
    <div class="more-specialty">
      <!-- <div class="more-food-title">当地美食  <span class='food-en'>Local Delicacy   </span></div> -->

      <div class="food-content">

        <ul class="food-lists">
          <li class='list'>
            <img src="./img/01.png" alt="">
            <p class="list-name"> 成都假日花园酒店 </p>
            <p class="specialty-desc">
              停车场
            </p> 
            <p class="specialty-desc">活动优惠</p>
            <p class="specialty-desc">洗浴保健</p> 
             <p class="specialty-desc">洗浴保健</p> 
            
                     

            <div class="price-container">
              <p class="inn-price">价格 ： 199￥</p>
              <p class="line-detail"><router-link to='/innDetail'>查看详情</router-link></p> 
            </div>
          </li>
          <li class='list'>
            <img src="./img/02.png" alt="">
            <p class="list-name"> 成都假日花园酒店 </p>
            <p class="specialty-desc">
              停车场
            </p> 
            <p class="specialty-desc">活动优惠</p>
            <p class="specialty-desc">洗浴保健</p> 
             <p class="specialty-desc">洗浴保健</p> 
            
                     

            <div class="price-container">
              <p class="inn-price">价格 ： 199￥</p>
              <p class="line-detail">查看详情</p> 
            </div>


          </li>
          <li class='list'>
            <img src="./img/03.png" alt="">
            <!-- <p class="list-name">   好吃的  </p> -->
            <p class="list-name"> 成都假日花园酒店 </p>
            <p class="specialty-desc">
              停车场
            </p> 
            <p class="specialty-desc">活动优惠</p>
            <p class="specialty-desc">洗浴保健</p> 
             <p class="specialty-desc">洗浴保健</p> 
            <div class="price-container">
              <p class="inn-price">价格 ： 199￥</p>
              <p class="line-detail">查看详情</p> 
            </div>        
          </li>                             
        </ul>
      </div>
    </div>
  </div>
</template>

<script>


// import ImgWrapper from './components/ImgWrapper/imgWrapper'


export default {
  name: 'Inn',
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
}

.inn-container{
  width:60%;
  margin:0 auto;
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
        
          li.list{
            img{
              width:100%;
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
            }
            p.specialty-desc{
              width:49%;
              text-align: center; 
              display: inline-block;
              font-size: 16px;
              font-weight: normal;
              font-style: normal;
              font-stretch: normal;
              // line-height: 30px;
              letter-spacing: 0px;
              color: #959595; 
              // padding:0 40px;
              text-align: left;
              padding:0;
              padding-top:10px; 
              margin:0;          
            }
            p.specialty-desc::before{
              content:"·";
              display:inline-block;
              padding-right:20px;
              vertical-align: middle;
            }

            .price-container{
              display: block;
              padding:10px;
              margin:20px 0;
              border-top:1px solid #ccc;
              border-bottom:1px solid #ccc;
              .inn-price{
                text-align: left;
                font-size: 14px;
                display: inline-block;
                width:49%;
              }

              .line-detail{
                border:1px solid rgba(80, 187, 219, 1);
                padding:4px 10px;
                display: inline-block;
                // margin-top:20px;
                color:#fff;
                display: inline-block;
                // width:48%;
                text-align: right;
                background: rgba(80, 187, 219, 1);
              }
            }

          }
        
      }
    } 
  } 
}
</style>
