<template>
  <div>
    <Header/>
    <div id="video-list-container">
      <Video
          v-for="video in videos"
          :video="video"
          :key="video.id">
      </Video>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header";
import Video from "@/components/Video";
export default {
  name: "MainPage",
  components: {
    Header,
    Video
  },
  data() {
    return {
      videos: []
    }
  },
  async mounted(){
    const _path = "https://my-json-server.typicode.com/modanisa/bootcamp-video-db/videos";
    const { data } = await axios.get(_path);
    this.videos = data;
    console.log(data);
  }
}
</script>

<style scoped>
#video-list-container{
  display: flex;
  flex-wrap: wrap;
  width: 1600px;
  margin-left: 30px;
  margin-top: 20px;
}
</style>