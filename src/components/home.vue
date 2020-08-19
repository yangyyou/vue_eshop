<template>
  <div>
    <el-button v-on:click="logout" type="info">退出</el-button>
  </div>
</template>

<script>
export default {
  methods: {
    logout () {
      sessionStorage.clear()
      this.$router.push('/login')
    }
  }
}
</script>

<style>

</style>
