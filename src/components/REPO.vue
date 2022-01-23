<template>
  <div class="repo">
    <div class="repo-title"></div>
    <!-- 基础底座 -->
    <div class="base">
      <div class="dec"></div>
      <!-- 盒子 -->
      <ul class="boxs">
        <li class="box0">
          <span class="s0"></span>
          <span class="s1"></span>
          <span class="s2"></span>
        </li>
        <li class="box1">
          <span class="s0"></span>
          <span class="s1"></span>
          <span class="s2"></span>
        </li>
        <li class="box2">
          <span class="s0"></span>
          <span class="s1"></span>
          <span class="s2"></span>
        </li>
        <li class="box3">
          <span class="s0"></span>
          <span class="s2"></span>
        </li>
        <li class="box4">
          <span class="s0"></span>
        </li>
        <li class="box5">
          <span class="s1"></span>
        </li>
      </ul>
    </div>
    <!-- 起重机 -->
    <div class="crane">
      <div class="crane-base"></div>
      <div class="arm"></div>
      <div class="up-down-arm">
        <div class="arm-m"></div>
        <div class="hand-l"></div>
        <div class="hand-b"></div>
        <div class="hand-box">
          <div class="hand"></div>
          <div class="hand-a"></div>
          <div class="repo-box"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "REPO",
};
</script>

<style lang="less">
.bg(@url,@x:100%,@y:100%) {
  background: url(".././assets/@{url}") no-repeat;
  background-size: @x @y;
}
.repo {
  position: absolute;
  bottom: 6.2rem;
  right: 6.6rem;
  width: 3.1rem;
  height: 2.5rem;
  &:hover {
    .repo-title {
      transform: translate(0.2rem, -0.2rem) scale(1.2);
    }
    .box0 {
      .s1 {
        animation: upDown 1.5s infinite;
      }
      .s2 {
        animation: toRight 1.8s infinite;
      }
    }
    .box1 {
      .s2 {
        animation: upDownSmall 2.2s infinite;
      }
    }
    .box2{
      .s0{
        animation: toLeft 2.3s infinite;
      }
      .s2{
        animation: toFront 2.8s infinite;
      }
    }
    .box3{
      .s0{
        animation: upDownBig 3s infinite;
      }
      .s2{
        animation: upDown 1.8s infinite;
      }
    }
    .box4{
      .s0{
        animation: toAfter 2.8s infinite;
      }
    }
    .box5{
      .s1{
        animation: upDownSmall 2s infinite;
      }
    }
    // 垂直臂增加上下移动
    .up-down-arm{
      animation: upDownArm 5s linear infinite;
    }
    // 前进臂增加伸缩
    .hand-box{
      animation: leftRightArm 5s linear infinite;
    }
    .repo-box{
      animation: repo 5s linear infinite;
    }
  }
  .base {
    position: absolute;
    width: 3.1rem;
    height: 1.88rem;
    left: 0.2rem;
    bottom: -0.3rem;
    .bg("repo_bg.png");
  }
  .boxs {
    li {
      position: absolute;
      span {
        position: absolute;
        width: 0.58rem;
        height: 0.65rem;
        .bg("repo_box.png");
        &.s0 {
          top: 0;
          left: 0;
        }
        &.s1 {
          top: 0.17rem;
          left: 0.3rem;
        }
        &.s2 {
          top: 0.34rem;
          left: 0.6rem;
        }
      }
      &.box0 {
        top: -0.07rem;
        left: 1.2rem;
        z-index: 1;
      }
      &.box1 {
        top: 0.1rem;
        left: 0.9rem;
        z-index: 2;
      }
      &.box2 {
        top: 0.27rem;
        left: 0.6rem;
        z-index: 3;
      }
      &.box3 {
        top: -0.4rem;
        left: 1.2rem;
        z-index: 1;
      }
      &.box4 {
        top: -0.23rem;
        left: 0.9rem;
        z-index: 2;
      }
      &.box5 {
        top: -0.06rem;
        left: 0.6rem;
        z-index: 3;
      }
    }
  }
  .crane {
    position: absolute;
    bottom: 1.88rem;
    right: 1.1rem;
    width: 4rem;
    height: 4rem;
    z-index: 3;
    .crane-base {
      position: absolute;
      top: 2.7rem;
      left: 1rem;
      width: 1.7rem;
      height: 2.49rem;
      .bg("crane_d.png");
    }
    .arm {
      position: absolute;
      top: 2.74rem;
      left: 1.55rem;
      width: 0.43rem;
      height: 1.73rem;
      .bg("crane_arm.png",200%);
      z-index: 6;
    }
    .arm-m{
      position: absolute;
      top: 1.74rem;
      left: 1.62rem;
      width: 0.43rem;
      height: 1.73rem;
      .bg("crane_arm.png",200%);
      background-position-x: 100%;
      z-index: 5;
    }
    .up-down-arm {
      position: absolute;
      top: 0.3rem;
      left: 0;
      width: 5rem;
      height: 5rem;
    }
    .hand-box {
      position: absolute;
      top: 1.18rem;
      left: 1.85rem;
      width: 2.63rem;
      height: 2.72rem;
      z-index: 4;
    }
    .hand-l {
      position: absolute;
      top: 1.9rem;
      left: 1.55rem;
      width: 2.57rem;
      height: 1.74rem;
      .bg("crane_hand1.png",100%,200%);
      z-index: 6;
    }
    .hand-b {
      position: absolute;
      top: 1.82rem;
      left: 1.75rem;
      width: 2.57rem;
      height: 1.74rem;
      .bg("crane_hand1.png",100%,200%);
      background-position-y: 100%;
      z-index: 4;
    }
    .hand {
      position: absolute;
      top: 0.8rem;
      left: 0;
      width: 2.86rem;
      height: 2.85rem;
      .bg("crane_hand.png",200%);
      z-index: 5;
    }
    .hand-a {
      position: absolute;
      top: 0.8rem;
      left: 0;
      width: 2.86rem;
      height: 2.85rem;
      .bg("crane_hand.png",200%);
      background-position-x: 100%;
      z-index: 3;
    }
    .repo-box {
      position: absolute;
      top: 2.8rem;
      left: 2.13rem;
      width: 0.74rem;
      height: 0.82rem;
      .bg("bigbox.png");
      z-index: 4;
    }
  }
  .repo-title {
    position: absolute;
    width: 1.24rem;
    height: 1.03rem;
    top: 1.2rem;
    right: 0.2rem;
    z-index: 4;
    transition: all 0.5s;
    .bg("repo.png");
  }
}
// 上下
@keyframes upDown {
  0% {
    transform: translate(0, 0.01rem);
  }
  25% {
    transform: translate(0, -.1rem);
  }
  50% {
    transform: translate(0, .05rem);
  }
  75% {
    transform: translate(0, -.1rem);
  }
  100% {
    transform: translate(.01rem, .01rem);
  }
}
// 上下运动幅度小
@keyframes upDownSmall {
    0% {
    transform: translate(0, 0.01rem);
  }
  25% {
    transform: translate(0, -.2rem);
  }
  50% {
    transform: translate(0, .01rem);
  }
  75% {
    transform: translate(0, -.2rem);
  }
  100% {
    transform: translate(.01rem, .01rem);
  }
}
// 上下运动幅度大
@keyframes upDownBig {
    0% {
    transform: translate(0, .01rem);
  }
  25% {
    transform: translate(0, -.35rem);
  }
  50% {
    transform: translate(0, .01rem);
  }
  75% {
    transform: translate(0, -.35rem);
  }
  100% {
    transform: translate(.01rem, .01rem);
  }
}
// 向右
@keyframes toRight{
  0% {
    transform: translate(.01rem, 0.01rem);
  }
  25% {
    transform: translate(.2rem, -.2rem);
  }
  50% {
    transform: translate(.01rem, .01rem);
  }
  75% {
    transform: translate(.2rem, -.2rem);
  }
  100% {
    transform: translate(.01rem, .01rem);
  }
}
// 向左
@keyframes toLeft{
  0% {
    transform: translate(.01rem, 0.01rem);
  }
  25% {
    transform: translate(-.2rem, .2rem);
  }
  50% {
    transform: translate(.01rem, .01rem);
  }
  75% {
    transform: translate(-.2rem, .2rem);
  }
  100% {
    transform: translate(.01rem, .01rem);
  }
}
// 向后
@keyframes toAfter{
  0% {
    transform: translate(.01rem, 0.01rem);
  }
  25% {
    transform: translate(-.2rem, -.2rem);
  }
  50% {
    transform: translate(.01rem, .01rem);
  }
  75% {
    transform: translate(-.2rem, -.2rem);
  }
  100% {
    transform: translate(.01rem, .01rem);
  }
}
// 机械臂上下
@keyframes upDownArm {
  0%{transform: translate(0,-.01rem)}
  12%{transform: translate(0,-.6rem)}
  24%{transform: translate(0,-.6rem)}
  36%{transform: translate(0,-.01rem)}
  48%{transform: translate(0,-.01rem)}
  60%{transform: translate(0,-.6em)}
  72%{transform: translate(0,-.6rem)}
  84%{transform: translate(0,-.01rem)}
  100%{transform: translate(0,-.01rem)}
}
// 机械臂前后
@keyframes leftRightArm {
  0%{transform: translate(.01rem,.01rem)}
  12%{transform: translate(.01rem,.01rem)}
  24%{transform: translate(1.9rem,1.11rem)}
  36%{transform: translate(1.9rem,1.11rem)}
  48%{transform: translate(1.9rem,1.11rem)}
  60%{transform: translate(1.9rem,1.11rem)}
  72%{transform: translate(.01rem,.01rem)}
  84%{transform: translate(.01rem,.01rem)}
  100%{transform: translate(.01rem,.01rem)}
}
// repo显隐效果
@keyframes repo {
   0%{opacity: 0;}
   5%{opacity: 1;}
   40%{opacity: 1;}
   50%{opacity: 0;}
   100%{opacity: 0;}
}
</style>
