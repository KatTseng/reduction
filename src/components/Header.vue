<template>
  <div class="header" :class="{ scrolled: scrolled }">
    <ProgressBar />
    <div class="udn-logo">
      <a href="https://udn.com" class="logo" title="回首頁" target="_blank">
        <i class="udn-icon udn-icon-logo"></i>
      </a>
    </div>
    <div class="header-layout">
      <div class="burger" @click="onBurgerClick">
        <div class="burger-icon"><span></span><span></span><span></span><span></span></div>
      </div>
      <div class="header-menu">
        <div class="buttons">
          <a href="https://udn.com/upf/newmedia/2019_data/recycle/" class="button" title="民眾回收一場空" target="_blank">民眾回收一場空</a>
          <a href="https://udn.com/upf/newmedia/2019_data/recycle/government" class="button" title="政府燒錢有用嗎" target="_blank">政府燒錢有用嗎</a>
          <a href="https://udn.com/upf/newmedia/2019_data/recycle/reduction" class="button active" title="環保不只一條路" target="_blank">環保不只一條路</a>
        </div>
      </div>
    </div>
    <div class="slide-menu">
      <div class="buttons">
        <a href="https://udn.com/upf/newmedia/2019_data/recycle/" class="button" title="民眾回收一場空" target="_blank">民眾回收一場空</a>
        <a href="https://udn.com/upf/newmedia/2019_data/recycle/government" class="button" title="政府燒錢有用嗎" target="_blank">政府燒錢有用嗎</a>
        <a href="https://udn.com/upf/newmedia/2019_data/recycle/reduction" class="button active" title="環保不只一條路" target="_blank">環保不只一條路</a>
      </div>
    </div>
  </div>
</template>

<script>
import ProgressBar from '@/components/ProgressBar'

export default {
  name: 'Header',
  components: {
    ProgressBar
  },
  props: {
    scrolled: Boolean
  },
  methods: {
    onBurgerClick () {
      this.$emit('onSlideMenuTrigger')
    }
  },
  mounted () {
    console.log(this.scrolled)
  }
}
</script>

<style lang="scss">
  .header {
    z-index: 999;
    position: fixed;
    width: 100%;
    top: -48px;
    height: 48px;
    padding-top: 2px;
    background-color: #F7F7F7;
    box-shadow: 0 8px 6px -6px rgba(#a4a4a4, .3);

    @include rwd($RWD_DESKTOP) {
      top: -55px;
      height: 55px;
    }

    &.scrolled {
      top: 0;
      transition: top 0.2s ease 0.1s;
    }
  }

  .header-layout {
    z-index: 995;
    position: relative;
    width: 100%;
    height: 100%;
    padding-left: 44px;
    padding-right: 46px;

    @include use-vertical-align();

    @include rwd($RWD_DESKTOP) {
      padding-right: 0;
      text-align: right;
    }
  }

  .udn-logo {
    z-index: 999;
    position: fixed;
    top: 8px;
    left: 0;

    .logo {
      display: inline-block;
      text-decoration: none;
    }

    i {
      font-size: 2rem;
      color: #CFCFCF;
    }

    @include rwd($RWD_DESKTOP) {
      top: 11px;

      i {
        color: #000000;
      }
    }
  }

  .burger {
    position: absolute;
    right: 0;
    top: 0;

    @include rwd($RWD_DESKTOP) {
      display: none;
    }
  }

  .burger-icon {
    width: 46px;
    height: 46px;
    z-index: 30;
    position: relative;
    transform: rotate(0deg);
    transition: .5s ease-in-out;
    cursor: pointer;
    opacity: 1;
    span {
        display: block;
        position: absolute;
        height: 4px;
        width: 30px;
        margin: 0 auto;
        background: #000;
        border-radius: 2px;
        opacity: 1;
        right: 8px;
        transform: rotate(0deg);
        transition: .455s ease-in-out;
    }
    span:nth-child(1){
        top: 12px;
        transition: .343s ease-out;
        transform-origin: right;
    }
    span:nth-child(2),
    span:nth-child(3){
        top: 21px;
    }
    span:nth-child(4){
        top: 30px;
        transition: .343s ease-out;
    }
  }

  .header-menu {
    display: none;
    text-decoration: none;

    .button{
      margin-right: 36px;
      font-size: 1.125rem;
      color: #ACACAC;
      text-decoration: none;

      &.active {
        color: #464646;
        font-weight: 700;
      }
    }

    @include rwd($RWD_DESKTOP) {
      display: inline-block;
      vertical-align: middle;
    }
  }

  .slide-menu {
    z-index: 990;
    position: absolute;
    top: 0;
    right: -100%;
    width: 100%;
    height: 100vh;
    opacity: 1;
    padding-top: 48px;
    background-color: #FFFFFF;
    transition: right 0.2s linear;
    -webkit-overflow-scrolling: auto;
    overflow: hidden;

    .buttons {
      width: 100%;
      padding: 10px;

      a {
        position: relative;
        display: block;
        padding: 20px 15px 20px 15px;
        color: #ACACAC;
        font-size: 1.5rem;
        background-color: #fff;
        text-align: center;
        text-decoration: none;
        border-bottom: 1px solid rgb(240, 240, 240);

        &.active {
          color: #464646;
          font-weight: 700;
        }
      }
    }

    @include rwd($RWD_DESKTOP) {
      display: none;
    }
  }

  .app.slide-menu-open {
    height: 100%;
    min-height: none;
    overflow: hidden;

    .burger-icon {
      span:nth-child(1){
        opacity: 0;
        transform: rotateY(90deg);
      }
      span:nth-child(2){
        transform: rotate(315deg);
      }
      span:nth-child(3){
        transform: rotate(405deg);
      }
      span:nth-child(4){
        opacity: 0;
        transform: rotateY(-90deg);
      }
    }

    .slide-menu {
      right: 0;
    }
  }
</style>
