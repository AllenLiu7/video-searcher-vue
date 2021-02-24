<template>
  <div class="container">
    <h1>Search Video</h1>
    <SearchBar @termChange="onTermChange" />
    <div class="row">
      <VideoDetail :video="video" />
      <VideoList :videos="videos" @videoClick="onVideoClick" />
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VedioDetail";
import axios from "axios";
const API_KEY = "AIzaSyC5CzI-6oLxhMrsxmTFC6UmKSzZYkL84VI";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videos: "",
      video: null,
    };
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            part: "snippet",
            q: searchTerm,
            type: "video",
            key: API_KEY,
          },
        })
        .then((res) => {
          this.videos = res.data.items;
        });
    },
    onVideoClick(video) {
      this.video = video;
    },
  },
};
</script>

<style>
.container {
  display: flex;
  flex-direction: column;
  margin-top: 20px;
}

h1 {
  align-self: center;
}
</style>

