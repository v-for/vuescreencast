<template>
  <div>
    <video-player  
      class="video-player-box"
      ref="videoPlayer"
      :options="playerOptions"
    ></video-player>
    <img :src="video.img" alt="">
    <h1>{{video.name}}</h1>
    <div v-html="video.desc"></div>
  </div>
</template>

<script>
import 'video.js/dist/video-js.css'
 
import { videoPlayer } from 'vue-video-player'

export default {
  components:{
    videoPlayer
  },
  computed:{
    video(){
      return this.$store.state.videos.find(vid=>vid.id == this.$route.params.id)
    },
    playerOptions(){
      return {
        language: 'id',
          playbackRates: [0.7, 1.0, 1.5, 2.0],
          sources: [{
            type: "video/mp4",
            src: "https://cdn.theguardian.tv/webM/2015/07/20/150716YesMen_synd_768k_vp8.webm"
          }],
          poster: this.video.img,
      }
    }
  }
}
</script>

<style scooped>
img{
  max-width: 50%;
}
</style>