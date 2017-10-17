<template>
	<div class='more-container'>
		<div class='more-name'>成都</div>

		<div class='more-feature'>
			<ul>
				<li>

					<div class='more-imgWrapper'>						
						<img src="./img/icon-dqqh.png" alt="">
					</div>
					

					<div class='more-words'>
						<div class="more-title">地区气候</div>
						<p class="more-describe">
							成都，是一个地理方位，在中国的版图上恰巧位于著名的“震旦线”与北纬33度交汇处；更是一个动态历史概念，
							李冰、文翁、杜甫……无数的人来到这里，吸纳、再造并反哺，不断丰盈她的存在。经过漫漫岁月的雕琢与淬炼，
							成都人更加精致和缓、温文尔雅，这座城也越发体现上善若水、润物不争的气质
						</p>
					</div>
				</li>

				<li>
					<div class="more-imgWrapper">
						<img src="./img/icon-dqqh.png" alt="">
					</div>

					<div class='more-words'>
						<div class="more-title">地区气候</div>
						<p class="more-describe">
							成都，是一个地理方位，在中国的版图上恰巧位于著名的“震旦线”与北纬33度交汇处；更是一个动态历史概念，
							李冰、文翁、杜甫……无数的人来到这里，吸纳、再造并反哺，不断丰盈她的存在。经过漫漫岁月的雕琢与淬炼，
							成都人更加精致和缓、温文尔雅，这座城也越发体现上善若水、润物不争的气质
						</p>
					</div>
				</li>
				<li>
					<div class="more-imgWrapper">
						<img src="./img/icon-dqqh.png" alt="">
					</div>

					<div class='more-words'>
						<div class="more-title">地区气候</div>
						<p class="more-describe">
							成都，是一个地理方位，在中国的版图上恰巧位于著名的“震旦线”与北纬33度交汇处；更是一个动态历史概念，
							李冰、文翁、杜甫……无数的人来到这里，吸纳、再造并反哺，不断丰盈她的存在。经过漫漫岁月的雕琢与淬炼，
							成都人更加精致和缓、温文尔雅，这座城也越发体现上善若水、润物不争的气质
						</p>
					</div>
				</li>
				<li>

					<div class="more-imgWrapper">
						<img src="./img/icon-dqqh.png" alt="">
					</div>
					

					<div class='more-words'>
						<div class="more-title">地区气候</div>
						<p class="more-describe">
							成都，是一个地理方位，在中国的版图上恰巧位于著名的“震旦线”与北纬33度交汇处；更是一个动态历史概念，
							李冰、文翁、杜甫……无数的人来到这里，吸纳、再造并反哺，不断丰盈她的存在。经过漫漫岁月的雕琢与淬炼，
							成都人更加精致和缓、温文尔雅，这座城也越发体现上善若水、润物不争的气质
						</p>
					</div>
				</li>				
			</ul>
		</div>
	</div>
</template>

<script>

// import MyHeader from '../header/Header'
import ImgWrapper from '../imgWrapper/imgWrapper'
export default {
  name: 'DestinationMore',
  data () {
    return {
      msg: 'Welcome to destination'
    }
  },
  componemts:{
  	// MyHeader
  	ImgWrapper
  }
}
</script>
<style lang='less'>

.more-container{
	width:88%;
	margin:0 auto;

	.more-name{
		font-size: 56px;
		padding:70px 0 94px 0;
	}

	.more-feature{
		ul{
			display: flex;
			list-style: none;
			li{
				flex:1;
				padding-right:5%;
				// text-align: center;

				// .more-words{

				// 	.more-title{
				// 		padding:30px 0;
				// 	}

				// 	p{
				// 		text-align: justify;
				// 		padding: 0;
				// 		margin:0;
				// 	}
				// }

				.more-imgWrapper{
					text-align: center;
				}

				.more-words{
					.more-title{
						text-align: center;
						padding:30px 0;
					}

					p{
						padding:0;
						margin:0;
						color: #959595;
						line-height: 30px;
					}
				}


			}
			li:last-child{
				padding-right: 0%;
			}
		}
	}
}

</style>