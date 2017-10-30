<template>
	<div class='destination-container'>
		<!-- 123 -->
		<!-- <img src="./img/destination-top.png" alt=""> -->
		<div class="destination-content">

			<div class="left-wrapper">
				<div class="destination-sort">
					<div class="title">目的地省属分类</div>
					<ul>
						<li>四川（4）</li>
						<li>四川（4）</li>
						<li>四川（4）</li>
						<li>四川（4）</li>
						<li>四川（4）</li>
						<li>四川（4）</li>
						<li>四川（4）</li>
						<li>四川（4）</li>
						<li>四川（4）</li>
						<li>四川（4）</li>

					</ul>
				</div>
				<div class="destination-tags">
					<div class="title">目的地标签</div>
					<ul>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
						<li>历史遗迹</li>
					</ul>	
				</div>
			</div>
			<div class="right-wrapper">
				<div class="destination-search"><input placeholder="Search" type="text"></div>

				
				<div class="destination-intro">
					<div class="destination-swiper">
						<swiper >
					        <swiper-slide class='swiper-container'><img src="./img/destination-top.png" alt=""></swiper-slide>
					        <swiper-slide class='swiper-container'><img src="./img/swiper2.png" alt=""></swiper-slide>
					        <swiper-slide class='swiper-container'><img src="./img/swiper2.png" alt=""></swiper-slide>

					      </swiper>
					</div>
					<div class="destination-words">
						<a class="destination-name"   href='/DestinationMore' target="view_window">西昌</a>


						<div class="destination-describe">
							<p>下火车那世界萨灰色空间玩， 客户在今年爱看法搜aLKali按时是。就是；在啊安徽的承诺啊按擦无敌模式阿萨
							额肯定是是是是是 世界黄金客是是是是户说来着是 色带芯积累</p>

							<p>下火车那世界萨灰色空间玩， 客户在今年三维数字接口吗额东方闪电vses'pkcx爱看法搜aLKali按时是。就是；在啊
								安徽的承诺啊按擦无敌模式阿萨
							额肯定是是是是是 世界黄金客是是是是户说来着是 色带芯积累</p>

							<p class='intro-little'><i><img src="./img/logo2.png" alt=""></i> 信息来自 <span class='where'>西昌旅游局</span> <span>3</span> -评论</p>
							<p class='intro-little'><i><img src="./img/logo2.png" alt=""></i> 信息来自 <span class='where'>西昌旅游局</span> <span>3</span> -评论</p>
						</div>
					</div>
				</div>


				<div class="destination-intro">
					<div class="destination-swiper">
						<swiper >
					        <swiper-slide class='swiper-container'><img src="./img/destination-top.png" alt=""></swiper-slide>
					        <swiper-slide class='swiper-container'><img src="./img/swiper2.png" alt=""></swiper-slide>
					        <swiper-slide class='swiper-container'><img src="./img/swiper2.png" alt=""></swiper-slide>

					      </swiper>
					</div>
					<div class="destination-words">
						<div class="destination-name">西昌</div>
						<div class="destination-describe">
							<p>火把节是彝族、白族、纳西族、基诺族、拉祜族等民族的古老传统节日，有着深厚的民俗文化内涵，被称为“东方的狂欢节”。
							不同的民族举行火把节的时间也不同，大多是在农历的六月二十四，主要活动有斗牛、斗羊、斗鸡、赛马、摔跤、歌舞表演、选美等。</p>

							<p>火把节是彝族、白族、纳西族、基诺族、拉祜族等民族的古老传统节日，有着深厚的民俗文化内涵，被称为“东方的狂欢节”。
							不同的民族举行火把节的时间也不同，大多是在农历的六月二十四，主要活动有斗牛、斗羊、斗鸡、赛马、摔跤、歌舞表演、选美等。</p>
						</div>
					</div>
				</div>

				<div class="destination-intro">
					<div class="destination-swiper">
						<swiper >
					        <swiper-slide class='swiper-container'><img src="./img/destination-top.png" alt=""></swiper-slide>
					        <swiper-slide class='swiper-container'><img src="./img/swiper2.png" alt=""></swiper-slide>
					        <swiper-slide class='swiper-container'><img src="./img/swiper2.png" alt=""></swiper-slide>

					      </swiper>
					</div>
					<div class="destination-words">
						<div class="destination-name">西昌</div>
						<div class="destination-describe">
							<p>下火车那世界萨灰色空间玩， 客户在今年爱看法搜aLKali按时是。就是；在啊安徽的承诺啊按擦无敌模式阿萨
							额肯定是是是是是 世界黄金客是是是是户说来着是 色带芯积累</p>

							<p>下火车那世界萨灰色空间玩， 客户在今年三维数字接口吗额东方闪电vses'pkcx爱看法搜aLKali按时是。就是；在啊
								安徽的承诺啊按擦无敌模式阿萨
							额肯定是是是是是 世界黄金客是是是是户说来着是 色带芯积累</p>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import axios from 'axios'

import 'swiper/dist/css/swiper.css'

import Vue from 'vue'

import VueRouter from 'vue-router'

import VueAwesomeSwiper from 'vue-awesome-swiper'

import DestinationMore from '../destination-more/destinationMore'

import ImgWrapper from '../imgWrapper/imgWrapper'

Vue.use(VueAwesomeSwiper)
Vue.use(VueRouter)


const routes=[
  {path:'/destinationMore',component:DestinationMore}
]

const router=new VueRouter({
  routes
})

import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  name: 'destination',
  data () {
    return {
      msg: 'Welcome to destination'
    }
  },
  created (){
  	// axios.get('139.129.118.14:8082/destination_listDestinationByAddress.json').then(function(res){
  	// 	console.log(res)
  	// })
  	axios.get('http://139.129.118.14:8082/WestBoundA/destination_listDestinationByAddress.json?addressId=1').then((res)=>{
  		console.log(res)
  	}).catch(err=>{
  		console.log(err)
  	})

  },
  router,
  components: {
    swiper,
    swiperSlide,
    DestinationMore,
    ImgWrapper
  }
}
</script>
<style lang='less'>

ul,li{
	list-style:none;
}
.destination-container{
	img{
		height:275px;
		width:100%;
	}
	.destination-content{
		.left-wrapper{
			padding-left:100px;
			float:left;
			width:320px;
			font-size:14px;
			.destination-sort,.destination-tags{
				padding-top:80px;

				.title{
					font-size:18px;
					font-weight:800;
					margin-bottom:20px;
				}
				ul{
					padding:0;
					margin:0;
					margin-left:-12px;

					li{
						font-size: 12px;
						display: inline-block;
						margin-right:10px;
						color:#707070;
						text-align: center;
						margin-bottom: 6px;
						padding:6px 12px;
					}

				}
			}
			.destination-tags{
				ul{
					li{
						border:1px solid rgba(149, 149, 149, 1);
					}
				}
			}
		}
		.right-wrapper{
			float:right;
			width:100%;
			margin-left:-420px;
			.destination-search{
				// margin-top:44px;
				// margin-left: 520px;
    			padding-right: 220px;
    			margin:44px 0 40px 520px;
				// width:100%;
				input{
					height:50px;
					line-height: 50px;
					width:100%;
					padding-left:16px;
				}

			}

			.destination-intro{
				margin-left:520px;
				padding-right: 200px;
				max-width: 770px;
    			min-width: 480px;
    			margin-bottom:50px;
    			font-size: 16px;
				.destination-swiper{
					// width:770px;
					height:336px;
					.swiper-container{
						// width:770px;
						height:336px;
						img{
							widh:100%;
							// height:100%;
						}
					}
				}
				.destination-words{
					.destination-name{
						// display: inline-block;
						float:left;
						font-size: 24px;
						color:#221815;
						padding:0 42px 0 10px;
					}
					.destination-describe{
						// display: inline-block;
						overflow: hidden;

						p{
							line-height: 22px;							
							text-align:justify;
							color:#959595;
							padding-top:0;
							margin:0;
							padding-bottom: 1em;	

							.where{
								color:#444;	
							}

							i{
								img{
									width:10px;
									height:10px;
								}
							}						
						}

						p.intro-little{
							display: inline-block;
							padding-right:40px;
						}
					}
				}
			}
		}
	}
}
	
</style>