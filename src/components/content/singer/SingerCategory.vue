<template>
  <div class="singercatory">
    singercatory
  </div>
</template>

<script>
  export default {
    data() {
      return {
        singercatory: {}
      }
    }
    created() {
      this.getSingerCategory()
    },
    methods: {
      getSingerCategory() {
        this.$axios({
          url: '/artist/list'
        })
        .then(res => {
          console.log(res)
        })
      }
    }
  }
</script>