<template>
  <el-container>
    <el-header height="“48px”">
      <div class="toolbar">
        <div class="back">
          <span>
            <i class="el-icon-arrow-left"></i>返回
          </span>
        </div>
        <div class="title">
          <span>标题</span>
        </div>
      </div>
    </el-header>
    <el-main style="padding: 0px;">
      <div class="background">
        <img width="100%" height="100%" src="../assets/bg.jpg">
      </div>
      <MusicImage
        class="music-image"
        ref="musicImage"
        strokeWidth="6"
        imageWidth="160"
        musicTotal="15"
        imageSrc="/img/bg.071706b6.jpg"
        @musicClick="handlerMusicClick"
      ></MusicImage>

      <!-- <img id="img-icon" :class=" isRotate ? 'xx rotate' : 'xx rotate pause-rotate' " width="160px" height="160px" src="../assets/bg.jpg"> -->
      <!-- // autoplay preload loop controls -->
      <audio
        ref="audio"
        preload="load"
        controls
        src="http://183.192.163.157/amobile.music.tc.qq.com/C400001gT93A2w8mcs.m4a?guid=1385141139&vkey=0DCDC9692555D3389DE57A814A01AFEAC3FF5776DBC3B97572500FCB2F7E0738620F6F577447EDB748D54F548285C25BB4A3F7D9A15DD690&uin=0&fromtag=66"
      ></audio>
      
      <el-button ref="btn" type="primary" @click="doTheThing">主要按钮</el-button>
    </el-main>
  </el-container>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import MusicImage from "@/components/MusicImage.vue"; // @ is an alias to /src

@Component({
  components: {
    HelloWorld,
    MusicImage
  }
})
export default class Home extends Vue {
  private isRotate: boolean = false;
  $refs!: {
    musicImage: MusicImage;
    audio: HTMLAudioElement;
    btn: HTMLButtonElement;
  };
  mounted() {
    var that = this;
    console.log("mounted");
    // this.$refs.audio.play()
    var t = setTimeout(function() {
      console.log("执行了", that.$refs.btn);
    }, 3000);
  }
  handlerMusicClick(isRunning: boolean) {
    console.log("handlerMusicClick", isRunning);
    if (isRunning) {
      this.$refs.audio.play();
    } else {
      this.$refs.audio.pause();
    }
    // this.$refs.audio.play();
  }
  doTheThing() {
    console.log("主要按钮");
    // this.$refs.audio.play()
    // this.isRotate = !this.isRotate;
    this.$refs.musicImage.toggle();
  }
}
</script>
<style lang="scss">
body {
  margin: 0px;
}
.el-header,
.el-footer {
  color: #333;
  text-align: center;
  line-height: 48px;
}

.music-image {
  margin: 0 auto;
}

.toolbar {
  width: 100%;
  display: flex;
}

.back {
}
.title {
  align-self: center;
}
.home {
  width: 100%;
  height: 100%;
}

.background {
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  opacity: 0.6;
  filter: blur(20px);
}
.music-list-container {
  height: 80px;
  width: 100%;
  position: absolute;
}
.music-list-bg {
  height: 80px;
  width: 100%;
  float: left;
  opacity: 0.2;
  background: #333;
}
.music-list {
  height: 80px;
  overflow-x: scroll;
}
.slide-box {
  width: 1000px;
  height: 80px;
  display: -webkit-box;
  overflow-x: scroll;
  -webkit-overflow-scrolling: touch;
}
.slide-item {
  padding: 5px 10px;
  height: 35px;
}

#divscroller {
  max-width: 2000px;
  width: 100%;
}

#divscroller .scroll-box {
  white-space: nowrap;
  overflow-x: auto;
  height: 120px;
  margin: 0px;
  padding: 0px;
  padding-inline-start: 0px;
}

#divscroller .scroll-box li {
  list-style: none;
  display: inline-block;
  width: 60px;
  margin-top: 30px;
  margin-left: 10px;
  margin-right: 10px;
}

.scroll-box::-webkit-scrollbar {
  width: 0;
  height: 0;
  display: none;
}
</style>
