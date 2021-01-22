<template>
  <div id="singer">
    <scroll>
      <!-- <singer-category/> -->
      <ul v-for="item in singer" :key="item.id">
        <li>
          <img :src="item.img1v1Url" alt="" class="singImg">
          <div class="name">
            {{item.name}}
          </div>
        </li>
      </ul>
    </scroll>
  </div>
</template>

<script>
// import SingerCategory from '../../components/content/singer/SingerCategory'
import Scroll from '../../components/common/Scroll.vue'

  export default {
    components: {
      // SingerCategory
      Scroll
    },
    data() {
      return {
        singer: []
      }
    },
    created() {
      this.getSinger()
    },
    methods: {
      getSinger() {
        this.$axios({
          url: '/artist/list'
        })
        .then(res => {
          this.singer = res.data.artists
        })
      }
    }
  }
</script>

<style scoped>
  li {
    display: flex;
    align-items: center;
  }
  .singImg {
    width: 80px;
    border-radius: 50%;
    margin: 10px;
    margin-left: 30px;
  }

  .name {
    font-size: 20px;
    font-weight: 500;
    margin-left: 20px;
  }
</style>