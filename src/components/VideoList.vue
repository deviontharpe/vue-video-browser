<template>
<ul class="list-group">
  <VideoListItem 
  v-for="video in videos"
  :video="video"
  :key="video.etag">
  </VideoListItem>
</ul>
</template>


<script>
import VideoListItem from "./VideoListItem";
export default {
  name: "VideoList",
  components: {
    VideoListItem
  },
  props: ["videos"]
};
</script>


<style>
ul {
  margin-top: 50px;
  width: 40%;
  float: right;
}
</style>
