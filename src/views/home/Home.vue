<template>
<!--  首页-->
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
  <Swiper>
    <swiper-item  v-for="item in banners">
      <a :href="item.link">
        <img :src="item.image" alt="">
      </a>
    </swiper-item>
  </Swiper>
  </div>
</template>

<script>
  import NavBar from "@/components/common/navbar/NavBar";
  import {getHomeMultidata} from "@/network/home";
  import {Swiper,SwiperItem} from "@/components/common/swiper/Swiper";
  export default {
    name: "Home",
    components:{
      NavBar,
      Swiper,
      SwiperItem
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
  .home-nav{
    /*使用变量设置颜色*/
    background-color: var(--color-tint);
    color: white;
  }
</style>
