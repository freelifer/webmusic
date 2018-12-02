<template>
  <div class="mi-component-container" :style="{width:allWidth, height:allWidth}" >
    <div class="mi-wrapper mi-right" :style="{width:harfWidth, height:allWidth}">
      <div
      ref="rightcircle"
        @transitionend.native="aa"
        :class="isRunning ? 'circleProgress rightcircle' : 'circleProgress rightcircle pause-rotate'"
        :style="{width:imageWidth + 'px', height:imageWidth + 'px', 'border-width':strokeWidth + 'px','border-top-width': strokeWidth + 'px', 'border-right-width': strokeWidth + 'px', 'animation-duration': circleProgressLoadTime}"
      ></div>
    </div>
    <div class="mi-wrapper mi-left" :style="{width:harfWidth, height:allWidth}">
      <div
        :class="isRunning ? 'circleProgress leftcircle' : 'circleProgress leftcircle pause-rotate'"
        :style="{width:imageWidth + 'px', height:imageWidth + 'px', 'border-width':strokeWidth + 'px','border-bottom-width': strokeWidth + 'px', 'border-left-width': strokeWidth + 'px', 'animation-duration': circleProgressLoadTime}"
      ></div>
    </div>

    <img :class="isRunning ? 'mi-img rotate' : 'mi-img rotate mi-img-pause-rotate' " :width="imageWidth" :height="imageWidth" :style="{'margin-top':strokeWidth + 'px'}" :src="imageSrc">
    <div class="mi-wrapper" :style="{width:allWidth, height:allWidth}">
      <a @click="handlerClick">
      <i :style="{'font-size': '36px', 'line-height':allWidth}" :class="isRunning ? 'iconfont icon-zantingtingzhi' : 'iconfont icon-bofang'"></i>
      </a>
    </div>
    
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

// https://www.cnblogs.com/xiaozhu007/p/8900037.html
@Component
export default class MusicImage extends Vue {
  @Prop() private strokeWidth!: number;
  @Prop() private imageWidth!: number;
  @Prop() private imageSrc!: String;
  @Prop() private musicTotal!: number;

  private isRunning: boolean = false;

  $refs!: {
    rightcircle: HTMLDivElement;
  };

  mounted() {
    this.$refs.rightcircle.addEventListener('animationend', function aa() {
      console.log('animationend');
    });
    this.$refs.rightcircle.addEventListener('webkitAnimationEnd', function aa() {
      console.log('webkitAnimationEnd');
    });
  }
  toggle() {
    this.isRunning = !this.isRunning;
  };

  handlerClick() {
    console.log('music click....')
    this.toggle()

    this.$emit('musicClick', this.isRunning)
  }

  aa() {
    console.log('aa....')
  }
  // computed
  get allWidth() {
    return Number(this.imageWidth) + Number(this.strokeWidth) * 2 + "px";
  }
  get harfWidth() {
    return Number(this.imageWidth) / 2 + Number(this.strokeWidth) + "px";
  }
  get circleProgressLoadTime() {
    // return  "circleProgressLoad_left " + this.musicTotal +"s linear infinite"
    return  this.musicTotal +"s"
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.mi-start {
  margin: 0 auto;
}
.mi-component-container {
  position: relative;
}
.mi-wrapper {
  position: absolute;
  top: 0;
  overflow: hidden;
}
.mi-right {
  right: 0;
}
.mi-left {
  left: 0;
}

.circleProgress {
  border-color: transparent;
  border-style: solid;
  border-radius: 50%;
  position: absolute;
  top: 0;

  animation: rotate(-135deg);
  -webkit-animation: rotate(-135deg);
  -moz-animation: rotate(-135deg);
}

.rightcircle {
  border-top-style: solid;
  border-top-color: green;
  border-right-style: solid;
  border-right-color: green;
  right: 0;

  animation: circleProgressLoad_right 5s linear infinite;
  -webkit-animation: circleProgressLoad_right 5s linear infinite;
  -moz-animation: circleProgressLoad_right 5s linear infinite;
}

.leftcircle {
  border-bottom-style: solid;
  border-bottom-color: green;
  border-left-style: solid;
  border-left-color: green;
  left: 0;

  animation: circleProgressLoad_left 5s linear infinite;
  -webkit-animation: circleProgressLoad_left 5s linear infinite;
  -moz-animation: circleProgressLoad_left 5s linear infinite;
}

.pause-rotate {
   animation-play-state: paused;
   -webkit-animation-play-state: paused;
   -moz-animation-play-state: paused;
}

@keyframes circleProgressLoad_left {
  0%, 50% { transform: rotate(-135deg); }
  100% { transform: rotate(45deg); }
}
@-webkit-keyframes circleProgressLoad_left {
  0%, 50% { transform: rotate(-135deg); }
  100% { transform: rotate(45deg); }
}
@-moz-keyframes circleProgressLoad_left {
  0%, 50% { ransform: rotate(-135deg); }
  100% { transform: rotate(45deg); }
}

@keyframes circleProgressLoad_right {
  0% { transform: rotate(-135deg); }
  50%, 100% { transform: rotate(45deg); }
}
@-webkit-keyframes circleProgressLoad_right {
  0% { transform: rotate(-135deg); }
  50%, 100% { transform: rotate(45deg); }
}
@-moz-keyframes circleProgressLoad_right {
  0% { transform: rotate(-135deg); }
  50%, 100% { transform: rotate(45deg); }
}

/// image class start

.mi-img {
  border-radius: 50%;
}

.rotate {
  animation: circle 10s infinite linear;
  -webkit-animation:circle 10s infinite linear;
  -moz-animation:circle 10s infinite linear;
}

.mi-img-pause-rotate {
   animation-play-state: paused;
   -webkit-animation-play-state: paused;
   -moz-animation-play-state: paused;
}

@keyframes circle {
  0%{ transform:rotate(0deg); }
  100%{ transform:rotate(360deg); }
}
@-webkit-keyframes circle{
  0%{ transform:rotate(0deg); }
  100%{ transform:rotate(360deg); }
}
@-moz-keyframes circle{
  0%{ transform:rotate(0deg); }
  100%{ transform:rotate(360deg); }
}
</style>
