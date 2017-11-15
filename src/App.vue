<template>
  <div id="app">
    <HeaderTop :img='img'></HeaderTop>
    <!-- <router-link to='/destination'>目的地</router-link> -->

    <router-view></router-view> 
    <Foot></Foot>
  </div>
</template>

<script>
import 'normalize.css/normalize.css'
import Vue from 'vue'
import VueRouter from 'vue-router'
import HeaderTop from './components/header/header'
import destination from './components/destination/destination'

import DestinationMore from './components/destination-more/destinationMore'

import Hot from './components/hot/hot'

import Line from './components/line/line'

import LineDetail from './components/line-detail/lineDetail'

import Inn from './components/inn/inn'

import InnDetail from './components/inn-detail/innerDetail'

import Home from './components/home/home'

import Celebrity from './components/celebrity/celebrity'

import CelebrityDetail from './components/celebrityDetail/celebrityDetail'

import Info from './components/info/info'

import InfoDetail from './components/infoDetail/infoDetail'

import Foot from './components/footer/footer'

import CelebrityArticle from './components/celebrityArticle/celebrityArticle'

import Test from './components/test/test'

import About from './components/aboutus/about'

import axios from 'axios'


Vue.use(VueRouter)

const routes=[
  {
    path: '/', 
    redirect: '/home'
  },
  {
    path:'/destination',
    component:destination,
    children:[
      {
        path:'test',
        component:DestinationMore
      }
    ]

  },
  {
    path:'/DestinationMore',
    component:DestinationMore
  },
  {
    path:'/hot',
    component:Hot
  },
  {
    path:'/line',
    component:Line
  },
  {
    name:'lineDetail',
    path:'/line/:id',
    component:LineDetail
  },
  {
    path:'/inn',
    component:Inn
  },
  {
    path:'/innDetail',
    component:InnDetail
  },{
    path:'/home',
    component:Home
  }
  ,{
    path:'/test',
    component:Test
  },
  {
    name:'destinationmore',
    path:'/destination/:id',
    component:DestinationMore
  },

  {
    name:'innDetail',
    path:'/inn/:id',
    component:InnDetail
  },
  {
    path:'/celebrity',
    component:Celebrity,

  },
  {
    name:'celebrityDetail',
    path:'/celebrity/:id',
    component:CelebrityDetail
  },
  {
    path:'/info',
    component:Info
  },{
    name:'infoDetail',
    path:'/info/:id',
    component:InfoDetail
  },
  {
    name:'celebrityArticle',
    path:'/celebrity/article/:id',
    component:CelebrityArticle
  },{
    path:'/about',
    component:About
  }
]

const router=new VueRouter({
  routes
})

export default {
  name: 'app',
  router,
  components: {
    destination,
    HeaderTop,
    DestinationMore,
    Hot,
    LineDetail,
    Inn,
    InnDetail
    ,Test,
    Celebrity,
    CelebrityDetail,
    Info,
    InfoDetail,
    Foot,
    CelebrityArticle,
    About

  },

  data(){
    return {
      img:""
    }
  },
  created (){

  },

  methods:{
    toggleImg(){
      console.log(2)
    }
  },

  mounted(){
    // console.log("APP route",this.$route)
    let path=this.$route.path
    switch (path){
        case '/home':
        this.img='/static/home.jpg'
        break;

        case '/hot':
        this.img='/static/remen.png'
        break;

        case '/destination':
        this.img='/static/des.png'
        break;

        case '/line':
        this.img='/static/line.png'
        break;


        case '/inn':
        this.img='/static/yizhan.png'
        break;

        case '/celebrity':
        this.img='/static/daka.png'
        break;

        case '/info':
        this.img='/static/line.png'
        break;

        case '/about':
        this.img='/static/des.png'
        break;

      }

      if(path.indexOf('/line/')!==-1){

        this.img='/static/line.png'
      }

  },

  // props:{
  //   img:{
  //     type:String
  //   }
  // },

  watch:{
    '$route'(to,from){
      console.log("app route!!!!",to.path)
      let path=to.path


  switch (path){
      case '/home':
      this.img='/static/home.jpg'
      break;

      case '/hot':
      this.img='/static/remen.png'
      break;

      case '/destination':
      this.img='/static/des.png'
      break;

      case '/line':
      this.img='/static/line.png'
      break;


      case '/inn':
      this.img='/static/yizhan.png'
      break;

      case '/celebrity':
      this.img='/static/daka.png'
      break;

      case '/info':
      this.img='/static/line.png'
      break;

      case '/about':
      this.img='/static/des.png'
      break;

    }
  if(path.indexOf('/line/')!==-1){

    this.img='/static/line.png'
  }
  if(path.indexOf('/celebrity/')!==-1){

    this.img='/static/daka.png'
  }
  if(path.indexOf('/info/')!==-1){

    this.img='/static/line.png'
  }

    }
  }
}
</script>

<style>
#app{
position: relative;
}
*{
  padding:0;
  margin:0;
}
a{
  text-decoration:none;
  color:#000;
}

a:hover{
  cursor: pointer!important;
}
</style>
