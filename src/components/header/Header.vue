<template>
	<div class='header-container'>
		<div class="header-icon"><img src="../../assets/img/logo.png" alt=""></div>
		<ul>
			<li>首页</li>
			<li>热门</li>
			<li class='active'><router-link to='/destination'>目的地</router-link></li>
			<li><router-link to='/destinationMore'>线路</router-link></li>
			<li>驿站</li>
			<li>大咖</li>
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