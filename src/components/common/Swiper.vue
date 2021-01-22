<template>
  <div class="swiper">
    <swiper v-if="carouseldata.length>1" :options="swiperOption">
      <swiper-slide v-for="(item,index) in carouseldata" :key="index">
        <img :src="item.imageUrl" class="swiperImg">
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
  // 引入插件
  import { swiper, swiperSlide } from "vue-awesome-swiper";
  import "swiper/swiper-bundle.css";

  export default {
    components: {
      swiper,
      swiperSlide
    },
    data() {
      return {
        carouseldata: [],

        swiperOption: {
          loop: true,
          notNextTick: true,
          autoplay: {
            delay: 3000,
            stopOnLastSlide: false,
            disableOnInteraction: false
          },

          // 显示分页
          pagination: {
            el: ".swiper-pagination",
            clickable: true //允许分页点击跳转
          },
          // 设置点击箭头
          navigation: {
            nextEl: ".swiper-button-next",
            prevEl: ".swiper-button-prev"
          }
        }
      }
    },
    created: function () {
      this.carousel()
    },
    methods: {
      // 获取轮播图数据
      carousel() {
        this.$axios({
          url: '/banner'
        })
          .then(res => {
            this.carouseldata = res.data.banners
          })
      },
      test() {
        console.log(this);
      }
    },
    computed: {
      swiper() {
        return this.$refs.mySwiper.swiper
      }
    },
    mounted() {
      // console.log('Current Swiper instance object', this.swiper)
      // this.swiper.slideTo(3, 1000, false)
    }
  }
</script>

<style scoped>
  .swiperImg {
    width: 100%;
  }
</style>