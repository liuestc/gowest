<template>
  <div class="home-container">
	<div class="line-container">
		<div class="title">
			热门线路
		</div>

		<ul class="line-lists">
			<li>
				<img src="./img/12.png" alt="">
				<div class="p-container">
					<p class="list-title">最美西宁 </p>
					<p class="list-long">全长2000公里</p>
					<p class="list-step">
						长沙--重庆--成都--昆明--拉萨--西宁--西安--北京
					</p>

					<p class="list-days"><span >5</span>天</p>
					<p class="list-start">温江出发</p>
				</div>

			</li>


			<li>
				<img src="./img/12.png" alt="">
				<div class="p-container">
					<p class="list-title">最美西宁 </p>
					<p class="list-long">全长2000公里</p>
					<p class="list-step">
						长沙--重庆--成都--昆明--拉萨--西宁--西安--北京
					</p>

					<p class="list-days"><span >5</span>天</p>
					<p class="list-start">温江出发</p>
				</div>

			</li>


			<li>
				<img src="./img/12.png" alt="">
				<div class="p-container">
					<p class="list-title">最美西宁 </p>
					<p class="list-long">全长2000公里</p>
					<p class="list-step">
						长沙--重庆--成都--昆明--拉萨--西宁--西安--北京
					</p>

					<p class="list-days"><span >5</span>天</p>
					<p class="list-start">温江出发</p>
				</div>

			</li>								

		</ul>
	</div>

	<div class="vip-container">
		<div class="title">
			大咖   
		</div>

		<div class="vip-img">
			<img src="./img/avatar.png" alt="">
			<div class="vip-desc">
				<p class="vip-name">窃热</p>
				<p class="vip-line">
					入藏驾龄： 8年
				</p>
				<p class="vip-exp">参与路线：川藏线 青藏线</p>
			</div>

			<div class="vip-more">
				切热师傅是个极具感染力的人，他性格温和对人诚恳，总是竭尽全力的帮助身边的每个人，用自己的热情温暖旅客，谦虚、忠诚、微笑是很多客人对他的评价。切热师傅2从008年开始进藏，他把自己最美好的年华在西藏，川藏线、青藏线、滇藏线、墨脱、都留下他的脚印。跟随切热师傅游览西藏，你会有很多意外收获，他会带着你去领略西域最不可错过的美丽。
			</div>
		</div>
	</div>

	<div class="info-container">
		<div class="title">
			资讯
		</div>
		<div class="info-img">
			<img src="./img/m2.png" alt="">
		</div>
	</div>


	<div class="activity-container">
		<img src="./img/m3.png" alt="">

		<div class="activity-desc">
			<div class="title">
				活动
			</div>
			<p>
				彝族是一个崇拜火的民族，每年农历6月24日是彝族最热闹的节日——火把节。期间，凉山各地都将举办各种丰富多彩的活动，国内外游客相约来凉山“玩火”。今年的火把节比去年更早一些，活动主要在西昌、普格、昭觉、布拖4县市，活动包含美食、民俗...
			</p>
		</div>

	</div>



	<div class="inn-container">
		

		<div class="activity-desc">
			<div class="title">
				驿站
			</div>
			<p>
				彝族是一个崇拜火的民族，每年农历6月24日是彝族最热闹的节日——火把节。期间，凉山各地都将举办各种丰富多彩的活动，国内外游客相约来凉山“玩火”。今年的火把节比去年更早一些，活动主要在西昌、普格、昭觉、布拖4县市，活动包含美食、民俗...
			</p>

			<ul class='icon-list'>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<!-- <li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li> -->
			</ul>
		</div>

		<img src="./img/m4.png" alt="">

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
  padding:0;
  margin:0;
}
p{
	padding:0;
	margin:0;
}

.title{
	font-size:36px;
	color:#232323;
	margin-bottom:44px;
	margin-top: 44px;
}
.title::before{
	content:"|";
	display: inline-block;
	padding-right: 4px;
	width:2px;
	height:100%;
	background-color: rgba(80, 187, 219, 1);
	color:rgba(80, 187, 219, 1);
}

.home-container{
	width:64%;
	margin:0 auto;
	.line-container{
		
		margin:60px 0;

		.title{
			font-size:36px;
			color:#232323;
			margin-bottom:44px;
		}
		.title::before{
			content:"|";
			display: inline-block;
			padding-right: 4px;
			width:2px;
			height:100%;
			background-color: rgba(80, 187, 219, 1);
			color:rgba(80, 187, 219, 1);
		}
		.line-lists{
			display: flex;

			font-size: 14px;

			li{
				flex:0 1 32%;
				margin-right:44px;
				box-shadow: 1px 1px 2px 2px #ccc;
				padding-bottom:20px;

				img{
					width:100%;margin-bottom: 24px;
				}
				.p-container{
				
				padding:0 20px;

				.list-title{
					font-size: 24px;
					display: inline-block;
				}
				.list-long{
					display: inline-block;
					float:right;
					line-height: 24px;
					padding-top:5px;
				}

				.list-step{
					padding:24px 0;
					line-height: 21.97148px;
					letter-spacing: 0px;
					color: #959595;

				}
				.list-days{
					font-size:20px;
					display: inline-block;
					span{
						color: #50bbdb;
						display: inline-block;
						padding-right:1em;
					}
				}

				.list-start{
					float: right;
					display: inline-block;
					padding-top:4px;
				}
				}



			}
			li:last-child{
				padding-right:0;
				margin-right:0;
			}
		}

	}

	.vip-container{
		padding:0;
		margin:0;
		box-sizing: border-box;
		display: inline-block;
		width:49%;
		padding-right:20px;
		vertical-align: top;

		.vip-img{
			img{
				width:115px;
				display: inline-block;
				vertical-align: middle;
				margin-right:26px;
			}
		}

		.vip-desc{
			display: inline-block;
			vertical-align: middle;
			.vip-name{
				font-size: 20px;
				padding-bottom:10px; 
			}

			.vip-line,.vip-desc{
				padding:10px 0;
			}

		}
		.vip-more{
			font-size: 18px;
			padding-top:40px;
			color: #959595;
			text-align: justify;
			line-height: 1.5;
		}		

	}
	.info-container{
		paddin:0;
		margin:0;
		box-sizing: border-box;
		display: inline-block;
		width: 50%;
		padding-left: 20px;
		.info-img{
			img{
				width:100%;
				// vertical-align: middle;
			}
		}
	}
	.activity-container{
		margin-top:188px;
		img{
			display: inline-block;
			width: 49%;
			vertical-align: top;
		}
		.activity-desc{
			// flex:0 0 50%;
			box-sizing: border-box;;
			padding-left:40px;
			display: inline-block;
			width:50%;
			.title{
				margin-top:0;
			}

			color: #959595;
			line-height:1.5;
		}

	}
	.inn-container{
		margin-top:188px;
		img{
			display: inline-block;
			width: 49%;
			vertical-align: middle;
			box-sizing: border-box;
			padding-left: 40px;
		}
		.activity-desc{
			// flex:0 0 50%;
			box-sizing: border-box;;
			// padding-left:40px;
			display: inline-block;
			vertical-align: middle;
			width:50%;
			.title{
				margin-top:0;
			}
			.icon-list{
				li{
					display: inline-block;
					width:49%;
					margin:1em 0;
					color:#000;
					img{
						width:46px;
						padding-left:10px;
						vertical-align: middle;
					}
				}
			}

			color: #959595;
			line-height:1.5;
		}
	}

}

</style>
