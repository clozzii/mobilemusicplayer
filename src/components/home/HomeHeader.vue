<template>
  <div class="home-head">
    <div class="title">
      {{title}}
    </div>
    <div class="nav-list">
      <ul>
        <li 
          v-for="(item,index) in navlist" 
          :key="index"
          :class="{navActive: isActive === index}"
          @click="navClick(index, item)"
        >
          {{item.name}}
        </li>
      </ul>
    </div>
    
  </div>
</template>

<script>
  export default {
    props: {
      title: {
        type: String,
        default: '音乐播放器'
      }
    },
    data() {
      return {
        navlist: [
          { path: '/recommend', name: '推荐'},
          { path: '/singer', name: '歌手'},
          { path: '/rank', name: '排行'},
          { path: '/search', name: '搜索'}
        ],
        isActive: '',
      }
    },
    computed: {
    },
    methods: {
      navClick(index, item) {
        this.isActive = index
        this.$router.push({path: item.path})
      }
    }
  }
</script>

<style scoped>
  .title {
    color: #00BFFF;
    font-size: 18px;
    font-weight: 700;
    text-align: center;
    letter-spacing: 5px;
  }

  .nav-list ul {
    display: flex;
    margin: 5px 0 10px 0;
  }

  .nav-list ul li {
    flex: 1;
    text-align: center;
    color: #A9A9A9;
  }

  .navActive {
    color:#00BFFF!important;
    font-weight: 700;
  }
</style>