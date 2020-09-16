<template>
<!--  首页-->
  <div id="home" class="wrapper">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
   <scroll class="content">
    <HomeSwiper :banners="banners"></HomeSwiper>
    <HomeRecommendView :recommends="recommends"></HomeRecommendView>
    <HomeFeatureView></HomeFeatureView>
    <TabControl class="tab-control" :titles="['流行','新款','精选']"></TabControl>
   </scroll>
<!--     <ul class="scroll">-->
<!--      <li>哇哇哇哇</li>-->
<!--      <li>哇哇哇哇</li>-->
<!--      <li>哇哇哇哇</li>-->
<!--    </ul>-->
  </div>
</template>

<script>
  import NavBar from "@/components/common/navbar/NavBar";
  import TabControl from "@/components/content/tabControl/TabControl";
  import Scroll from "@/components/common/scroll/Scroll";

  import HomeSwiper from './childComps/HomeSwiper'
  import HomeRecommendView from "@/views/home/childComps/HomeRecommendView";
  import HomeFeatureView from "@/views/home/childComps/HomeFeatureView";

  import {getHomeMultidata,getHomeGoods} from "@/network/home";

  export default {
    name: "Home",
    components:{
      NavBar,
      TabControl,
      HomeSwiper,
      HomeRecommendView,
      HomeFeatureView,
      Scroll
    },
    data(){
      return{
        // result:null
        banners:[],
        recommends: [],
        goods:{
          'pop':{page:0,list:[]},
          'news':{page:0,list:[]},
          'sell':{page:0,list:[]},
        }
      }
    },
    created() {
      // 1.请求轮播图数据
    this.getHomeMultidata();
      // 2.请求商品数据
    this.getHomeGoods('pop');
    },
    methods:{
      getHomeMultidata(){
        getHomeMultidata().then(res=>{
          console.log(res);
          // this.result=res;
          this.banners=res.data.banner.list;
          this.recommends=res.data.recommend.list;
        })
      },
      getHomeGoods(type){
        const page =this.goods[type].page+1
        getHomeGoods(type,page).then(res=>{
          // console.log(res)
          // this.goods[type].list.push(...res.data.list)
          // this.goods[type].page+1
        })

      }
    }

  }
</script>

<style scoped>
  #home{
        padding-top: 44px;
          /*父元素设置*/
        position: relative;
        /*视口高度*/
        height: 100vh;
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
  .tab-control{
    position: sticky;
    top: 44px;
    z-index: 9;
  }
  .content{
    /*height:600px;*/
    overflow: hidden;
    position: absolute;
    /*固定上下区域 中间可滑动*/
    top: 44px;
    bottom: 49px;
    left: 0;
    right: 0;
  }

  /*设置部分滑动*/
  /*.scroll{*/
  /*  height: 200px;*/
  /*  background-color: pink;*/
  /*  overflow: scroll;*/
  /*}*/

</style>
