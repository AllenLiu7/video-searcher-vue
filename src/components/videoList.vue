<template>
  <ul>
    <VideoListItem v-for="video in videos" v-bind:video="video" v-bind:key="video.etag"/>
   
  </ul>
</template>

<script>
import VideoListItem from './VideoListItem'

export default {
 name: 'VideoList',
 props: {
     videos: Array
 },
 components: {VideoListItem
}}
</script>

<style>

</style>