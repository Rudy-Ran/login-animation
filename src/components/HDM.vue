<template>
  <div class="hdm">
    <div class="base">
      <div class="title"></div>
    </div>
    <div class="box">
      <div class="panel1"></div>
      <div class="panel2"></div>
      <div class="light"></div>
    </div>
    <div class="hdm-to-fist">
      <div class="line">
        <div class="spot1"></div>
        <div class="spot2"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HDM",
};
</script>

<style lang="less">
.bg(@url,@x:100%,@y:100%) {
  background: url(".././assets/@{url}") no-repeat;
  background-size: @x @y;
}
.hdm {
  position: absolute;
  right: 0;
  bottom: 0;
  width: 4rem;
  height: 4rem;
  z-index: 3;
  &:hover {
    cursor: pointer;
    .hdm-to-fist {
      .spot1,
      .spot2 {
        opacity: 1;
      }
      .line {
        width: 2.06rem;
        &::before {
          content: "";
          position: absolute;
          right: 0;
          bottom: .15rem;
          width: 0.05rem;
          height: 0.05rem;
          background: #fff;
          border-radius: 50%;
          animation: hdmEnergy 2s linear infinite;
        }
        &::after {
          content: "";
          position: absolute;
          bottom: 0rem;
          right: .22rem;
          width: 0.05rem;
          height: 0.05rem;
          background: #fff;
          border-radius: 50%;
          animation: hdmEnergyBack 2s linear infinite;
        }
      }
    }
    .title {
      transform: translate(0.2rem, -0.2rem) scale(1.2);
    }
    .box {
      animation: upDown 2s linear infinite;
    }
    .panel1 {
      animation: fadeIn 3s 0.5s linear infinite;
    }
    .panel2 {
      animation: toDown 3s linear infinite;
    }
    .light::before {
      animation: toggleHeight 3s linear infinite;
    }
  }
  .base {
    position: absolute;
    width: 4.58rem;
    height: 2.77rem;
    bottom: -0.37rem;
    right: -0.4rem;
    .bg("hdm_bg.png");
    .title {
      position: absolute;
      bottom: 0.66rem;
      left: 0.1rem;
      width: 1.16rem;
      height: 1.05rem;
      z-index: 4;
      .bg("hdm.png");
      transition: transform 0.5s; // 增加放大缩小时的过度效果
    }
  }
  .box {
    position: absolute;
    bottom: -0.62rem;
    right: 0.1rem;
    width: 3.81rem;
    height: 3.25rem;
    .bg("hdm1.png");
    z-index: 4;
    .panel1 {
      position: absolute;
      width: 1.1rem;
      height: 1.14rem;
      top: -0.7rem;
      left: 0.4rem;
      .bg("hdm2.png",auto);
    }
    .panel2 {
      position: absolute;
      width: 1.5rem;
      height: 1.79rem;
      right: 0.1rem;
      bottom: 2.6rem;
      .bg("hdm_t2.png",auto);
    }
    .light {
      position: absolute;
      width: 4.6rem;
      height: 1.98rem;
      transform: rotate(30deg);
      bottom: 2.66rem;
      right: -1.6rem;
      // opacity: 0;
      &::before {
        content: "";
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        .bg("hdm_light.png");
        background-position: bottom center;
      }
    }
  }
  .hdm-to-fist {
    .line {
      position: absolute;
      width: 0;
      height: 1.41rem;
      right: 2.99rem;
      bottom: 1.25rem;
      .bg("fist_hdm.png",auto);
      transition: width .6s; // 过度效果 .6s后变成 2.06rem
      background-position: right center;
    }
    .spot1 {
      position: absolute;
      bottom: 1.16rem;
      right: 1.68rem;
      width: 0.38rem;
      height: 0.29rem;
      z-index: 3;
      opacity: 0;
      .bg("fist_hdm_spot.png");
      transition: opacity .6s;
    }
    .spot2 {
      position: absolute;
      bottom: -0.1rem;
      right: -0.1rem;
      width: 0.5rem;
      height: 0.31rem;
      z-index: 3;
      opacity: 0;
      .bg("fist_hdm_spot1.png");
      transition: opacity 1s;
    }
  }
}
// 上下效果
@keyframes upDown {
  0% {
    transform: translate(0, 0.01rem);
  }
  25% {
    transform: translate(0, -0.05rem);
  }
  50% {
    transform: translate(0, 0.05rem);
  }
  75% {
    transform: translate(0, -0.05rem);
  }
  100% {
    transform: translate(0, 0.1rem);
  }
}
// 淡入效果
@keyframes fadeIn {
  0% {
    width: 0rem;
    opacity: 0;
  }
  20% {
    opacity: 1;
  }
  70% {
    width: 100%;
    opacity: 1;
  }
  80% {
    width: 100%;
    opacity: 0;
  }
  100% {
    width: 100%;
    opacity: 0;
  }
}
// 向下运动效果
@keyframes toDown {
  0% {
    bottom: 2.9rem;
    opacity: 0;
  }
  30% {
    bottom: 2.8rem;
    opacity: 1;
  }
  80% {
    bottom: 2.7rem;
    opacity: 1;
  }
  100% {
    bottom: 2.6rem;
    opacity: 0;
  }
}
@keyframes toggleHeight {
  0% {
    height: 0rem;
    opacity: 0;
  }
  30% {
    height: 100%;
    opacity: 1;
  }
  80% {
    height: 100%;
    opacity: 1;
  }
  100% {
    height: 100%;
    opacity: 0;
  }
}
// hdm-to-fist 圆点
@keyframes hdmEnergy {
  0% {
    transform: translate(0,0);
    opacity: 0;
  }
  20% {
    transform: translate(0,-.17rem);
    opacity: 1;
  }
  90% {
    transform: translate(-1.75rem,-1.17rem);
    opacity: 1;
  }
  100%{
    transform: translate(-1.75rem,-1.17rem);
    opacity: 0;
  }
}
@keyframes hdmEnergyBack {
  0% {
    transform: translate(-1.75rem,-1.17rem);
    opacity: 0;
  }
  20% {
    transform: translate(-1.75rem,-1.17rem);
    opacity: 1;
  }
  95% {
    transform: translate(0,-.17rem);
    opacity: 1;
  }
  100%{
    transform: translate(0,0);
    opacity: 0;
  }
}
</style>
