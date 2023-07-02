<template>
  <div class="container">
   
  <SearchBox class ="mt-2" label="Search-Box" @termChange ="onTermChange"/>
  <div class="row">
    <VideoDetails :video="selectedVideo"/>
  <VideoList :videos ="videos"  @videoSelect="onVideoSelect"/>
  </div>
 
 
  </div>
</template>

<script>
import SearchBox from './components/SearchBox.vue';
const API_KEY = "AIzaSyDGicFFi3lJYqdl50LmB8WTdlI1gOUuhzQ";
import axios from "axios";
import VideoList from  './components/VideoList.vue';
import VideoDetails from './components/VideoDetails.vue';


export default {
  name: 'App',
  components: {
    SearchBox,
    VideoList,
    VideoDetails
  },
  data(){
     return {
      videos:[],
      selectedVideo:null,
     } 
  },
  methods:{
    onVideoSelect(video){
      console.log(video, "video")
      this.selectedVideo = video;
      console.log( this.selectedVideo , "video1")
    },
    onTermChange(searchTerm){
      // console.log(searchTerm)
      axios.get('https://www.googleapis.com/youtube/v3/search',{
        params : {
        key : API_KEY,
        type:'video',
        part:'snippet',
        q:`${searchTerm}`
        }
      }).then((res)=>{
        this.videos = res.data.items
        // console.log(this.videos)
      })
    }
  }
}
</script>

<style>

</style>
