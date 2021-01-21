<template>
  <ul class="list-group col">
    <VideoListItem
      v-for="video in videos"
      v-bind:video="video"
      v-bind:key="video.etag"
      @videoClick="onVideoClick"
    />
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  props: {
    videos: Array,
  },
  components: { VideoListItem },
  methods: {
    onVideoClick(vedio) {
      this.$emit("videoClick", vedio);
    },
  },
};
</script>

<style>
</style>