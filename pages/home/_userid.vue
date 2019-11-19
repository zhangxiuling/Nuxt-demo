<template>
  <div>
    用户id为 {{userid}} 的主页
  </div>
</template>

<script>

export default {
  validate ({ params }) {
    // userid必须为数字才能进入本页面，否则进入404或500错误页面
    return /^\d+$/.test(params.userid)
  },

  data() {
    return {
      userid: ''
    }
  },

  created() {
    this.userid = this.$route.params.userid
  }
}
</script>

<style>
</style>