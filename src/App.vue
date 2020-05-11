<template>
  <div id="app">
    <img src="./assets/logo.png">
    <transition :name="routerTransition">
      <router-view/>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'App',
  watch: {//使用watch 监听$router的变化
    $route(to, from) {
      //如果to索引大于from索引,判断为前进状态,反之则为后退状态
      if(to.meta.index > from.meta.index){
        //设置动画名称
        this.routerTransition = 'slide-left';
      }else if(to.meta.index < from.meta.index){
        this.routerTransition = 'slide-right';
      } else {
        this.routerTransition = 'slide-equal';
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.slide-equal-enter-active,
    .slide-equal-leave-active{
      will-change: transform;
      transition: all 500ms;
      position: absolute;
      top:0;
      left:0;
      bottom:0;
      right:0;
      height:100%;
      width:100%;
    }
    .slide-equal-enter,
    .slide-equal-leave-active {
      opacity: 0;
    }
    .slide-right-enter-active,
    .slide-right-leave-active,
    .slide-left-enter-active,
    .slide-left-leave-active {
        will-change: transform;
        transition: all 500ms;
        position: absolute;
        top:0;
        left:0;
        bottom:0;
        right:0;
        height:100%;
        width:100%;
    }
    .slide-right-enter {
      opacity: 0;
      transform: translate3d(-100%, 0, 0);
    }
    .slide-right-leave-active {
      opacity: 0;
      transform: translate3d(100%, 0, 0);
    }
    .slide-left-enter {
      opacity: 0;
      transform: translate3d(100%, 0, 0);
    }
    .slide-left-leave-active {
      opacity: 0;
      transform: translate3d(-100%, 0, 0);
    }
</style>
