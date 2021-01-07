<template>
  <div>
      <SearchBar @termChange='onTermChange'/>
      <VideoList :videos='videos'/>
      
  </div>
</template>

<script>
import SearchBar from './components/search-bar'
import VideoList from './components/videoList'
import axios from 'axios'
const API_KEY = "AIzaSyC5CzI-6oLxhMrsxmTFC6UmKSzZYkL84VI"

export default {
    name: 'App',
    components: {
        SearchBar,
        VideoList
        
    },
    data(){
        return {
            videos: ''
        }
    },
    methods: {
        onTermChange(searchTerm){
            axios.get('https://www.googleapis.com/youtube/v3/search', {
                params: {
                    part:'snippet',
                    q:searchTerm,
                    type:'video',
                    key: API_KEY
                }
            }).then(res=>{this.videos = res.data.items})
        }
    }
  
}
</script>

<style>

</style>

