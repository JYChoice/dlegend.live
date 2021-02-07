<template>
  <div id="app">
    <div class="top-bar">
      <div class="icon"/>
      <span class="app-name"><b>TimeRec</b></span>
      <span class="slogan">Moments Create Memories</span>
    </div>
    <van-pull-refresh v-model="isLoading" @refresh="onRefresh" loosing-text="^ Release to refresh ^" loading-text="Loading...">
      <router-view class="contents"/>
    </van-pull-refresh>
    <a href="http://www.mytimerec.com">
      <van-button class="open-btn" round color="linear-gradient(to right, #ff9966, #ff6666)">
        <b>Open in TimeRec</b>
      </van-button>
    </a>
  </div>
</template>

<script>
  import {
    Button,
    PullRefresh
  } from 'vant';
  export default {
    name: "app",
    components:{
      [Button.name]: Button,
      [PullRefresh.name]: PullRefresh
    },
    data() {
      return {
        isLoading: false
      }
    },
    methods: {
      onRefresh() {
        setTimeout(() => {
          this.isLoading = false;
        },500);
        window.location.reload();
      }
    }
  }
</script>

<style lang="scss">
  $font-stack: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;
  $primary-color: 	#ff9f80;
  $secondary-color: #ff6655;
  $white: #ffffff;
  $gradient-color: linear-gradient(-45deg, #ff9966, #ff6666);
  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font: 100% $font-stack;
    text-align: center;
    position: relative;
  }
  .tag{
    opacity: 0.7;
  }
  .top-bar{
    justify-content: space-between;
    background-image: $gradient-color;
    height: 4rem;
    width: 100%;
    position: fixed;
    z-index: 1;
    color: $white;
    box-shadow: 2px 10px 16px rgba(0, 0, 0, 0.3);

    .icon{
      background-image: url("./assets/images/icon2.png");
      background-size: 3rem;
      width: 3rem;
      height: 3rem;
      position: fixed;
      left: 0.5rem;
      top: 0.5rem;
    }
    .app-name{
      position: fixed;
      top: 0.6rem;
      left: 4rem;
    }
    .slogan{
      position: fixed;
      top: 2rem;
      left: 4rem;
    }
    .opn{
      background-color: $white;
      color: $secondary-color;
      position: fixed;
      top: 0.8rem;
      right: 0.5rem;
      box-shadow: 2px 10px 16px rgba(0, 0, 0, 0.3);
    }
  }
  .contents{
    position: relative;
    top: 4.5rem;
    z-index: 0;
  }
  .open-btn{
    position: fixed !important;
    left: 30%;
    bottom: 1.25rem;
    z-index: 1;
    box-shadow: 2px 10px 16px rgba(0, 0, 0, 0.3);
  }
</style>
