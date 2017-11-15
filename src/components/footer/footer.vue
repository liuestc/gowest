<template>
  <div class="foot-container">
    <div class="connect-us">  
      <img src="./img/email.jpg" alt="">
      <div class='connect-word'>联系我们</div>
      <div class="connect-num"><input type="text" placeholder="请输入你的账号"></div>
      <div class="connect-login">登录</div>
      <div class="connect-icon">
        <ul class='fuck'>
          <!-- <li><img src="./img/loc.png" alt=""></li> -->
          <li><img src="./img/list1.png" alt=""></li>
          <li><img src="./img/list2.png" alt=""></li>
          <li><img src="./img/list3.png" alt=""></li>
<!--           <li><img src="./img/list4.png" alt=""></li>
          <li><img src="./img/list5.png" alt=""></li> -->
<!--           <li><img src="./img/loc.png" alt=""></li>
          <li><img src="./img/loc.png" alt=""></li> -->

        </ul>
      </div>
    </div>
  <div class="wrapper">
    <div class="foot-content">
      <div class="xx-img">
        <img src="./img/logo.jpg" alt="">
      </div>

      <ul class='icon-list'>
        <li>
          <img src="./img/mail.png" alt="">
          <p>成都市温江区光华</p>
        </li>
        <li>
          <img src="./img/tel.png" alt="">
          <p>86-028-888-8898</p>
        </li>

        <li>
          <img src="./img/loc.png" alt="">
          <p>xidian@thotel.com</p>
        </li>  
      </ul>

      <ul>
        <li class='foot-title'>集团服务</li>
        <li>文化产业</li>
        <li>电商服务</li>
      </ul>

      <ul>
        <li class='foot-title'>关于我们</li>
        <li>关于我们</li>
        <li>人才招聘</li>
      </ul>


      <ul>
        <li class='foot-title'>商务合作</li>
        <li>商务合作</li>
        <li>项目招商</li>
      </ul>
    </div>      
    </div>

    <div class="copy-right">
      © 2017 The Xi Xing Qi Dian. All rights reserved.
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style lang='less'>
ul,li{
  padding:0;
  margin:0;
}
.wrapper{
  background: #232323;
}
.foot-container{
  position: absolute;

  bottom:0;
  // height:358px;
  background-color: rgba(46, 46, 46, 1);
  width:100%;
  margin:0 auto;
  .connect-us{
    width:66%;
    margin:0 auto;
    // height:82px;
    padding:16px 0;

    div{
      display: inline-block;
    }
    img{
      width:30px;
      display: inline-block;
      vertical-align: middle;
      margin-right:16px;
    }
    .connect-word{
      // display: inline-block;
      font-size:20px;
      color:#fff;
      vertical-align: middle;
      margin-right:109px;

    }

    .connect-num{
      // border-left:1px solid #fff;
      padding-left:15px;
      margin-left:-14px;
       input{
        background:rgba(46, 46, 46, 1);
        color:#fff;
        padding-left:15px;
        height:34px;
        line-height: 34px;
        display: inline-block;
        // border-left:none;
        // border-top:none;
      }
    }

    .connect-login{
    font-size:18px;
     padding:8px 50px;
     background-color: rgba(80, 187, 219, 1);
     margin-left:14px;
     color:#fff;
    }

    .connect-icon{
      margin-left:60px;
      ul.fuck{
        li{
          display: inline-block;
          img{
            width:32px;
            // height:22px;
          }
        }
      }
    } 
  }
  .foot-content{
    width:66%;

    margin:0 auto;
    // padding-left: 17%;
    // padding-right: 17%;
    display: flex;
    align-items:center;
    justify-content:center;
    padding:45px 0 60px 0;

    .xx-img{
        flex:120px;
    }
    ul{
      flex:1;
      color: #acacac;
      // align-items: center;
      font-size:14px;

        align-items:center;
        justify-content:center;

      li{
        padding:12px 0;
        text-align: center;
        display: block;
      }

      li.foot-title{
          color:#fff;
          font-size:15px;
        
      }
    }

    ul.icon-list{
      
      li{
          text-align: left;
      }
      img{
        display: inline-block;
        width:20px;
        height:20px;
        vertical-align: middle;

      }
      p{
        display: inline-block;
        vertical-align: middle;
      }
    }
  }
}

.copy-right{
  background: #101010;
  text-align: center;
  color: #acacac;
  font-size:14px;
  height:60px;
  line-height: 60px;
}

.connect-us-wrapper{
  border:1px solid rgba(80, 187, 219, 1);
  border-radius:50%;
}

@media(max-width:1350px){
.foot-container .foot-content{
  width:80%!important;
}
}
</style>
