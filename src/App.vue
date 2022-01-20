<template>
  <div id="app">
    <div class="main">
      <!-- 背景悬浮动画 -->
      <div class="suspend-bg">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
      </div>
      <!-- 主体部分 -->
      <div class="main-wrapper">
        <!-- 传送带 -->
        <div class="belt" id="belt">
          <div class="belt-base"></div>
          <div class="line">
            <div class="sopt"></div>
            <div class="sopt"></div>
          </div>
          <div class="robotic-arm"></div>
          <div class="box"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
    
  }
}
</script>

<style lang="less">
.bg(@url,@x:100%,@y:100%){
  background:url('./assets/@{url}') no-repeat;
  background-size: @x @y;
}

.main{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  .bg('bg.jpg');
  overflow: hidden;
  .suspend-bg{
    span{
      position: absolute;
      .bg('bg_d.png',5.41rem,3.39rem);
      &.bg-d0{
        width: 1rem;
        height: 2.23rem;
      }
      &.bg-d1{
        width: 1.48rem;
        height: 2.9rem;
        background-position: -1.01rem 0;
      }
      &.bg-d2{
        width: 2.93rem;
        height: 3.39rem;
        background-position: -2.48rem 0;
      }
      // 坐下两个盒子
      &:nth-child(1){
         left: 3rem;
         bottom: -1rem;
         .bg-d0();
         animation: upDown 2s linear infinite;
      }
      &:nth-child(2){
        left: 4rem;
        bottom: -1rem;
        .bg-d1();
        animation: upDown 2.5s linear infinite;
      }
      // 右上四个盒子
      &:nth-child(3){
        top: -0.5rem;
        right: 4.2rem;
        .bg-d2();
        animation: upDown 2.8s linear infinite;
      }
      &:nth-child(4){
        top: 1.1rem;
        right: 2.8rem;
        .bg-d2();
        animation: upDown 2.8s linear infinite;
      }
      &:nth-child(5){
        top: 0.8rem;
        right: 1.7rem;
        .bg-d0();
        animation: upDown 2s linear infinite;
      }
      &:nth-child(6){
        top: 0.3rem;
        right: 0.2rem;
        .bg-d1();
        animation: upDown 2.5s linear infinite;
      }
      // 右侧盒子
      &:nth-child(7){
        top: 5rem;
        right: -.4rem;
        .bg-d0();
        animation: upDown 2s linear infinite;
      }
      // 右下盒子
      &:nth-child(8){
        bottom: -2.4rem;
        right: 4rem;
        .bg-d2();
        animation: upDown 2.8s linear infinite;
      }
      &:nth-child(9){
        bottom: -3rem;
        right: 1.6rem;
        .bg-d2();
        animation: upDown 2.8s linear infinite;
      }
    }
  }
  .main-wrapper{
    position:absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  .belt{
    position:absolute;
    width: 15.03rem;
    height: 8.65rem;
    bottom: 0;
    right: 0;
    .belt-base{
      position: absolute;
      bottom: -2.8rem;
      right: 0;
      width: 100%;
      height: 100%;
      .bg('belt.png');
      z-index: 1;
    }
  }
}

// 上下浮动效果
@keyframes upDown {
  0% {transform: translate(0,.05rem);}
  50% {transform: translate(0,.1rem);}
  100% {transform: translate(0,.05rem);}
}

#app {
  position: relative;
  width: 100%;
  min-height: 100%;
  height: 100%;
}
</style>
