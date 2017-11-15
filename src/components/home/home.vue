<template>
  <div class="home-container">
	<div class="line-cotainer-home">
		<div class="title">
			线路
		</div>

		<ul class="line-lists" ref='imgauto'>
			<li v-for='item in routers' >
				<img :src="item.cover" alt=""  id='lines-img' v-bind:style="{  height: clientHeight + 'px' }">
				<router-link class="p-container" :to='{name:"lineDetail",params:{id:item.id}}'  tag='div'>
					<p class="list-title">{{item.name}} </p>
					<p class="list-long">全长<span class='list-long-content'>{{item.mileage}}</span>公里</p>
					<p class="list-step">
						{{item.middlePoint}}
					</p>
					
					<div class="list-days-wrapper">
						<p class="list-days"><span >{{item.dayNum}}</span>天</p>
						<p class="list-start">{{item.origin}} 出发&nbsp;></p>						
					</div>

				</router-link>

			</li>	

		</ul>
	</div>

	<div class="vip-container">
		<div class="title">
			大咖   
		</div>

		<router-link class="vip-img" tag='div' :to='{name:"celebrityDetail",params:{id:celebrity.id}}' >
			<img :src="celebrity.headPortrait" alt="">
			<div class="vip-desc">
				<p class="vip-name">{{celebrity.name}}</p>
				<p class="vip-line">
					驾龄： {{celebrity.journeyNum?celebrity.journeyNum:10}}年
				</p>
				<p class="vip-exp">技能：{{celebrity.profession}}</p>
			</div>

			<div class="vip-more">
				{{celebrity.describe}}
			</div>
		</router-link>
	</div>

	<div class="info-container2">
		<div class="title">
			资讯
		</div>
		<router-link class="info-img" tag='div'  :to='{name:"infoDetail",params:{id:news.id}}'>
			<img :src="news.cover" alt="">
		</router-link>
	</div>


	<div class="activity-container">
		<img :src="activity.cover" alt="">

		<div class="activity-desc">
			<div class="title hd">
				活动
			</div>
			<p class='activity-desc-content'>
				{{activity.describe}}
			</p>
			<!-- <p class='view'> READ&nbsp;MORE</p> -->
		</div>

	</div>



	<div class="inn-container2">
		

		<div class="activity-desc">
			<div class="title hd">
				驿站
			</div>
			<p class='inn-desc-content'>
				彝族是一个崇拜火的民族，每年农历6月24日是彝族最热闹的节日——火把节。期间，凉山各地都将举办各种丰富多彩的活动，国内外游客相约来凉山“玩火”。今年的火把节比去年更早一些，活动主要在西昌、普格、昭觉、布拖4县市，活动包含美食、民俗...
			</p>

			<ul class='icon-list'>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
				<li><img src="./img/1.png" alt=""> <span>餐饮娱乐</span></li>
			</ul>
		</div>

		<img src="./img/m4.png" alt="">
	</div>	




  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
export default {
  name: 'Home',
  components: {

  },
  data(){
  	return {
  		routers:{},
  		celebrity:"",
  		activity:"",
  		news:"",
  		clientHeight:""
  	}
  },

  created(){
  	this.getData()
  },
  mounted(){
  	
	console.log("图片",this.$refs.imgauto.clientWidth)
  	this.$nextTick(() => {
  		console.log(document.getElementById("lines-img"))
	 	// this.clientWidth= `${document.querySelector(".lines-img").clientWidth}px`;
	 	// console.log(this.clientWidth)
	 	this.clientHeight = (this.$refs.imgauto.clientWidth*.9)/(3*1.6);
	    const that = this;
	    window.onresize = function temp() {
	        that.clientHeight = (that.$refs.imgauto.clientWidth*.9)/(3*1.6);
	    };
    })
  },
  methods:{
  	getData(){
  		axios("http://139.129.118.14:8082/WestBoundA/getContentForHomePage.json").then((res)=>{
  			console.log(res.data)
  			this.routers=res.data.routes.slice(0,3)
  			this.activity=res.data.activity[0]
  			this.celebrity=res.data.bigShots[0]
  			this.news=res.data.news[0]
  		})
  	}
  }
}
</script>

<style lang='less'>
a{
  text-decoration:none;
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
	font-size:30px;
	color:#232323;
	margin-bottom:30px;
	// margin-top: 44px;
	font-weight: 600;
	position: relative;
}

.title::before{
	content:"  ";
	position: absolute;
	top:4px;
	display: inline-block;
	padding-right: 6px;
	width:2px;
	height:32px;
	left:-18px;
	background-color: rgba(80, 187, 219, 1);
	color:#fff;
}

.hd::before{
	top:8px;
}


// @media (max-width: 800px) {
// 	.home-container .line-cotainer-home .line-lists li img{
// 		height:80px !important;
// 	}
// }

// @media (max-width: 1200px) {
// 	.home-container .line-cotainer-home .line-lists li img{
// 		height:100px !important;
// 	}
// }

// @media (min-width: 1400px) {
// 	.home-container .line-cotainer-home .line-lists li img{
// 		min-height:210px !important;
// 	}
// }

.home-container{
	width:64%;
	margin:0 auto;
	padding-bottom:500px;
	.line-cotainer-home{
		
		margin:60px 0;
		.line-lists{
			display: flex;
			flex-wrap:wrap;

			font-size: 14px;
			// justify-content:center;

			li:hover{
				box-shadow: 0px 5px 11.6px 1.4px rgba(4, 0, 0, 0.05);
			}

			li{
				flex:0 1 32%;
				position: relative;
				box-sizing: border-box;
				margin-right:2%;
				// box-shadow: 0px 5px 11.6px 1.4px rgba(4, 0, 0, 0.05);
				padding-bottom:20px;
				margin-bottom:50px;

				img{
					width:100%;
					margin-bottom: 16px;
					// height:144px;
					// max-height:250px;
				}
				.p-container{
				
				padding:0 20px;
				// position: absolute;
				// bottom:0;

				.list-title{
					font-weight:800;
					font-size: 22px;
					display: inline-block;
				}
				.list-long{
					display: inline-block;
					float:right;
					line-height: 24px;
					padding-top:5px;
					.list-long-content{
						color: #50bbdb;
					}
				}

				.list-step{
					padding:16px 0 16px 0;
					line-height: 22px;
					letter-spacing: 0px;
					color: #959595;
					margin-bottom:50px;
					font-weight:300;

				}

				.list-days-wrapper{
					width:80%;
					position: absolute;
					bottom:0;
					margin-bottom:24px;
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
						// font-family: ﻿SourceHanSansCN-Regular;
						float: right;
						display: inline-block;
						padding-top:4px;
					}
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
				height:115px;
				display: inline-block;
				vertical-align: middle;
				margin-right:26px;
				border-radius:50%;
			}
		}

		.vip-desc{
			display: inline-block;
			vertical-align: middle;
			.vip-name{
				font-size: 20px;
				padding-bottom:10px; 
			}

			.vip-line,.vip-exp{
				padding:2px 0;
				color: #959595;
				font-weight:300;
			}

		}
		.vip-more{
			font-size: 18px;
			padding-top:40px;
			color: #959595;
			text-align: justify;
			line-height: 1.5;
			font-weight:300;
		}		

	}
	.info-container2{
		paddin:0;
		margin:0;
		box-sizing: border-box;
		display: inline-block;
		width: 50%;
		padding-left: 20px;
		.info-img{
			img{
				width:100%;
				max-height:240px;
				// vertical-align: middle;
			}
		}
	}
	.activity-container{
		margin-top:120px;
		img{
			display: inline-block;
			width: 49%;
			vertical-align: top;
			max-height:240px;
		}
		.activity-desc{
			// flex:0 0 50%;
			box-sizing: border-box;;
			padding-left:40px;
			display: inline-block;
			width:50%;
			// .title{
			// 	margin-top:0;
			// }



			color: #959595;
			line-height:1.5;
		}

	}
	.inn-container2{
		margin-top:120px;
		img{
			display: inline-block;
			width: 49%;
			vertical-align: middle;
			box-sizing: border-box;
			padding-left: 40px;
			padding-top:16px;
		}
		.activity-desc{
			// flex:0 0 50%;
			box-sizing: border-box;;
			// padding-left:40px;
			display: inline-block;
			vertical-align: middle;
			width:50%;
			// .title{
			// 	margin-top:0;
			// }
			.icon-list{
				li{
					display: inline-block;
					width:49%;
					margin:6px 0;
					color:#000;
					img{
						width:46px;
						padding-left:10px;
						vertical-align: middle;
						margin-right:16px;
					}
				}
			}

			color: #959595;
			line-height:1.5;
		}
	}

}


// p.list-step{position: relative;  max-height: 77px;overflow: hidden; width:100%}
// p.list-step::after{content: "..."; position: absolute; bottom: 0; right: 0;
// background: -webkit-linear-gradient(left, transparent, #fff 55%);
// background: -o-linear-gradient(right, transparent, #fff 55%);
// background: -moz-linear-gradient(right, transparent, #fff 55%);
// background: linear-gradient(to right, transparent, #fff 55%);
// }


.activity-desc-content,.inn-desc-content{
	font-weight:300;
	margin-bottom:20px;
}

.view{
	display: inline-block;
    font-size: 12px;
    padding: 6px 12px;
	border:1px solid #232323;
	color: #232323;
}
</style>
