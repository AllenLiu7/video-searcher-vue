<template>
  <li class="list-group-item media" @click="onVideoClick">
    <div class="image">
      <img :src="thumbnailUrl" alt="image" />
    </div>
    <div class="media-body">
      <h4>
        {{ video.snippet.title }}
      </h4>
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    onVideoClick() {
      this.$emit("videoClick", this.video);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
.image {
  margin-right: 10px;
}
</style>