<template>
  <div
    class="swiper-container"
    :class="{'empty': imgUrl === []}"
  >
    <div class="swiper-wrapper">
      <div
        class="swiper-slide"
        v-for="item in imgUrl"
        @click="initFocus(item.categoryId)"
      >
        <router-link
          tag="a"
          :to="`/product-list?categoryId=${item.categoryId}`"
          v-if="item.categoryId"
        >
          <img
            :src="item.imgUrl"
            class="swiper_img "
            ref="slideImg"
            :onerror="defaultImg"
          >
        </router-link>
        <div v-else>
          <img
            :src="item.imgUrl"
            class="swiper_img"
            ref="slideImg"
            :onerror="defaultImg"
          >
        </div>
      </div>
    </div>
    <div class="swiper-pagination"></div>
  </div>
</template>
<script>
import Swiper from "swiper";
import "swiper/dist/css/swiper.min.css";
import "swiper/dist/js/swiper.min.js";

export default {
  data() {
    return {
      defaultImg: 'this.src="' + require("../../assets/loading.png") + '"'
    };
  },
  props: {
    imgUrl: {
      type: Array,
      default: []
    },
    imgHeight: {
      type: Number,
      default: 340
    }
  },
  mounted() {
    this.slider = new Swiper(".swiper-container", {
      // autoplay: true,
      // speed: 2000,
      // // autoplay: 2000,
      // loop: true,
      // observer: true,//修改swiper自己或子元素时，自动初始化swiper
      // observeParents: true,//修改swiper的父元素时，自动初始化swiper
      // 分页器
      pagination: {
        el: ".swiper-pagination"
      },

      observer: true, //修改swiper自己或子元素时，自动初始化swiper
      observeParents: true, //修改swiper的父元素时，自动初始化swiper
      loop: true,
      autoplay: true,
       lazyLoading : true,//懒加载开启
      paginationClickable: true,
      notNextTick: true,
      initialSlide: 0,
      setWrapperSize: true,
      autoplayDisableOnInteraction: false
    });

    // this.$refs.slideImg.style.height = this.imgHeight + 'px'
  },
  methods: {
    initFocus(id) {
      // console.log(id)
    }
  }
};
</script>
<style lang="scss" rel="stylesheet/scss">
.swiper-container {
  width: 100%;
  margin-top: 0;
  .swiper_img {
    width: 100%;
  }
}
</style>
