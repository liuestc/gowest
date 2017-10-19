<template>
	<div class='header-container'>
		<div class="header-icon"><img src="../../assets/img/logo.png" alt=""></div>
		<ul>
			<li>首页</li>
			<li ><router-link to='/hot'>热门</router-link></li>
			<li class='active'><router-link to='/destination'>目的地</router-link></li>
			<li><router-link to='/line'>线路</router-link></li>
			<li><router-link to='/inn'>驿站</router-link></li>
			<li> <router-link to='/lineDetail'>大咖</router-link></li>
			<li>资讯</li>
			<li>更多</li>
		</ul>

		<div class='header-img'>
			<img src="../destination/img/destination-top.png" alt="">
		</div>
	</div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      msg: 'Welcome to destination'
    }
  }
}
</script>
<style lang='less'>
	.header-img{
		img{
			width:100%;
		}
	}

	// @media (min-width: 1000px) {
	//   .header-container {
	//     // display: none;
	//     ul{
	//     	margin-left: 40px;
	//     }
	//   }
	// }
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
				font-size:18px;
				color:#000;
				display: inline-block;
				width:90px;
				height:82px;
				line-height: 82px;
				text-align: center;
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