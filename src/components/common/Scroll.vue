<template>
  <div class="wrapper"
    ref="wrapper"
  >
    <slot></slot>
  </div>
</template>

<script>
  import BScroll from '@better-scroll/core'

  export default {
    methods: {
      initScroll() {
        this.scroll = new BScroll(this.$refs.wrapper)
      }
    },
    mounted() {
      this.initScroll()
    }
  }
</script>

<style scoped>
  .wrapper {
    position: absolute;
    overflow: hidden;
    top: 70px;
    left: 0;
    bottom: 0;
    right: 0;
  }
</style>