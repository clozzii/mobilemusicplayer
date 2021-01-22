<template>
  <div class="songlist">
    <div class="songs"
      v-for="item in songlist"
      :key="item.id"
    >
      <div class="img">
        <img :src="item.coverImgUrl" alt="">
      </div>
      <div class="text">
        <span class="name">{{item.name}}</span>
        <span class="copywriter">{{item.copywriter}}</span>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        songlist: [
          
        ]
      }
    },
    mounted: function () {
      this.getSongList()
    },
    methods: {
      getSongList() {
        this.$axios({
          url: '/top/playlist/highquality'
        })
        .then(res => {
          this.songlist = res.data.playlists
        })
      }
    }
  }
</script>

<style scoped>
  .songs {
    display: flex;
    margin: 3px;
  }
  img {
    width: 80px;
  }
  .text {
    margin-left: 10px;
    font-size: 15px;
  }
  .name {
    /* font-size: 1px!important; */
    font-weight: 600;
    /* margin-bottom: 100px; */
  }
  .copywriter {
    display: block;
    /* font-size: 1px; */
    color: #D3D3D3;
    margin-top: 10px;
  }
</style>