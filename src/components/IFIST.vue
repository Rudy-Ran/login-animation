<template>
  <div class="ifist">
    <div class="ifist-title"></div>
    <!-- IFST基础底座 -->
    <div class="base">
      <div class="dec"></div>
      <div class="bios"></div>
      <div class="bios-bg"></div>
      <div class="spot"></div>
      <div class="line"></div>
    </div>
    <!-- IFST盒子 -->
    <div class="box1">
      <div class="light"></div>
      <div class="panel">
        <div class="p0"></div>
        <div class="p1"></div>
        <div class="p2"></div>
      </div>
      <div class="lines"></div>
    </div>
    <!-- OS -->
    <div class="box2">
      <div class="top"></div>
      <div class="os right">
        <div class="lines"></div>
      </div>
      <div class="os left">
        <div class="lines"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IFIST",
};
</script>

<style lang="less">
.bg(@url,@x:100%,@y:100%) {
  background: url(".././assets/@{url}") no-repeat;
  background-size: @x @y;
}
@timers: 3s;
.ifist {
  position: absolute;
  right: 7.95rem;
  bottom: 2.77rem;
  width: 7rem;
  height: 4rem;
  z-index: 4;
  &:hover {
    .base {
      .bios {
        transform: translate(0, 0);
      }
      .bios-bg {
        opacity: 1;
      }
      .line {
        width: 1.26rem;
        &::before {
          content: "";
          position: absolute;
          top: 0.3rem;
          left: 0;
          width: 0.05rem;
          height: 0.05rem;
          background: #fff;
          border-radius: 50%;
          animation: energy 1.8s linear infinite;
        }
        &::after {
          content: "";
          position: absolute;
          top: 0.22rem;
          left: 0.2rem;
          width: 0.05rem;
          height: 0.05rem;
          background: #fff;
          border-radius: 50%;
          animation: energyBack 2s linear infinite;
        }
      }
      .spot {
        opacity: 1;
      }
    }
    .dec {
      animation: light 1s infinite;
    }
    .ifist-title {
      transform: translate(0.2rem, -0.2rem) scale(1.2);
    }
    .box1 {
      .p0 {
        opacity: 0;
        animation: showP0 @timers 0.5s linear infinite;
      }
      .p1 {
        opacity: 0;
        animation: showP1 @timers 0.5s linear infinite;
      }
      .p2 {
        opacity: 0;
        animation: showP2 @timers 0.5s linear infinite;
      }
      .lines::before {
        animation: lines 1s linear forwards;
      }
    }
    .box2{
      .lines::before{
        animation: lines 1s linear forwards;
      }
    }
    .lines::after{
      opacity: 1;
      transition: opacity 1s 1s linear;
    }
  }
  .base {
    position: absolute;
    right: 0;
    bottom: 0;
    width: 6.22rem;
    height: 3.94rem;
    .bg("ifist_bg.png");
    .dec {
      position: absolute;
      left: 0.15rem;
      bottom: 0.22rem;
      width: 1.89rem;
      height: 1.26rem;
      .bg("ifist_bg_d.png");
    }
    .bios {
      position: absolute;
      top: 2.8rem;
      left: 1.5rem;
      width: 1.07rem;
      height: 0.67rem;
      .bg("bios.png",200%);
      z-index: 1;
      transform: translate(-0.02rem, 0.03rem);
      transition: transofrm 0.5s linear;
    }
    .bios-bg {
      position: absolute;
      top: 2.8rem;
      left: 1.5rem;
      width: 1.07rem;
      height: 0.67rem;
      .bg("bios.png",200%);
      background-position: 100% 0;
      opacity: 0;
      transition: opacity 0.5s linear;
    }
    .spot {
      position: absolute;
      top: 1.33rem;
      right: 0.7rem;
      width: 0.4rem;
      height: 0.22rem;
      opacity: 0;
      .bg("ifist_spot.png");
      transition: opacity 1s;
    }
    .line {
      position: absolute;
      top: 1.1rem;
      left: 5.2rem;
      width: 0;
      height: 0.84rem;
      overflow: hidden;
      transition: width 0.6s;
      .bg("ifist_line.png",auto);
      background-position: left center;
    }
  }
  .ifist-title {
    position: absolute;
    top: 0.5rem;
    left: 2.83rem;
    width: 1.06rem;
    height: 1.02rem;
    z-index: 4;
    transition: transform 0.5s;
    .bg("ifist.png");
  }
  .lines {
    width: 0.32rem;
    height: 0.57rem;

    &::before {
      content: "";
      display: block;
      width: 0%;
      height: 0%;
      .bg("ifist_line1.png",0.32rem,0.57rem);
    }
    &::after {
      content: "";
      position: absolute;
      top: 0.05rem;
      left: 0.04rem;
      width: 0.05rem;
      height: 0.05rem;
      border-radius: 50%;
      background: #fff;
      opacity: 0;
    }
  }
  .box1 {
    position: absolute;
    top: 0.25rem;
    left: 0.8rem;
    width: 4.07rem;
    height: 3.25rem;
    z-index: 2;
    .bg("ifist1.png");
    .panel {
      position: absolute;
      bottom: 3rem;
      left: 0.96rem;
      width: 1.26rem;
      height: 1.47rem;
      div {
        .bg("ifist_t.png",300%);
      }
      .p0 {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
      }
      .p1 {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-position: 50% 0;
      }
      .p2 {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-position: 100% 0;
      }
    }
    .lines {
      position: absolute;
      top: 1.9rem;
      left: 2.25rem;
      &::after {
        animation: lineSpot 1s linear infinite;
      }
    }
  }
  .box2 {
    position: absolute;
    top: -1.1rem;
    left: 2.5rem;
    width: 4.2rem;
    height: 3.83rem;
    .lines {
      position: absolute;
      top: 1.9rem;
      left: 0.8rem;
      &::after {
         animation: lineSpot 1s .3s linear infinite;
      }
    }
    .top {
      position: absolute;
      top: 0.05rem;
      left: 0.75rem;
      z-index: 2;
      width: 2.52rem;
      height: 1.25rem;
      .bg("ifist3.png");
    }
    .os {
      position: absolute;
      width: 1.03rem;
      height: 2.38rem;
      .bg("ifist2.png",200%);
      z-index: 1;
    }
    .left {
      top: 0.5rem;
      left: 1.22rem;
    }
    .right {
      top: 0.24rem;
      left: 1.72rem;
      background-position-x: 100%;
    }
  }
}

// 圆点运动效果
@keyframes energy {
  0% {
    transform: translate(0, 0);
    opacity: 0;
  }
  20% {
    transform: translate(0, -0.2rem);
    opacity: 1;
  }
  95% {
    transform: translate(1.25rem, 0.48rem);
    opacity: 1;
  }
  100% {
    transform: translate(1.25rem, 0.48rem);
    opacity: 0;
  }
}
@keyframes energyBack {
  0% {
    transform: translate(1.25rem, 0.48rem);
    opacity: 0;
  }
  20% {
    transform: translate(1.25rem, 0.48rem);
    opacity: 1;
  }
  95% {
    transform: translate(0, -0.2rem);
    opacity: 1;
  }
  100% {
    transform: translate(0, 0);
    opacity: 0;
  }
}
// BIOS灯光效果
@keyframes light {
  0% {
    opacity: 0.4;
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0.4;
  }
}
// IFST面板效果
@keyframes showP0 {
  0% {
    transform: translate(-0.2rem, 0);
    opacity: 0;
  }
  15% {
    transform: translate(0, 0);
    opacity: 1;
  }
  90% {
    transform: translate(0.2rem, 0);
    opacity: 0;
  }
  100% {
    transform: translate(0, 0);
    opacity: 0;
  }
}
@keyframes showP1 {
  0% {
    transform: translate(-0.2rem, 0);
    opacity: 0;
  }
  15% {
    transform: translate(-0.2rem, 0);
    opacity: 0;
  }
  30% {
    transform: translate(0.01rem, 0);
    opacity: 1;
  }
  90% {
    transform: translate(0.2rem, 0);
    opacity: 0;
  }
  100% {
    transform: translate(0.01rem, 0);
    opacity: 0;
  }
}
@keyframes showP2 {
  0% {
    transform: translate(-0.2rem, 0);
    opacity: 0;
  }
  30% {
    transform: translate(-0.2rem, 0);
    opacity: 0;
  }
  45% {
    transform: translate(0.01rem, 0);
    opacity: 1;
  }
  90% {
    transform: translate(0.2rem, 0);
    opacity: 0;
  }
  100% {
    transform: translate(0.01rem, 0);
    opacity: 0;
  }
}
// 线条效果
@keyframes lines {
  0% {
    width: 0%;
    height: 33.33%;
  }
  50% {
    width: 100%;
    height: 33.33%;
  }
  100% {
    width: 100%;
    height: 100%;
  }
}
@keyframes lineSpot {
    0%{transform: translate(.18rem,.43rem);}
    50%{transform: translate(.18rem,.13rem);}
    100%{transform: translate(.01rem,.01rem);}
}
</style>
