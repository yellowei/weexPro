<template>
  <div>
    <image class="testImage" :src="src"></image>
  </div>
</template>

<style scoped>
.testImage {
    width: 750px;
    height: 1250px;
}
</style>

<script>
export default {
  data () {
    return {
      state: '----',
      src: 'http://7xjyw1.com1.z0.glb.clouddn.com/20170412101827.png'
    }
  }
}
</script>
