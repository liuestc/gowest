<template>
	<div class='destination-container'>
		<!-- 123 -->
		<!-- <img src="./img/destination-top.png" alt=""> -->
		<div class="destination-content">

			<div class="left-wrapper">
				<div class="destination-sort">
					<div class="left-title">目的地省属分类</div>
					<ul class='pro-lists'>
						<!-- <li v-on:click='provinceQuery'> 四川  &nbsp; <span>4</span></li> -->
						<li v-for='item in destinationsLists' @click='getDestinationByProvince(item[0])' > {{item[1]}} &nbsp;<span>({{item[2]}})</span></li>

					</ul>
				</div>
				<div class="destination-tags">
					<div class="left-title">目的地标签</div>
					<ul>
						<li v-for='(item,index) in labels' @click='searchLabelsDestination(item,index)'    :class="{activetags:item.isActive}"  >{{item.name}}</li>
					</ul>	
				</div>
			</div>
			<div class="right-wrapper"  ref='rightSide' :style='{marginLeft:marginLeft+"px"}'>
				<div class="destination-search"><input placeholder="Search" type="text"><span class='search-icon'><img src="./img/Shape-49.png" alt=""></span></div>

				<paginate  name="languages" :list="destinations" :per="4" class="food-lists" ref="paginator">

					<div class="destination-intro"  v-for="item in paginated('languages')">
						<div class="destination-swiper">
							<swiper >
						        <swiper-slide class='swiper-container' v-for='(item2,index) in item.cover'><img :src="item2" alt=""></swiper-slide>

						      </swiper>
						</div>
						<div class="destination-words">
							<router-link class="destination-name"   :to='{name:"destinationmore",params:{id:item.id}}'>{{item.name}}</router-link>

							<div class="destination-describe">
								<p>{{item.describe}}</p>
								<p>{{item.ecology}}</p>
								<p>{{item.historyAndCulture}}</p>

								<p class='intro-little'><i class='intro-little-line'> </i> 信息来自 <span class='where'>{{item.publisher}}</span> <span>3</span> -评论</p>
								<p class='intro-little'><i><img src="./img/logo2.png" alt=""></i> 信息来自 <span class='where' v-for='label in item.labels'>{{label.name}}</span> </p>
							</div>
						</div>
					</div>
				</paginate>

				<div class="paginate-wrapper">
					<div class="all-page">共 <span class='list-num-wrapper'>{{listNums}}</span>条</div>
					<paginate-links for="languages" :show-step-links="true"  >
			        </paginate-links>
					<div class='page-input'><span>前往</span><input type="text" v-model='pages' @change="goToPage"><span>页</span></div>
				</div>

			</div>
		</div>

		<!-- <router-view></router-view> -->
	</div>
</template>

<script>
import axios from 'axios'

import 'swiper/dist/css/swiper.css'

import Vue from 'vue'

import VuePaginate from 'vue-paginate'

Vue.use(VuePaginate)

import VueAwesomeSwiper from 'vue-awesome-swiper'

import DestinationMore from '../destination-more/destinationMore'

// import ImgWrapper from '../imgWrapper/imgWrapper'

Vue.use(VueAwesomeSwiper)


import { swiper, swiperSlide } from 'vue-awesome-swiper'

export default {
  name: 'destination',
  data () {
    return {
      msg: 'Welcome to destination',
      destinations:[],
      destinationsLists:[],
      labels:"",
      paginate: ['languages'],
      listNums:"",
      pages:"",
      marginLeft:"",
      isActive:true


    }
  },
  created (){
	  axios.get('http://139.129.118.14:8082/WestBoundA/destination_listDestinationStatistics.json').then((res)=>{
	      
	      this.destinationsLists=res.data.statistics
	      console.log("destinationsLists",this.destinationsLists)

	    }).catch(err=>{
	      console.log(err)
	    })

//

		this.getDestinationByProvince(25)

	    this.getAllLabels()
  },

  mounted(){
  	let width=document.body.clientWidth
  	if(width>1440){
  		this.marginLeft=width*.1
  		console.log(this.marginLeft)
  	}

  	else{
  		this.marginLeft=0;
  	}

	    const that = this;
	    window.onresize = function temp() {
	    	let width=document.body.clientWidth
		  	if(width>1440){
		  		that.marginLeft=width*.08
		  		console.log(that.marginLeft)
		  	}

		  	else{
		  		that.marginLeft=0;
		  	}
	    };
  },

  methods :{
  	goToPage(){
  		console.log("page",this.pages)
  		if (this.$refs.paginator) {
      		this.$refs.paginator.goToPage(this.pages)
    	}
  	},

  	provinceQuery: function($event){
  		console.log(1)
  		console.log("provinceId",$event)
  	},
  	getAllLabels(){
	  axios.get('http://139.129.118.14:8082/WestBoundA/label_listLabel.json').then((res)=>{
	      
	    this.labels=res.data.labels
	    console.log("labels",this.labels)

	    this.labels.forEach((item,index)=>{
          Vue.set(item,"isActive",false)
        })
        // this.labels[0].isActive=true

	    }).catch(err=>{
	      console.log(err)
	    })	
  	},

  	searchLabelsDestination(item,index){

  		// console.log("标签id",item.id)
      this.labels.forEach(function(v,i){
        i==index?v.isActive=true:v.isActive=false
      })

      // this.labelsList.forEach(function(v,i){
      //   i==curIndex?v.isActive=true:v.isActive=false
      // })

      // this.getLabelCelebrity(curItem.id)

  		 axios.get('http://139.129.118.14:8082/WestBoundA/destination_listDestinationByLabelId.json',{
  		 	params:{
  		 		labelId:item.id
  		 	}
  		 }).then((res)=>{
  		 	this.destinations=res.data.destinations
		      this.destinations.forEach((item,index)=>{
		      	item.cover=item.cover.split(",")
		      })

		      console.log("labels",this.destinations)

		    this.listNums=this.destinations.length
  		 })
  	},

  	getDestinationByProvince(id){
	  axios.get('http://139.129.118.14:8082/WestBoundA/destination_listDestinationByAddress.json',{
	      params:{
	        addressId:id
	      }
	    }).then((res)=>{
	      
	      this.destinations=res.data.destinations
	      console.log("通过省份查找目的地列表",this.destinations)
	      this.destinations.forEach((item,index)=>{
	      	item.cover=item.cover.split(",")
	      })

	      this.listNums=this.destinations.length

	      console.log(this.destinations)


	    }).catch(err=>{
	      console.log(err)
	    })		
  	}


  },
  // router,
  components: {
    swiper,
    swiperSlide

  }
}
</script>
<style lang='less'>
.activetags{
	 background-color: rgba(80, 187, 219, 1);
	 color:#fff!important;
	 border:none!important;
	 padding: 7px 13px!important;
}

::-webkit-input-placeholder { /* Chrome/Opera/Safari */
  font-weight:300;
}
::-moz-placeholder { /* Firefox 19+ */
  font-weight:300;
}
:-ms-input-placeholder { /* IE 10+ */

  font-weight:300;
}
:-moz-placeholder { /* Firefox 18- */

  font-weight:300;
}


ul,li{
	list-style:none;
	margin:0;
	padding:0;
}
.destination-container{
	width:66%;
	margin:0 auto;
	padding-bottom:440px;

	.destination-content{
		display: flex;
		.left-wrapper{
			flex: 0 1 300px;
			font-size:14px;
			.destination-sort,.destination-tags{
				padding-top:80px;

				.left-title{
					font-size:18px;
					font-weight:800;
					margin-bottom:20px;
				}
				ul{
					padding:0;
					margin:0;
					// margin-left:-12px;

					li{
						font-size: 12px;
						display: inline-block;
						margin-right:6px;
						color:#959595;
						text-align: center;
						margin-bottom: 6px;
						padding:6px 12px;
						font-weight:300;
					}

				}
			}
			.destination-sort{
				ul.pro-lists{
					// margin-left:-10px;
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

			flex: 480px;
			.destination-search{

    			max-width: 600px;
    			position: relative;
    			margin:44px 0 40px 0px;
				// width:100%;
				input{
					height:36px;
					line-height: 36px;
					width:96%;
					padding-left:16px;
				}
				span.search-icon{
				    position: absolute;
				    top: 12px;
				    right:22px;
				}

			}

			.destination-intro{
				// margin-left:520px;
				// padding-right: 200px;
				max-width: 600px;
    			min-width: 480px;
    			margin-bottom:50px;
    			font-size: 16px;
				.destination-swiper{
					// height:336px;
					height:100%;
					.swiper-container{
						// height:300px;
						img{
							width:100%;
							// height:100%;
						}
					}
				}
				.destination-words{
					margin-top:33px;
					.destination-name{
						// display: inline-block;
						float:left;
						font-size: 24px;
						color:#221815;
						padding:0 42px 0 10px;
						font-weight:600;
					}
					.destination-describe{
						// display: inline-block;
						overflow: hidden;
						font-weight:300;

						p{
							line-height: 20px;							
							text-align:justify;
							color:#959595;
							padding-top:0;
							margin:0;
							padding-bottom: 1em;

							font-size:14px;	

							.where{
								// color:#444;	
								display: inline-block;
								padding:0 10px;
							}

							i{
								img{
									width:10px;
									height:10px;
								}
							}						
						}

						p:nth-child(3){
							padding-bottom:16px;
						}

						p.intro-little{
							display: inline-block;
							padding-right:40px;
							padding-bottom:4px;
							font-size:12px;
						}
					}
				}
			}
		}
	}
}

@media (max-width: 1200px) {
	.destination-container .destination-content .right-wrapper .destination-intro{
		max-width:400px !important;
	}
	.destination-container .destination-content .right-wrapper .destination-search{
		max-width:480px !important;
	}
}


	.paginate-wrapper{
		position: relative;
		text-align: center;
		margin-top:80px;
		font-size:12px;

		.all-page{
			display: inline-block;
			span.list-num-wrapper{
				display: inline-block;
				padding:0 10px;
			}
		}
		.paginate-links.languages{
			display: inline-block;

			margin:0 auto;
			text-align: center;
			li{
				display: inline-block;
				padding:7px 12px;
				border:1px solid #ccc;
				border-left:none;
			}

			li:nth-child(1){
				border:1px solid #ccc;
			}
			li.active{
				border:1px solid #50bbdb;
				a{
					color:#fff;
				}

			}
		}

		.page-input{
			// position: absolute;
			margin-left:-6px;
			display: inline-block;
			input{
				width:20px;
				padding:5px;
			}

			span{
				display: inline-block;
				padding:7px ;
				// border:1px solid #ccc;
				border-left:none;
			}

			span:nth-child(1){
				border-right:none;
			}
		}		
	}

::-webkit-input-placeholder { /* Chrome/Opera/Safari */
  color: #959595;
}
::-moz-placeholder { /* Firefox 19+ */
  color: #959595;
}
:-ms-input-placeholder { /* IE 10+ */
  color: #959595;
}
:-moz-placeholder { /* Firefox 18- */
  color: #959595;
}

.intro-little-line{
	height: 12px;
    width: 2px;
    background: #444444;
    display: inline-block;
    /* top: 4px; */
    transform: translateY(1px);
    margin-right: 9px;

}

ul.pro-lists{
	width:226px;
	li{
		width: 68px;
    	height: 18px;
    	text-align: left!important;
    	padding:0!important;
	}
}

</style>