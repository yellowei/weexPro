<template>
  <!-- @loadmore="fetch" loadmoreoffset="10" -->
  <list class="list">
    <header>
      <text class="banner">HEADER</text>
    </header>
    <refresh class="refresh" @refresh="onrefresh" @pullingdown="onpullingdown" :display="refreshing">
      <text class="indicator">Refreshing ...</text>
    </refresh>
    <cell class="cell" v-for="num in lists" :key="num.in">
      <div class="panel">
        <text class="text">{{num}}</text>
      </div>
    </cell>
    <loading class="loading" @loading="onloading" :display="showLoading">
      <text class="indicator">Loading...</text>
    </loading>
  </list>
</template>

<style scoped>
.banner {
    width: 750px;
    padding: 25px;
    font-size: 60px;
    text-align: center;
    font-weight: bold;
    color: #41b883;
    background-color: rgb(162, 217, 192);
}
.panel {
    width: 600px;
    height: 300px;
    margin-left: 75px;
    margin-top: 35px;
    margin-bottom: 35px;
    flex-direction: column;
    justify-content: center;
    border-width: 2px;
    border-style: solid;
    border-color: rgb(162, 217, 192);
    background-color: rgba(162, 217, 192, 0.2);
}
.text {
    font-size: 88px;
    text-align: center;
    color: #41b883;
}
.indicator {
    text-align: center;
    /* justify-content: center; */
    font-size: 42px;
}
.loading {
    width: 750;
    display: -ms-flex;
    display: -webkit-flex;
    display: flex;
    -ms-flex-align: center;
    -webkit-align-items: center;
    -webkit-box-align: center;
    align-items: center;
}
</style>

<script>
const modal = weex.requireModule('modal')
export default {
  data () {
    return {
      lists: [1, 2, 3, 4, 5],
      showLoading: 'hide',
      refreshing: 'hide'
    }
  },
  methods: {
    // fetch (event) {
    //   modal.toast({ message: 'loadmore', duration: 1 })
    //   setTimeout(() => {
    //     const length = this.lists.length
    //     for (let i = length; i < length + 4; i++) {
    //       this.lists.push(i + 1)
    //     }
    //   }, 800)
    // },
    onloading (event) {
      modal.toast({ message: 'loading', duration: 1 })
      this.showLoading = 'show'
      setTimeout(() => {
        const length = this.lists.length
        for (let i = length; i < length + 4; i++) {
          this.lists.push(i + 1)
        }
        setTimeout(() => {
          this.showLoading = 'hide'
        }, 1)
      }, 2000)
    },
    onrefresh (event) {
      modal.toast({ message: 'refresh', duration: 1 })
      this.refreshing = 'show'
      setTimeout(() => {
        this.lists = [1, 2, 3, 4, 5]
        this.refreshing = 'hide'
      }, 2000)
    },
    onpullingdown (event) {
      // modal.toast({ message: 'pulling down', duration: 1 })
    }
  }
}
</script>
