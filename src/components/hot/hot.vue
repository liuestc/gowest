<template>
	<div class='hot-container'>
		<div class="hot-tabs">
			<ul>
				<li  v-on:click='getHotDestination'  :class='{isActive:true}'>目的地</li>
				<li v-on:click='getHotLine' :class='{isActive:false}' >线路</li>
				<li v-on:click='getHotInn' :class='{isActive:false}' >驿站</li>
				<li v-on:click='getHotCelebrity'  :class='{isActive:false}'>大咖</li>
				<!-- <li >资讯</li> -->
				<!-- <li>雅安</li> -->
			</ul>
		</div>

		<div class="hot-content">
			<div class="more-specialty">

				<div class="food-content">
						<paginate  name="languages" :list="list" :per="9" class="food-lists" ref="paginator">
							<router-link  tag='li'  :to='{name:item.url,params:{id:item.id}}'   class='list'  v-for="item in paginated('languages')" >
								<img :src="item.cover" alt="" ref='imgAuto' class='hot-img'  v-bind:style="{  height: clientHeight + 'px' }">
								<p class="list-name"> {{item.name}}</p>
								<p class="specialty-desc">
									{{item.describe}}
								</p>
								<router-link class="hot-more"  tag='p'  :to='{name:item.url,params:{id:item.id}}'>查看详情 > </router-link>						
							</router-link>
						</paginate>	
																
					<!-- </ul> -->

					<div class="paginate-wrapper">
						<div class="all-page">共 <span class='list-num-wrapper'>{{listNums}}</span>条</div>
						<paginate-links for="languages" :show-step-links="true"  >
				        </paginate-links>
						<div class='page-input'><span>前往</span><input type="text" v-model='pages' @change="goToPage"><span>页</span></div>
					</div>

				</div>


			</div>
		</div>

	</div>
</template>

<script>

import Vue from 'vue'

import VuePaginate from 'vue-paginate'

Vue.use(VuePaginate)

import axios from 'axios'

const that=this;
export default {
  name: 'Hot',
  data () {
    return {
      msg: 'Welcome to destination',
      list:[],
      langs: ['JavaScript', 'PHP', 'HTML', 'CSS', 'Ruby', 'Python', 'Erlang'],
      paginate: ['languages'],
      pages:"",
      listNums:"",
      screenWidth:this.$refs.imgAuto,
      clientHeight:""
    }
  },
  components:{
  	// paginate
  },
  created(){
  	// console.log("screenWidth",this.screenWidth)
  	this.getHotDestination()
  },
  computed:{
  	// listNums(){
  	// 	this.listNums=this.lists.length+1
  	// }
  },
  mounted(){

 	this.clientHeight = (`${document.documentElement.clientWidth}`*.8*0.99-90)/(3*1.6);

    const that = this;
    window.onresize = function temp() {
        that.clientHeight = (`${document.documentElement.clientWidth}`*.8*0.99-90)/(3*1.6);
        console.log("clientHeight",that.clientHeight)
    };
  },

  methods:{
  	goToPage(){
  		console.log("page",this.pages)
  		if (this.$refs.paginator) {
      		this.$refs.paginator.goToPage(this.pages)
    	}
  	},
  	getHotDestination($event){
  		if($event){
	   		let nodes=[...$event.target.parentNode.children]
	  		nodes.forEach((item)=>{
	  			item.className="";
	  		})

	  		$event.target.className='isActive' 			
  		}


  		let list=[]
  		axios.get("http://139.129.118.14:8082/WestBoundA/destination_listHotDestinations.json").then((res)=>{
  			console.log("getHotDestination",res.data.destinations)
  			let destination=res.data.destinations

  			// this.listNums=list.length+1
  			res.data.destinations.forEach((item,index)=>{

  				// let cover2=''
  				// if(item.cover.indexOf(',')==-1){
  				// 	cover2=item.cover.split(",")[0]
  				// }
  				// else{
  				// 	cover2=item.cover
  				// }

  				list.push({
  					"id":item.id,
  					"name":item.name,
  					"describe":item.describe,
  					"cover":item.cover.split(',')[0],
  					"url":"destinationmore"

  				})
  			})

  			// console.log(list)
  			this.list=list

  			this.listNums=list.length
  			console.log("list",this.list)


  		})


  	},
  	getHotLine($event){
  		let nodes=[...$event.target.parentNode.children]
  		nodes.forEach((item)=>{
  			item.className="";
  		})

  		$event.target.className='isActive'  		
  		let list=[]
  		axios.get("http://139.129.118.14:8082/WestBoundA/route_listHotRoutes.json").then((res)=>{
  			console.log("routes",res.data.routes)
  			let destination=res.data.routes
  			destination.forEach((item,index)=>{

  				list.push({
  					"id":item.id,
  					"name":item.name,
  					"describe":item.describe,
  					"cover":item.cover,
  					"url":"lineDetail"

  				})
  			})
  			this.list=list
  			this.listNums=list.length


  			console.log("list",this.list)

  		}) 		
  	},
  	getHotInn($event){
  		let nodes=[...$event.target.parentNode.children]
  		nodes.forEach((item)=>{
  			item.className="";
  		})

  		$event.target.className='isActive'    		
  		let list=[]
  		axios.get("http://139.129.118.14:8082/WestBoundA/hotel_listHotHotels.json").then((res)=>{
  			console.log("hotels",res.data.hotels)
  			let destination=res.data.hotels
  			destination.forEach((item,index)=>{

  				list.push({
  					"id":item.id,
  					"name":item.name,
  					"describe":item.description,
  					"cover":item.cover,
  					"url":"innDetail"

  				})
  			})

  			this.list=list
  			this.listNums=list.length
  			console.log("list",this.list)

  		})  		
  	},

  	getHotCelebrity($event){
  		let nodes=[...$event.target.parentNode.children]
  		nodes.forEach((item)=>{
  			item.className="";
  		})

  		$event.target.className='isActive'    		
  		let list=[]
  		axios.get("http://139.129.118.14:8082/WestBoundA/bigShot_listHotBigShots.json").then((res)=>{
  			console.log("getHotDestination",res.data.BigShots)
  			let destination=res.data.BigShots
  			destination.forEach((item,index)=>{

  				list.push({
  					"id":item.id,
  					"name":item.name,
  					"describe":item.describe,
  					"cover":item.headPortrait,
  					"url":"celebrityDetail"

  				})
  			})

  			// console.log(list)
  			this.list=list
  			this.listNums=list.length
  			console.log("list",this.list)

  		})  		
  	}  	

  }
}
</script>
<style lang='less'>
*{
	padding:0;
	margin:0;
}
	.isActive{
		border-bottom:4px solid rgba(80, 187, 219, 1);
		color:#313131 !important;
		font-weight:600 !important;
	}
	ul,li{
		list-style: none;
	}
	
	.hot-container{
		width:80%;
		margin:0 auto;
		padding-bottom:500px;

		.hot-tabs{
			text-align: center;
			// padding:50px 0;
			padding-top:40px;
			padding-bottom:20px;
			ul{
				li{
					box-sizing: border-box;
					display: inline-block;
					padding:0 0em 10px;
					font-size: 18px;
					margin:0 1em;
					color:#959595;
					font-weight:300;
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

				.food-lists{
					display: flex;
					flex-wrap:wrap;
					width:100%;
					
						li.list{
							flex:0 1 33%;
							box-sizing: border-box;
							// max-width: 370px;
							height:100%;
							padding:0 15px;
							p{
								// max-width:350px;
							}
	
							img{
								// min-width: 350px;
								width:100%;
								// height:200px;
								// max-height: 240px;
								// // height:100%;
								// height:240px;
							}
							margin-top:24px;

							.list-name{
								padding:24px 0 16px 0;
								font-size:22px;
								color: #313131;
								text-align: left;
								margin:0;
								font-weight:600;
							}
							.specialty-desc{
								font-size: 16px;
								font-weight: 300;
								font-style: normal;
								font-stretch: normal;
								line-height: 22px;
								letter-spacing: 0px;
								color: #959595;	
								// padding:0 40px;
								text-align: left;
								padding-right: 1em;						
							}

							.hot-more{
								color: #313131;
								font-size:12px;
								padding:16px 0;
								margin:0;
								font-weight:400;
							}
							.hot-more:hover{
								color:#50bbdb;
							}
						}
					
				}
			}	
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
				// color:#fff;
			}
			li:nth-child(1){
				border-left:1px solid #ccc;
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


p.specialty-desc{
	display: -webkit-box;
	-webkit-box-orient: vertical;
	-webkit-line-clamp: 3;
	overflow: hidden;
}
// p.specialty-desc::after{content: "..."; position: absolute; bottom: 0; right: 11px;
// background: -webkit-linear-gradient(left, transparent, #fff 55%);
// background: -o-linear-gradient(right, transparent, #fff 55%);
// background: -moz-linear-gradient(right, transparent, #fff 55%);
// background: linear-gradient(to right, transparent, #fff 55%);
// }

</style>