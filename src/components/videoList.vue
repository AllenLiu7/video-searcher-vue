<template>
  <div>Video List</div>
  {{videos.length}}
</template>

<script>
export default {
 name: 'VideoList',
 props: {
     videos: Array
 }
}
</script>

<style>

</style>