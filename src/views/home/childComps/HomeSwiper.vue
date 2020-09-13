<template>
  <div>
    <Swiper>
      <SwiperItem v-for="(item,index) in banners" :key="index">
        <a :href="item.link">
          <img :src="item.image">
        </a>
      </SwiperItem>
    </Swiper>
  </div>
</template>

<script>
  // import Swiper from "@/components/common/swiper/Swiper";
  // import SwiperItem from "@/components/common/swiper/SwiperItem";
  // 因为在index.js直接导出了所有 所以在这也可一块导入
  import {Swiper,SwiperItem} from "@/components/common/swiper";

  export default {
    name: "HomeSwiper",
    props:{
      banners:{
        type:Array,
        default(){
          return[]
        }
      }
    },
    components:{
      Swiper,
      SwiperItem
    }
  }
</script>

<style scoped>

</style>
