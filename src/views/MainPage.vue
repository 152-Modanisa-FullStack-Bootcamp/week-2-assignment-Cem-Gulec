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
import Header from "@/components/Header";
import Video from "@/components/Video";
import {  mapGetters } from "vuex";
export default {
  name: "MainPage",
  components: {
    Header,
    Video
  },
  computed: {
    ...mapGetters({
      videos: "getVideoInfo"
    })
  },
  mounted(){
    this.$store.dispatch("callVideoInfo");
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