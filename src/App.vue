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
            <div class="spot"></div>
            <div class="spot"></div>
          </div>
          <div class="robotic-arm"></div>
          <div class="box"></div>
        </div>
        <FIST/>
        <HDM/>
        <REPO/>
        <IFIST/>
      </div>
    </div>
  </div>
</template>

<script>
import FIST from './components/FIST.vue'
import HDM from './components/HDM.vue'
import REPO from './components/REPO.vue'
import IFIST from './components/IFIST.vue'
export default {
  name: "App",
  components: {
    FIST,
    HDM,
    REPO,
    IFIST
  },
  data() {
    return {
      interval: null,
    };
  },
  mounted() {
    let time = 2000;
    this.addItem(time);
    this.interval = setInterval(() => {
      this.addItem(time);
    }, time);
  },
  methods: {
    addItem(time) {
      let belt = document.getElementById("belt");
      let box = belt.getElementsByClassName("box")[0];
      let item = document.createElement("div");
      item.setAttribute("class", "item load");
      box.appendChild(item);
      setTimeout(() => {
        item.setAttribute("class", "item onGoing");
        setTimeout(() => {
          box.removeChild(item);
        }, 10000);
      }, time / 2);
    },
  },
};
</script>

<style lang="less">
.bg(@url,@x:100%,@y:100%) {
  background: url("./assets/@{url}") no-repeat;
  background-size: @x @y;
}
@timer: 2s;
.main {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  .bg("bg.jpg");
  overflow: hidden;
  .suspend-bg {
    span {
      position: absolute;
      .bg("bg_d.png",5.41rem,3.39rem);
      &.bg-d0 {
        width: 1rem;
        height: 2.23rem;
      }
      &.bg-d1 {
        width: 1.48rem;
        height: 2.9rem;
        background-position: -1.01rem 0;
      }
      &.bg-d2 {
        width: 2.93rem;
        height: 3.39rem;
        background-position: -2.48rem 0;
      }
      // 坐下两个盒子
      &:nth-child(1) {
        left: 3rem;
        bottom: -1rem;
        .bg-d0();
        animation: upDown 2s linear infinite;
      }
      &:nth-child(2) {
        left: 4rem;
        bottom: -1rem;
        .bg-d1();
        animation: upDown 2.5s linear infinite;
      }
      // 右上四个盒子
      &:nth-child(3) {
        top: -0.5rem;
        right: 4.2rem;
        .bg-d2();
        animation: upDown 2.8s linear infinite;
      }
      &:nth-child(4) {
        top: 1.1rem;
        right: 2.8rem;
        .bg-d2();
        animation: upDown 2.8s linear infinite;
      }
      &:nth-child(5) {
        top: 0.8rem;
        right: 1.7rem;
        .bg-d0();
        animation: upDown 2s linear infinite;
      }
      &:nth-child(6) {
        top: 0.3rem;
        right: 0.2rem;
        .bg-d1();
        animation: upDown 2.5s linear infinite;
      }
      // 右侧盒子
      &:nth-child(7) {
        top: 5rem;
        right: -0.4rem;
        .bg-d0();
        animation: upDown 2s linear infinite;
      }
      // 右下盒子
      &:nth-child(8) {
        bottom: -2.4rem;
        right: 4rem;
        .bg-d2();
        animation: upDown 2.8s linear infinite;
      }
      &:nth-child(9) {
        bottom: -3rem;
        right: 1.6rem;
        .bg-d2();
        animation: upDown 2.8s linear infinite;
      }
    }
  }
  .main-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  .belt {
    position: absolute;
    width: 15.03rem;
    height: 8.65rem;
    bottom: 0;
    right: 0;
    .belt-base {
      position: absolute;
      bottom: 0;
      right: 0;
      width: 100%;
      height: 100%;
      .bg("belt.png");
      z-index: 2;
    }
    .line {
      position: absolute;
      right: 3.5rem;
      bottom: 0.1rem;
      width: 7.72rem;
      height: 4.42rem;
      .bg("line.png");
      z-index: 1;
      .spot {
        &::before,
        &::after {
          content: "";
          position: absolute;
          width: 0.05rem;
          height: 0.05rem;
          border-radius: 50%;
          background: #fff;
        }
        &:nth-child(1) {
          &::before,
          &::after {
            left: 0.2rem;
            bottom: 3.02rem;
          }
          &::before {
            animation: spot1 10s linear infinite;
          }
          &::after {
            animation: spot1Back 5s linear infinite;
          }
        }
        &:nth-child(2) {
          &::before,
          &::after {
            left: 2rem;
            bottom: 0.45rem;
          }
          &::before {
            animation: spot2 4.7s linear infinite;
          }
          &::after {
            animation: spot2Back 5s linear infinite;
          }
        }
      }
    }
    .robotic-arm {
      position: absolute;
      right: -1rem;
      top: -0.7rem;
      width: 0.82rem;
      height: 1.53rem;
      .bg("fist_hand.png");
      animation: surfaced @timer linear infinite;
    }
    .box {
      position: relative;
      top: 0;
      left: 0;
      z-index: 2;
    }
    .item {
      position: absolute;
      top: 0.95rem;
      right: -0.2rem;
      width: 1.59rem;
      height: 1rem;
      .bg("fist_item.png");
      &.load {
        animation: boxFirstLoad @timer / 2 linear forwards;
      }
      &.onGoing {
        animation: boxMove 10s linear forwards;
      }
      &::before {
        content: "";
        position: absolute;
        width: 0.8rem;
        height: 0.73rem;
        top: -0.3rem;
        left: 0.43rem;
        .bg("fist_line.png");
        animation: fist_item_line 1.4s linear forwards;
      }
      &::after {
        content: "";
        position: absolute;
        width: 1.63rem;
        height: 1.73rem;
        top: -0.73rem;
        left: 0rem;
        opacity: 0;
        .bg("fist_item_light.png");
        animation: fist_item_light 10s linear forwards;
      }
    }
  }
}

// 上下浮动效果
@keyframes upDown {
  0% {
    transform: translate(0, 0.05rem);
  }
  50% {
    transform: translate(0, 0.1rem);
  }
  100% {
    transform: translate(0, 0.05rem);
  }
}
// 机械臂浮出效果
@keyframes surfaced {
  0% {
    top: -1rem;
    right: -1rem;
  }
  25% {
    top: -1rem;
    right: 0rem;
  }
  50% {
    top: -0.7rem;
    right: 0rem;
  }
  75% {
    top: -1rem;
    right: 0rem;
  }
  100% {
    top: -1rem;
    right: -1rem;
  }
}
// 盒子首次进入效果
@keyframes boxFirstLoad {
  0% {
    top: 0.65rem;
    right: -1.2rem;
  }
  50% {
    top: 0.65rem;
    right: -0.2rem;
  }
  100% {
    top: 0.95rem;
    right: -0.2rem;
  }
}
// 盒子快速移动
@keyframes boxMove {
  100% {
    top: 9.4rem;
    right: 14.5rem;
    opacity: 0.5;
  }
}
// 盒子上线条动画
@keyframes fist_item_line {
  100% {
    opacity: 0;
  }
}
// 发光盒子动画
@keyframes fist_item_light {
  0% {
    opacity: 0;
  }
  25% {
    opacity: 0;
  }
  35% {
    opacity: 1;
  }
  100% {
    opacity: 1;
  }
}
// 第一个圆点正序运动
@keyframes spot1 {
  0% {
    left: 0rem;
    bottom: 3.02rem;
  }
  35% {
    left: 2.4rem;
    bottom: 1.65rem;
  }
  50% {
    left: 3.6rem;
    bottom: 1.92rem;
  }
  90% {
    left: 6.9rem;
    bottom: 0.02rem;
  }
  100% {
    left: 7.7rem;
    bottom: 0.42rem;
  }
}
// 第一个个圆点倒序
@keyframes spot1Back {
  0% {
    left: 7.5rem;
    bottom: 0.42rem;
  }
  10% {
    left: 7rem;
    bottom: 0.12rem;
  }
  50% {
    left: 3.6rem;
    bottom: 2.02rem;
  }
  65% {
    left: 2.54rem;
    bottom: 1.75rem;
  }
  100% {
    left: 0rem;
    bottom: 3.12rem;
  }
}
// 第二个圆点正序
@keyframes spot2 {
  0% {
    left: 2rem;
    top: .45rem;
  }
  45% {
    left: 4.9rem;
    top: 2.1rem;
  }
  60% {
    left: 5.06rem;
    top: 2.92rem;
  }
  90% {
   left: 6.92rem;
    top: 3.92rem;
  }
  100% {
   left: 7.53rem;
    top: 3.62rem;
  }
}
@keyframes spot2Back {
  0% {
    left: 7.54rem;
    top: 3.52rem;
  }
  10% {
    left: 6.92rem;
    top: 3.84rem;
  }
  40% {
    left: 5.2rem;
    top: 2.9rem;
  }
  55% {
   left: 5.05rem;
    top: 2.0rem;
  }
  100% {
   left: 2rem;
    top: .32rem;
  }
}
#app {
  position: relative;
  width: 100%;
  min-height: 100%;
  height: 100%;
}
</style>
