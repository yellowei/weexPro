<template>
  <div class="wrapper">
    <TopHeader></TopHeader>
    <image :src="logo" class="logo" />
    <text class="greeting">The environment is ready!</text>
    <HelloWorld/>
    <!-- <ImageTest></ImageTest> -->
    <button id="goImageBtn" class="routerlink" v-on:click="goImage">Image</button>
    <button class="routerlink">Video</button>
    <button class="routerlink">List</button>
    <button class="routerlink">Image</button>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import ImageTest from './components/ImageTest.vue'
import TopHeader from './components/TopHeader.vue'
var getURL = require('./base-url.js').getURL
var navigator = weex.requireModule('navigator')
var modal = weex.requireModule('modal')

export default {
  name: 'App',
  components: {
    HelloWorld,
    ImageTest,
    TopHeader
  },
  data () {
    return {
      logo: 'https://gw.alicdn.com/tfs/TB1yopEdgoQMeJjy1XaXXcSsFXa-640-302.png'
    }
  },
  methods: {
    // 前往ImageTest页面
    goImage () {
      console.log('will jump')
      var url = getURL(this, 'components/ImageTest')
      var env = weex.config.env
      modal.toast({ message: env.platform })
      navigator.push({
        url: url,
        animated: 'true'
      }, event => {
        modal.toast({ message: 'callback: ' + event })
      })
    }
  },
  created () {
    console.log('created!')
  }
}
</script>

<style scoped>
.wrapper {
    /* justify-content: center; */
    align-items: center;
}
.logo {
    width: 424px;
    height: 200px;
}
.greeting {
    text-align: center;
    margin-top: 70px;
    font-size: 50px;
    color: #41b883;
}
.message {
    margin: 30px;
    font-size: 32px;
    color: #727272;
}
.routerlink {
    /* width: 200px;
    height: 100px; */
    font-size: 50px;
    border-width: 1px;
    text-align: center;
    justify-content: center;
    background-color: palegoldenrod;
    border-radius: 12px;
    padding: 10px;
    margin-top: 10px;
}
</style>
