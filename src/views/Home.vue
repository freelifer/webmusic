<template>
<el-container>
  <el-header height=“48px”>
    <div class="toolbar">
        <div class="back"><span><i class="el-icon-arrow-left"></i>返回</span></div>
        <div class="title"><span>标题</span></div>
    </div>
  </el-header>
  <el-main style="padding: 0px;">
    <div class="background">
      <img width="100%" height="100%" src="../assets/bg.jpg">
    </div>
    <!-- music list -->
    <div id="divscroller">
      <ul class="scroll-box">
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
        <li>
          <img id="img-icon" class="" width="60px" height="60px" src="../assets/bg.jpg"/>
        </li>
      </ul>
    </div>

<el-progress type="circle" :percentage="80" color="#8e71c7">

      <slot>
    <img id="img-icon" width="200px" height="200px" src="../assets/bg.jpg">
    </slot>
</el-progress>

<!-- // autoplay preload loop controls -->
    <audio ref="audio"  src="http://117.135.168.12/amobile.music.tc.qq.com/C400001aZHDQ4Kj8sC.m4a?guid=1385141139&vkey=CC6F5F145290C3C7617089131D4314E4789CF99A67EA7344A421BF3A87AFFB75B61051B1A48D15BBC568E09F94213263FFD56DAD3F00A2A2&uin=0&fromtag=66"></audio>
  </el-main>
</el-container>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

@Component({
  components: {
    HelloWorld
  }
})
export default class Home extends Vue {
  $refs!: {
    audio: HTMLAudioElement;
  };
  mounted() {
    console.log("mounted");
    // this.$refs.audio.play()
  }
}
</script>
<style lang="scss">
body {
  margin: 0px;
}
.el-header, .el-footer {
  color: #333;
  text-align: center;
  line-height: 48px;
}

.music-progress {
  width: 200px;
  height: 200px;
}

.music-main {
  padding: 0px;
}

.toolbar {
  width: 100%;
  display: flex;
}

.back {
}
.title {align-self: center;
}
.home {
  width: 100%;
  height: 100%;
}
#img-icon {
  border-radius: 50%;
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
