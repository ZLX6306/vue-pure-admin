<template>
  <el-card shadow="never" class="mt-[20px]">
    <template #header>
      <div class="card-header">
        <span class="font-medium">
          视频组件，采用开源的
          <el-link
            href="https://www.liveqing.com/docs/manuals/LivePlayer.html#%E5%9C%A8-vue-%E4%B8%AD%E4%BD%BF%E7%94%A8"
            target="_blank"
            :icon="useRenderIcon(VideoPlay)"
            style="margin: 0 4px 5px; font-size: 16px"
          >
            Liveplayer播放器(支持MP4/WebRTC/m3u8/HLS/HTTP-FLV/WS-FLV/RTMP播放)
          </el-link>
        </span>
      </div>
    </template>
    <div class="card content-box">
      <div class="flex flex-center">
        <div style="width: 512px; height: 300px; margin: auto">
          <LivePlayer :videoUrl="mp4URL" :autoplay="false" />
        </div>
        <div style="width: 512px; height: 300px; margin: auto" class="palyer2">
          <LivePlayer ref="player2" :videoUrl="flvURL" live />
        </div>
      </div>
    </div>

    <h3>相关说明</h3>
    <ul class="flex flex-center">
      <li>
        <a
          href="https://www.liveqing.com/docs/manuals/LivePlayer.html#%E5%B1%9E%E6%80%A7-property"
          target="_blank"
          rel="noopener"
          >属性(Property)</a
        >
      </li>
      <li class="ml-[20px] mr-[20px]">
        <a
          href="https://www.liveqing.com/docs/manuals/LivePlayer.html#%E6%96%B9%E6%B3%95-medthod"
          target="_blank"
          rel="noopener"
          >方法(Medthod)</a
        >
      </li>
      <li>
        <a
          href="https://www.liveqing.com/docs/manuals/LivePlayer.html#%E4%BA%8B%E4%BB%B6-event"
          target="_blank"
          rel="noopener"
          >事件(Event)</a
        >
      </li>
    </ul>

    <h3>方法调用示例</h3>
    <ul>
      <el-button type="primary" @click="pause">暂停</el-button>
      <el-button type="warning" @click="play">播放</el-button>
    </ul>
  </el-card>
</template>

<script setup lang="ts" name="videoDemo">
import VideoPlay from "@iconify-icons/ep/video-play";
import { useRenderIcon } from "@/components/ReIcon/src/hooks";
import { computed, getCurrentInstance } from "vue";
import LivePlayer from "@liveqing/liveplayer-v3";

const mp4URL = computed(() => {
  return `${location.protocol}//${location.host}/video.mp4`;
});

const flvURL = computed(() => {
  return `${location.protocol}//${location.host}/video.flv`;
});

const instance = getCurrentInstance();

function pause() {
  (instance.refs.player2 as any).pause();
}

function play() {
  (instance.refs.player2 as any).play();
}
</script>
