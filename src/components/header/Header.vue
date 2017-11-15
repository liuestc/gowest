<template>
	<div class='header-container'>
		<div class="header-icon"><img src="../../assets/img/logo.png" alt=""></div>
		<ul  >
			<router-link tag="li"  to='/home' active-class='active'>首页</router-link>
			<router-link tag="li"  to='/hot' active-class='active'>热门</router-link>
			<router-link tag="li" to='/destination' active-class='active'>目的地</router-link>
			<router-link tag="li" to='/line' active-class='active'>线路</router-link>
			<router-link tag="li" to='/inn' active-class='active'>驿站</router-link>
			<router-link tag="li" to='/celebrity' active-class='active'>大咖</router-link>
			<router-link tag="li" to='/info' active-class='active'>资讯</router-link>
			<!-- <router-link to='/test'> 更多</router-link> -->
		</ul>

		<div class='header-img'>
			<img :src="img">
		</div>
		<!-- {{img}} -->
	</div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      msg: 'Welcome to destination',
      img0:"/static/home.jpg"
      // img:""
    }
  },
  props:{
  	img:{
  		type:String,
  		default:'/static/remen.png'

  	}
  },
  methods:{
  	togActive($event){
  		// console.log($event)

  	},
  	togImg(e){
  		console.log("e",e)
  	}
  },
  created(){
	console.log("是否加载0000")
	let path=this.$route.path

	switch (path){
	case '/home':
	this.img0='/static/home.jpg'
	break;

	case '/hot':
	this.img0='/static/remen.png'
	break;

	case '/destination':
	this.img0='/static/des.png'
	break;

	case '/line':
	this.img0='/static/line.png'
	break;


	case '/inn':
	this.img0='/static/yizhan.png'
	break;

	case '/celebrity':
	this.img0='/static/daka.png'
	break;

	case '/info':
	this.img0='/static/line.png'
	break;

	case '/about':
	this.img0='/static/des.png'
	break;

}

  },
  mounted(){
  	console.log("是否加载header")
  },
	watch:{
		"$route"(to,from){
			console.log("我是否执行",to.path)
			let path=to.path
			switch (path){
				case '/home':
				this.img0='/static/home.jpg'
				break;

				case '/hot':
				this.img0='/static/remen.png'
				break;

				case '/destination':
				this.img0='/static/des.png'
				break;

				case '/line':
				this.img0='/static/line.png'
				break;


				case '/inn':
				this.img0='/static/yizhan.png'
				break;

				case '/celebrity':
				this.img0='/static/daka.png'
				break;

				case '/info':
				this.img0='/static/line.png'
				break;

				case '/about':
				this.img0='/static/des.png'
				break;

			}
		}
	}

}
</script>
<style lang='less'>
	.active{
    	background: rgb(80,187,219);
    	color:#fff;
    	font-weight:400!important;
    }
	.header-img{
		img{
			width:100%;
			// height
		}
	}

	@media (max-width: 1200px) {
	  .header-container 
	    ul{
	    	margin-left: 40px!important;
	    }
	  
	}
	.header-container{
		position:relative;
		width:100%;
		text-align: center;
		min-width: 1200px;
		


		.header-icon{
			display: inline-block;
			vertical-align: middle;
			height:32px;
		}

		ul{ 
			margin:0;
			padding:0;
			margin-left:300px;
			display: inline-block;

			li{
				font-size:15px;
				color:#000;
				display: inline-block;
				width:90px;
				height:68px;
				line-height: 68px;
				text-align: center;
				font-weight: 300;
				&>a{
					// background: rgb(80,187,219);
			    	// color:#fff;
				}

			}
			li.active{
		    	background: rgb(80,187,219);
		    	color:#fff;
		    }
		}
	}
</style>