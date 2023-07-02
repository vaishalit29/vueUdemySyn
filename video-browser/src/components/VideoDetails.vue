<template>
    <div class = " col-md-8" v-if="video" >
        <div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" :src="videoUrl"></iframe>
</div>
<div class="details">
    <h4>{{video.snippet.title}}</h4>
    <p>{{video.snippet.description}}</p>
</div>
</div>
</template>
<script>
export default{
    name:'VideoDetails',
    props:['video'],
    computed: {
        videoUrl() {
            const videoId = this.video.id.videoId;
            // const {videoId} = this.video.id      es6 syntex
            // return 'https://www.youtube.com/embed/'+ videoId;  es5 syntex
           return  `https://www.youtube.com/embed/${videoId}`;
        }
    }
}
</script>
<style scoped>
.details{
    margin-top: 20px;
    padding: 10px;
    border:1px solid #ddd;
    border-radius: 4px;
}
</style>