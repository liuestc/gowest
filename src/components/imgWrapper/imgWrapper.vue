<template>
	<div class='img-container'>
    <div>00000   IMGWRAPPER</div>
    <div v-for='item in lists'>
      <img src="item.imgUrl" alt="">

      <div class='word-wrapper'>
        <p class='img-title'>{{item.title}}</p>
        <p class="img-describe">
          {{item.more}}
        </p>
      </div>
    </div>
	</div>
</template>

<script>

// import MyHeader from '../header/Header'
export default {
  name: 'ImgWrapper',
  data () {
    return {
        flex: 4,
        lists:[
          {
            imgUrl:'./img/b1.png',
            title:"这里是一个title",
            word:"akjajkjskhfjmbsdhkjn,,ednksjdejkndejknemzhajkendkjajkajdjnx",
            more:"dkjfbjfbvulrhnfvidajnkcnkj.wshndissndfjv hendbc njkwaenjdzzdbdjkaebd"
          },
          {
            imgUrl:'./img/b2.png',
            title:"这里是一个title",
            word:"akjajkjskhfjmbsdhkjn,,ednksjdejkndejknemzhajkendkjajkajdjnx",
            more:"dkjfbjfbvulrhnfvidajnkcnkj.wshndissndfjv hendbc njkwaenjdzzdbdjkaebd"
          },
          {
            imgUrl:'./img/b3.png',
            title:"这里是一个title",
            word:"akjajkjskhfjmbsdhkjn,,ednksjdejkndejknemzhajkendkjajkajdjnx",
            more:"dkjfbjfbvulrhnfvidajnkcnkj.wshndissndfjv hendbc njkwaenjdzzdbdjkaebd"
          },
          {
            imgUrl:'./img/b1.png',
            title:"这里是一个title",
            word:"akjajkjskhfjmbsdhkjn,,ednksjdejkndejknemzhajkendkjajkajdjnx",
            more:"dkjfbjfbvulrhnfvidajnkcnkj.wshndissndfjv hendbc njkwaenjdzzdbdjkaebd"
          }
        ]
    }
  },
  props:{
    flex:{
      type:Number,
      default:4
    },
    lists:{
      Type:Object
      // default:
    },
    paddingLeft:{
      default:"20px",
      Type:"String"
    }
  },
  componemts:{
  	// MyHeader
  }
}
</script>
<style lang='less'>

</style>