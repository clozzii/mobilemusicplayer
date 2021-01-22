<template>
  <div id="rank">
    <scroll>
      <ul v-for="item in toplist" :key="item.id">
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
import Scroll from '../../components/common/Scroll.vue'

  export default {
    components: {
      Scroll
    },
    data() {
      return {
        toplist: []
      }
    },
    created() {
      this.getToplist()
    },
    methods: {
      getToplist() {
        this.$axios({
          url: '/toplist/artist'
        })
        .then(res => {
          this.toplist = res.data.list.artists
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