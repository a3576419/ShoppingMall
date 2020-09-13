<template>
<!--  首页-->
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <HomeSwiper :banners="banners"></HomeSwiper>
    <HomeRecommendView :recommends="recommends"></HomeRecommendView>
    <HomeFeatureView></HomeFeatureView>
    <ul>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>
      <li>哇哇哇哇</li>

    </ul>
  </div>
</template>

<script>
  import NavBar from "@/components/common/navbar/NavBar";
  import HomeSwiper from './childComps/HomeSwiper'
  import HomeRecommendView from "@/views/home/childComps/HomeRecommendView";
  import HomeFeatureView from "@/views/home/childComps/HomeFeatureView";

  import {getHomeMultidata} from "@/network/home";

  export default {
    name: "Home",
    components:{
      NavBar,
      HomeSwiper,
      HomeRecommendView,
      HomeFeatureView
    },
    data(){
      return{
        // result:null
        banners:[],
        recommends: []
      }
    },
    created() {
      getHomeMultidata().then(res=>{
        console.log(res);
        // this.result=res;
        this.banners=res.data.banner.list;
        this.recommends=res.data.recommend.list;
      })
    }
  }
</script>

<style scoped>
  #home{
    padding-top: 44px;
  }
  .home-nav{
    /*使用变量设置颜色*/
    background-color: var(--color-tint);
    color: white;
    position: fixed;
    left: 0px;
    right: 0px;
    top: 0px;
    z-index: 9;
  }
</style>
