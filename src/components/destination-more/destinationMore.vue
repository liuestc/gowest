<template>
	<div class='more-container'>
		<div class='more-name'>{{name}}</div>

		<div class='more-feature'>
			<ul>
				<li>

					<div class='more-imgWrapper'>						
						<img src="./img/icon-dqqh.png" alt="">
					</div>
					

					<div class='more-words'>
						<div class="more-title">地区气候</div>
						<p class="more-describe">
							{{climate}}
						</p>
					</div>
				</li>

				<li>
					<div class="more-imgWrapper">
						<img src="./img/icon-lswh.png" alt="">
					</div>

					<div class='more-words'>
						<div class="more-title">历史文化</div>
						<p class="more-describe">
							{{historyAndCulture}}
							
						</p>
					</div>
				</li>
				<li>
					<div class="more-imgWrapper">
						<img src="./img/icon-zjlyj.png" alt="">
					</div>

					<div class='more-words'>
						<div class="more-title">地区生态</div>
						<p class="more-describe">
							
							{{ecology}}
						</p>
					</div>
				</li>
				<li>

					<div class="more-imgWrapper">
						<img src="./img/icon-zrst.png" alt="">
					</div>
					

					<div class='more-words'>
						<div class="more-title">最佳季节</div>
						<p class="more-describe">
							{{touristSeason}}
						</p>
					</div>
				</li>				
			</ul>
		</div>

		<div class="more-food">
			<div class="more-food-title">当地美食  <span class='food-en'>Local Delicacy   </span></div>

			<div class="food-content">
				<div class="food-active">
					<img :src="activeFood.cover" alt="" ref='imgActive' :style='{height:height+"px"}'>
					<div class="food-info">
						<div class="food-name">{{activeFood.name}}</div>
						<div class="food-describe">{{activeFood.describe}}</div>
					</div>
				</div>

				<ul class="food-lists">
					<li class='list'  v-for='item in food'  v-on:click='foodActive(item)'>
						<img :src="item.cover" alt="">
						<p class="list-name"> {{item.name}} </p>
					</li>																
				</ul>
			</div>
		</div>

		<div class="more-specialty">
			<div class="more-food-title">当地特色  <span class='food-en'>Local Featrue  </span></div>

			<div class="food-content">

				<ul class="food-lists" ref=''>
					<li class='list' v-for='item in specialty'>
						<img :src="item.cover" alt="">
						<p class="list-name"> {{item.name}}</p>
						<p class="specialty-desc">
							{{item.describe}}
						</p>						
					</li>
<!-- 					<li class="list"><img src="./img/c1.png" alt=""> <p class="list-name"> test</p> <p class="specialty-desc">
							好吃的
						</p></li>	

					<li class="list"><img src="./img/c1.png" alt=""> <p class="list-name"> test</p> <p class="specialty-desc">
							好吃的好吃的好吃的好吃的好吃的好吃的好吃的好吃的好吃的好吃的好吃的好吃的好吃的

					</p></li>	 -->					
<!-- 					<li class='list'>
						<img src="./img/c2.png" alt="">
						<p class="list-name">  卤肉   </p>
						<p class="specialty-desc">
							豆瓣是烹制正宗川菜的主要辅料之一,郫县豆瓣的生产已有一百多年的历史，
							其特色是味辣、香酥、色红，用以炒菜，分外提色增香，被誉为“川菜的灵魂”。
						</p>


					</li>
					<li class='list'>
						<img src="./img/c3.png" alt="">
						<p class="list-name">   好吃的  </p>
						<p class="specialty-desc">
							豆瓣是烹制正宗川菜的主要辅料之一,郫县豆瓣的生产已有一百多年的历史，
							其特色是味辣、香酥、色红，用以炒菜，分外提色增香，被誉为“川菜的灵魂”。
						</p>						
					</li>
					<li class='list'>
						<img src="./img/c4.png" alt="">
						<p class="list-name">  好吃的   </p>
					</li>
					<li class='list'>
						<img src="./img/c5.png" alt="">
						<p class="list-name">  好吃的   </p>
						<p class="specialty-desc">
							豆瓣是烹制正宗川菜的主要辅料之一,郫县豆瓣的生产已有一百多年的历史，
							其特色是味辣、香酥、色红，用以炒菜，分外提色增香，被誉为“川菜的灵魂”。
						</p>							
					</li> -->																
				</ul>
			</div>
		</div>


   		<div class="more-entertainment">
			<div class="more-food-title">当地活动  <span class='food-en'>Local Active  </span></div>

			<div class="entertainment-lists">
				<ul>
					<li v-for='item in active'>
						<img :src="item.cover" alt="">
						<div class="entertainment-content">
							<div class="entertainment-title">{{item.name}}</div>
							<div class="entertainment-desc">{{item.describe}}
							</div>
						</div>
					</li>
<!-- 
					<li>
						<img src="./img/f1.png" alt="">
						<div class="entertainment-content">
							<div class="entertainment-title">川剧</div>
							<div class="entertainment-desc">
								到四川一定要看川剧，感受川剧的幽默和泼辣。早在唐代就有“蜀戏冠天下”的说法。清代乾隆时，在本地车灯戏基础上，融汇各地声腔，形成了含有高腔、胡琴、昆腔、灯戏、弹戏五种声腔的用四川话演唱的“川剧”。什么时候到，随时都可以上桌吃饭。
							</div>
						</div>
					</li> -->					
				</ul>
			</div>
   		</div>
<!-- 暂时没有 -->

<!--   		<div class="more-entertainment">
			<div class="more-food-title">购物  <span class='food-en'>Local Delicacy   </span></div>

			<div class="entertainment-lists">
				<ul>
					<li>
						<img src="./img/f1.png" alt="">
						<div class="entertainment-content">
							<div class="entertainment-title">川剧</div>
							<div class="entertainment-desc">
								到四川一定要看川剧，感受川剧的幽默和泼辣。早在唐代就有“蜀戏冠天下”的说法。清代乾隆时，在本地车灯戏基础上，融汇各地声腔，形成了含有高腔、胡琴、昆腔、灯戏、弹戏五种声腔的用四川话演唱的“川剧”。什么时候到，随时都可以上桌吃饭。
							</div>
						</div>
					</li>

					<li>
						<img src="./img/f1.png" alt="">
						<div class="entertainment-content">
							<div class="entertainment-title">川剧</div>
							<div class="entertainment-desc">
								到四川一定要看川剧，感受川剧的幽默和泼辣。早在唐代就有“蜀戏冠天下”的说法。清代乾隆时，在本地车灯戏基础上，融汇各地声腔，形成了含有高腔、胡琴、昆腔、灯戏、弹戏五种声腔的用四川话演唱的“川剧”。什么时候到，随时都可以上桌吃饭。
							</div>
						</div>
					</li>					
				</ul>
			</div>
   		</div> -->


<!--   		<div class="more-entertainment">
			<div class="more-food-title">文化活动  <span class='food-en'>Local Delicacy   </span></div>

			<div class="entertainment-lists">
				<ul>
					<li>
						<img src="./img/f1.png" alt="">
						<div class="entertainment-content">
							<div class="entertainment-title">川剧</div>
							<div class="entertainment-desc">
								到四川一定要看川剧，感受川剧的幽默和泼辣。早在唐代就有“蜀戏冠天下”的说法。清代乾隆时，在本地车灯戏基础上，融汇各地声腔，形成了含有高腔、胡琴、昆腔、灯戏、弹戏五种声腔的用四川话演唱的“川剧”。什么时候到，随时都可以上桌吃饭。
							</div>
						</div>
					</li>

					<li>
						<img src="./img/f1.png" alt="">
						<div class="entertainment-content">
							<div class="entertainment-title">川剧</div>
							<div class="entertainment-desc">
								到四川一定要看川剧，感受川剧的幽默和泼辣。早在唐代就有“蜀戏冠天下”的说法。清代乾隆时，在本地车灯戏基础上，融汇各地声腔，形成了含有高腔、胡琴、昆腔、灯戏、弹戏五种声腔的用四川话演唱的“川剧”。什么时候到，随时都可以上桌吃饭。
							</div>
						</div>
					</li>					
				</ul>
			</div>
   		</div> -->

	</div>
</template>

<script>

// import ImgWrapper from '../imgWrapper/imgWrapper'
import axios from 'axios'
export default {
  name: 'DestinationMore',
  data () {
    return {
		      msg: 'Welcome to destination',
		      food:{},
		      active:{},
		      feature:{},
		      activeFood:{},
		      specialty:{},
		      ecology:"",
		      historyAndCulture:"",
		      touristSeason:"",
		      describe:"",
		      height:"",
		      climate:"",
		      name:""
          }
  },

  mounted(){
  	

  	let id=this.$route.params.id
  	console.log("线路id",this.$route.params.id)
  	this.getDestinationDetail(id)

	axios.get("http://139.129.118.14:8082/WestBoundA/destination_listDetails.json",{
		params:{
			destinationId:id
		}
	}).then((res)=>{
		let destinationDetail=res.data.destinationDetails
		console.log("目的地详情",res.data)
		this.food=res.data.cate
		this.active=res.data.activity
		this.specialty=res.data.specialty
		this.activeFood={
			id:this.food[0].id,
			cover:this.food[0].cover,
			name:this.food[0].name,
			describe:this.food[0].describe

		}
	})

	let width=this.$refs.imgActive.clientWidth
	console.log("width",width)

	 this.height=width/1.5

 	const that = this;
    window.onresize = function temp() {
        that.height = that.$refs.imgActive.clientWidth/1.5;
        console.log("clientHeight",that.height)
    };

  },
  created(){
  		
  },
  methods:{
  	foodActive(item){
		this.activeFood={
			id:item.id,
			cover:item.cover,
			name:item.name,
			describe:item.describe

		}
  	},

  	getDestinationDetail(id){
  		axios.get("http://139.129.118.14:8082/WestBoundA/destination_getDestinationById.json",{
  			params:{
  				destinationId:id
  			}
  		}).then((res)=>{
  			console.log("000000",res)
  			// console.log("经济介绍",res.data.destinationDetails[0].destination)
  			let data=res.data.destination
  			console.log(data.ecology)
  			this.ecology=data.ecology

  			// console.log("ecology",this.ecology)
  			this.historyAndCulture=data.historyAndCulture
  			this.climate=data.climate
  			this.touristSeason=data.touristSeason
  			this.name=data.name
  		})
  	}
  },
  componemts:{
  	// MyHeader
  	// ImgWrapper
  }
}
</script>
<style lang='less'>
.more-food-title{
	border-left: 8px solid #50bbdb !important;
}

.more-container{
	width:64%;
	margin:0 auto;
	padding-bottom:500px;

	.more-name{
		font-size: 40px;
		padding:70px 0 94px 0;
		font-weight:600;
	}

	.more-feature{
		ul{
			display: flex;
			list-style: none;
			li{
				flex:1;
				padding-right:5%;

				.more-imgWrapper{
					text-align: center;
				}

				.more-words{
					.more-title{
						text-align: center;
						padding:30px 0;
						font-weight:600;
						font-size:24px;
					}

					p{
						padding:0;
						margin:0;
						color: #959595;
						line-height: 26px;
					}
				}


			}
			li:last-child{
				padding-right: 0%;
			}
		}
	}

	.more-food{
		margin-top:140px;
		.more-food-title{
			font-size:30px;
			color: #221815;
			padding:0 20px;
			border-left:5px solid rgba(80, 187, 219, 1);
			margin-bottom:60px;
			font-weight:600;

			.food-en{
				color:#959595;
				font-size:18px;
				font-weight:300;
			}
		}

		.food-content{

			.food-active{
				display: flex;
				img{
					flex:1;
					// min-width: 400px;
					// max-width:600px;
					// height:280px;

				}
				.food-info{
					flex:1;
					display: inline-block;
					padding:50px 100px 0 90px;

					.food-name{
						font-size:26px;
						padding-bottom:16px;
						border-bottom:1px solid rgba(229, 229, 229, 1)

					}

					.food-describe{
						padding-top: 1em;
					    font-size: 16px;
					    color: #959595;
					    line-height: 24px;
					    font-weight: 300;
					}
				}
			}

			.food-lists{
				display: flex;
				flex-wrap:wrap;
				
					li.list{
						flex:0 0 22%;
						// padding-right:10px;
						margin-right:2%;
						margin-top:2%;
						text-align: center;
						// max-width:300px;
						// box-shadow: 0px 5px 17px 7px rgba(4, 0, 0, 0.07);
						img{
							width:100%;
							max-height:146px;
						}

						.list-name{
							padding:12px 0;
							font-size:17px;
							color: #221815;
						}
					}

					li.list:hover{
						box-shadow: 0px 5px 17px 7px rgba(4, 0, 0, 0.07);
					}
				
			}
		}
	}

	.more-specialty{
		margin-top:140px;
		.more-food-title{
			font-size:30px;
			color: #221815;
			padding:0 20px;
			border-left:5px solid rgba(80, 187, 219, 1);
			margin-bottom:60px;
			font-weight:600;

			.food-en{
				color:#959595;
			    font-size: 18px;
			    font-weight: 300;

			}
		}	

		.food-content{

			.food-active{
				display: flex;
				img{
					flex:1;
					min-width: 400px;
					max-width:600px;

				}
				.food-info{
					flex:1;
					display: inline-block;
					padding:50px 100px 0 90px;

					.food-name{
						font-size:26px;
						padding-bottom:1em;
						border-bottom:1px solid rgba(229, 229, 229, 1)

					}

					.food-describe{
						padding-top:1em;
						font-size: 20px;
						color:#959595;
					}
				}
			}

			.food-lists{
				display: flex;
				flex-wrap:wrap;
				width:100%;
				min-width: 600px;
				max-width:1400px;
				
					li.list{
						flex:0 1 20%;
						margin-right:12%;
						// padding-right:10px;
						// margin-right:24px;
						// margin-top:24px;
						text-align: center;
						// box-shadow: -1px 3px 10px 0px #ccc;
						img{
							width:100%;
							border-radius:50%;
						}

						.list-name{
							padding:18px 0;
							font-size:22px;
							color: #221815;
							font-weight:600;
						}
						.specialty-desc{
							font-size: 16px;
							font-weight: normal;
							font-style: normal;
							font-stretch: normal;
							line-height: 24px;
							letter-spacing: 0px;
							color: #959595;	
							// padding:0 40px;
							text-align: left;
							font-weight:300;						
						}
					}
				
			}
		}	
	}

	.more-entertainment{

		margin-top:140px;
		.more-food-title{
			font-size:30px;
			color: #221815;
			padding:0 20px;
			border-left:5px solid rgba(80, 187, 219, 1);
			margin-bottom:60px;
			font-weight:600;

			.food-en{
				color:#959595;
				font-size:18px;
				font-weight:300;
			}
		}


		.entertainment-lists{
			ul{
				li{
					// flex:1;
					display: flex;
					margin-bottom:75px;

					img{
						flex:1;
					}
					.entertainment-content{
						flex:2;
						display: inline-block;
						padding:10px 0 0px 56px;
						font-size:30px;

						.entertainment-title{
							padding: 0px 10px 20px 0px;
							border-bottom:1px solid  rgba(229, 229, 229, 1);
							// box-shadow: 0 0 0,0 0 0,0 0 0,2px 2px 2px 2px #ccc;
							// color:#959595;
							font-size:26px;
						}
						.entertainment-desc{
						    color: #959595;
						    font-size: 16px;
						    padding-top: 1em;
						    line-height: 22px;
						    font-weight: 300;
						}


					}

				}
			}


		}


	}
}


ul,li{
	list-style: none;
	padding:0;
	margin:0;
}

p.more-describe{
	font-weight: 300;
	line-height: 30;
	font-size:18px;
	line-height: 26px;
}

</style>