<template>
  <div id="recommend">
    <scroll>
      <div class="scroll"> 
        <swiper/>
        <song-list/>
      </div>
    </scroll>
  </div>
</template>

<script>
  import Swiper from '../../components/common/Swiper.vue'
  import SongList from '../../components/content/recommend/SongList.vue'
  import Scroll from '../../components/common/Scroll.vue'

  export default {
    components: {
      Swiper,
      SongList,
      Scroll
    }
  }
</script>