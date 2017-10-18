<template>
	<div class='hot-container'>
		<div class="hot-tabs">
			<ul>
				<li>雅安</li>
				<li class='active'>雅安</li>
				<li>雅安</li>
				<li>雅安</li>
				<li>雅安</li>
				<li>雅安</li>
			</ul>
		</div>

		<div class="hot-content">
			<div class="more-specialty">
				<!-- <div class="more-food-title">当地美食  <span class='food-en'>Local Delicacy   </span></div> -->

				<div class="food-content">

					<ul class="food-lists">
						<li class='list'>
							<img src="../destination-more/img/f1.png" alt="">
							<p class="list-name"> 色达</p>
							<p class="specialty-desc">
								豆瓣是烹制正宗川菜的主要辅料之一,郫县豆瓣的生产已有一百多年的历史，
								其特色是味辣、香酥、色红，用以炒菜，分外提色增香，被誉为“川菜的灵魂”。
							</p>
							<p class="hot-more">View More...</p>						
						</li>
						<li class='list'>
							<img src="../destination-more/img/f2.png" alt="">
							<p class="list-name">  雅安   </p>
							<p class="specialty-desc">
								豆瓣是烹制正宗川菜的主要辅料之一,郫县豆瓣的生产已有一百多年的历史，
								其特色是味辣、香酥、色红，用以炒菜，分外提色增香，被誉为“川菜的灵魂”。
							</p>
							<p class="hot-more">View More...</p>


						</li>
						<li class='list'>
							<img src="../destination-more/img/f3.png" alt="">
							<p class="list-name">   攀枝花  </p>
							<p class="specialty-desc">
								豆瓣是烹制正宗川菜的主要辅料之一,郫县豆瓣的生产已有一百多年的历史，
								其特色是味辣、香酥、色红，用以炒菜，分外提色增香，被誉为“川菜的灵魂”。
							</p>	
							<p class="hot-more">View More...</p>					
						</li>
						<li class='list'>
							<img src="../destination-more/img/f1.png" alt="">
							<p class="list-name">  甘孜   </p>
							<p class="specialty-desc">
								豆瓣是烹制正宗川菜的主要辅料之一,郫县豆瓣的生产已有一百多年的历史，
								其特色是味辣、香酥、色红，用以炒菜，分外提色增香，被誉为“川菜的灵魂”。
							</p>	
							<p class="hot-more">View More...</p>							
						</li>
						<li class='list'>
							<img src="../destination-more/img/f2.png" alt="">
							<p class="list-name">  阿坝   </p>
							<p class="specialty-desc">
								豆瓣是烹制正宗川菜的主要辅料之一,郫县豆瓣的生产已有一百多年的历史，
								其特色是味辣、香酥、色红，用以炒菜，分外提色增香，被誉为“川菜的灵魂”。
							</p>							
						</li>																
					</ul>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
  name: 'Hot',
  data () {
    return {
      msg: 'Welcome to destination'
    }
  }
}
</script>
<style lang='less'>

	.hot-container{
		width:80%;
		margin:0 auto;

		.hot-tabs{
			text-align: center;
			padding:50px 0;
			ul{
				li{
					box-sizing: border-box;
					display: inline-block;
					padding:0 0em 20px;
					font-size: 18px;
					margin:0 1em;
					color:#959595;
				}
				li.active{
					border-bottom:4px solid rgba(80, 187, 219, 1);

				}
			}
		}



		.more-specialty{
			// margin-top:140px;
			.more-food-title{
				font-size:20px;
				color: #221815;
				padding:0 20px;
				border-left:5px solid rgba(80, 187, 219, 1);
				margin-bottom:60px;

				.food-en{
					color:#959595;
					// font-size:24px;
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
							font-size:20px;
							padding-bottom:1em;
							border-bottom:1px solid rgba(229, 229, 229, 1)

						}

						.food-describe{
							padding-top:1em;
							font-size: 16px;
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

							img{
								min-width: 350px;
								min-width: 240px;
							}
							flex:0 1 33%;
							// padding-right:40px;
							// margin-right:24px;
							margin-top:24px;
							// text-align: center;
							// box-shadow: -1px 3px 10px 0px #ccc;

							.list-name{
								// padding:24px 0;
								font-size:22px;
								color: #221815;
								text-align: left;
							}
							.specialty-desc{
								font-size: 16px;
								font-weight: normal;
								font-style: normal;
								font-stretch: normal;
								line-height: 30px;
								letter-spacing: 0px;
								color: #959595;	
								// padding:0 40px;
								text-align: left;
														padding-right: 1em;						
							}

							.hot-more{
								color: #333333;
								font-size:12px;
							}
						}
					
				}
			}	
		}
	}


</style>