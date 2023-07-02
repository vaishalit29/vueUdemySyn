<template>

    <ul class="list-group col-md-4">
        <VideoListItem 
        v-for="video in videos"
        :video="video"
        v-bind:key="video.etag"
        @videoSelect="onVideoSelect"
        >
   </VideoListItem></ul>

</template>
<script>
import VideoListItem from './VideolListItem.vue';
export default{
    name:'VideoList',
    components:{
        VideoListItem
    },
    props:{
        videos:Array
    },
    methods:{
        onVideoSelect(video){
            this.$emit('videoSelect', video)
    }
}
   
}
</script>