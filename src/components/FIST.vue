<template>
  <div class="fist">
    <div class="fist-box">
      <div class="title"></div>
      <div class="fist-bg1"></div>
      <div class="fist-bg2"></div>
      <!-- 安装进度 -->
      <div class="progress">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        <span></span>
      </div>
      <div class="light-up"></div>
      <!-- 向上喷射效果 -->
      <div class="fire">
        <span
          v-for="point in fireList.point"
          :key="point[3]"
          :style="{
            width: point[0] + 'rem',
            height: point[0] + 'rem',
            left: point[1] + 'rem',
            top: point[2] + 'rem',
            'animation-duration': (Math.random() * 5 + 1).toFixed(2) + 's',
          }"
        >
        </span>
        <i
          v-for="particle in fireList.particle"
          :key="'particle' + particle[3]"
          :style="{
            width: particle[0] / 2 + 'rem',
            height: particle[0] * 10 + 'rem',
            left: particle[1] + 'rem',
            top: particle[2] + 'rem',
            'animation-duration': (Math.random() * 5 + 0.5).toFixed(2) + 's',
          }"
        >
        </i>
      </div>
    </div>
    <div class="light-down"></div>
  </div>
</template>

<script>
export default {
  name: "FIST",
  data() {
    return {
      fireList: {
        point: [], // 圆点
        particle: [], // 粒子
      },
    };
  },
  mounted() {
    this.createFire(50, 10);
  },
  methods: {
    createFire(pointNum, particleNum) {
      let point = [],
        particle = [];
      for (let i = 0; i < pointNum; i++) {
        let size = (Math.random() * 0.08).toFixed(2);
        // 最小5px
        size = size <= 0 ? .05 : size;
        let x = (Math.random() * 3.21).toFixed(2);
        let y = (Math.random() * 4.73).toFixed(2);
        point.push([size, x, y, i]);
      }
      this.fireList.point = point;
      for (let i = 0; i < particleNum; i++) {
        let size = (Math.random() * 0.08).toFixed(2);
        // 最小5px
        size = size <= 0 ? .05 : size;
        let x = (Math.random() * 3.21).toFixed(2);
        let y = (Math.random() * 4.73).toFixed(2);
        particle.push([size, x, y, i]);
      }
      this.fireList.particle = particle;
      console.log(this.fireList);
    },
  },
};
</script>

<style lang="less">
.bg(@url,@x:100%,@y:100%) {
  background: url(".././assets/@{url}") no-repeat;
  background-size: @x @y;
}
@time: 3s;
@delay: 3s;
.fist {
  .fist-box {
    position: absolute;
    bottom: 2.05rem;
    right: 2.91rem;
    width: 4.71rem;
    height: 5.33rem;
    &:hover .title {
      transform: translate(-0.2rem, -0.2rem) scale(1.2);
    }
    .title {
      position: absolute;
      width: 1.46rem;
      height: 1.18rem;
      top: 1.8rem;
      left: 0.4rem;
      z-index: 4;
      .bg("fist_t.png");
      transition: transform 0.5s; // 增加放大缩小时的过度效果
      cursor: pointer;
    }
    .fist-bg1,
    .fist-bg2 {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      .bg("fist.png",200%);
      z-index: 3;
    }
    .fist-bg2 {
      background-position: 100%;
      z-index: 1;
    }
    .progress {
      position: absolute;
      top: 2.1rem;
      left: 2.7rem;
      width: 3.16rem;
      height: 2.03rem;
      z-index: 3;
      span {
        position: absolute;
        width: 1.9rem;
        height: 1.59rem;
        .bg("progress.png",100%,500%);
        &:nth-child(1) {
          top: 0;
          left: 0;
          opacity: 1;
        }
        // 通过delay产生延迟效果
        &:nth-child(2) {
          top: 0.11rem;
          left: 0.31rem;
          background-position-y: 25%;
          animation: progress @time / 1.5 @delay + 0.25s infinite;
        }
        &:nth-child(3) {
          top: 0.22rem;
          left: 0.62rem;
          background-position-y: 50%;
          animation: progress @time / 1.5 @delay + 0.5s infinite;
        }
        &:nth-child(4) {
          top: 0.33rem;
          left: 0.93rem;
          background-position-y: 75%;
          animation: progress @time / 1.5 @delay + 0.75s infinite;
        }
        &:nth-child(5) {
          top: 0.44rem;
          left: 1.24rem;
          background-position-y: 100%;
          animation: progress @time / 1.5 @delay + 1s infinite;
        }
      }
    }
    .fire {
      position: absolute;
      left: 0.7rem;
      bottom: 3.15rem;
      width: 3.21rem;
      height: 4.73rem;
      &::before {
        content: "";
        position: absolute;
        left: 0;
        bottom: 0;
        width: 100%;
        height: 100%;
      }
      span {
        position: absolute;
        border-radius: 50%;
        width: 0.1rem;
        height: 0.1rem;
        background: #fc5d78;
        animation-name: riser;
        animation-timing-function: linear;
        animation-iteration-count: infinite;
      }
      i{
        position: absolute;
        width: .03rem;
        background: linear-gradient(#f58534,transparent);
        animation-name: riser;
        animation-timing-function: linear;
        animation-iteration-count: infinite;
      }
    }
    .light-up {
      position: absolute;
      width: 2.81rem;
      height: 3.04rem;
      bottom: 3.8rem;
      right: 0.9rem;
      z-index: 3;
      animation: lightUp 3s linear infinite;
      .bg("fist_light.png");
      transform-origin: bottom center;
    }
  }
  .light-down {
    position: absolute;
    width: 6.77rem;
    height: 5.22rem;
    right: 1.8rem;
    bottom: 2.1rem;
    z-index: 2;
    .bg("light.png");
    animation: lightDown 1s linear infinite;
  }
}
// 向下的光效果
@keyframes lightDown {
  0% {
    transform: scale(0.9);
  }
  50% {
    transform: scale(1);
  }
  100% {
    transform: scale(0.9);
  }
}
// 向上的光效果
@keyframes lightUp {
  0% {
    transform: rotateX(0deg);
  }
  10% {
    transform: rotateX(10deg);
  }
  20% {
    transform: rotateX(0deg);
  }
  30% {
    transform: rotateX(30deg);
  }
  40% {
    transform: rotateX(0deg);
  }
  50% {
    transform: rotateX(20deg);
  }
  60% {
    transform: rotateX(0deg);
  }
  70% {
    transform: rotateX(40deg);
  }
  80% {
    transform: rotateX(0deg);
  }
  90% {
    transform: rotateX(30deg);
  }
  100% {
    transform: rotateX(0deg);
  }
}
// 进度展示效果
@keyframes progress {
  0% {
    transform: translate(-0.2rem, -0.2rem);
    opacity: 0;
  }
  50% {
    transform: translate(0, 0);
    opacity: 1;
  }
  100% {
    transform: translate(0, 0);
    opacity: 0;
  }
}
@keyframes riser {
  0% {
    transform: translate(0, 0);
    opacity: 0;
  }
  50% {
    transform: translate(0, -1rem);
    opacity: 1;
  }
  100% {
    transform: translate(0, -2rem);
    opacity: 0;
  }
}
</style>
