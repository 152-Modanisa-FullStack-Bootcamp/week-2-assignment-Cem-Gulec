<template>
  <div>
    <Header/>
    <div id="video-list-container">
      <FavoriteVideo
          v-for="video in filteredVideos"
          :video="video"
          :key="video.id">
      </FavoriteVideo>
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header";
import FavoriteVideo from "@/components/FavoriteVideo";
import axios from "axios";
export default {
  name: "FavoritesPage",
  components: {
    FavoriteVideo,
    Header
  },
  data() {
    return {
      videos: []
    }
  },
  computed:{
    filteredVideos(){
      return this.videos.filter(video => video.favorite === true)
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

</style>