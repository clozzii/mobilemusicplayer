<template>
  <div id="home">
    <home-header
      title="音乐播放器"
    />
    <recommend
      v-if="this.$route.path == '/'"
    />
    <!-- 路由匹配到的组件将渲染在这里 -->
    <router-view></router-view>
  </div>
</template>

<script>
  import HomeHeader from '../../components/home/HomeHeader.vue'
  import Recommend from '../../views/recommend/Recommend.vue'

  export default {
    components: {
      HomeHeader,
      Recommend
    },
    created() {
    },
    mounted() {
      // this.test()
    },
    methods: {
      test() {
        console.log(this);
        console.log(this.$route);
        
      }
    }
  }
</script>