<template>
  <div id="app">
    <HeaderTop></HeaderTop>
    <!-- <router-link to='/destination'>目的地</router-link> -->

    <router-view></router-view> 
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

// import ImgWrapper from './components/ImgWrapper/imgWrapper'

Vue.use(VueRouter)

const routes=[
  {
    path:'/destination',
    component:destination

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
    path:'/lineDetail',
    component:LineDetail
  },
  {
    path:'/inn',
    component:Inn
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
    Inn

  }
}
</script>

<style>
a{
  text-decoration:none;
  /*color:#000;*/
}
</style>
