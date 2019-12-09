<template>
  <div class="home">
    <h1>Videos</h1>
    <div class="video-container">
      <div v-for="video in videos" :key="video.name">
        
        <div class="video-box">
          <img :src="video.img" alt="">
          <div>
            <router-link :to="{name: 'videowatch',params:{id:video.id}}"><h3>{{ video.name }}</h3></router-link>
            <div v-html="video.desc"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import {mapState} from 'vuex'
export default {
  name: 'home',
  components: {},
  computed:{
    ...mapState({
      videos:'videos'
    })
  }
}
</script>

<style scoped lang="scss">
.video-container{
  .video-box{
    border: 1px solid black;
    border-radius: 10px;
    margin: 10px;
    padding: 10px;

    text-align: left;
    display: flex;
    justify-content: flex-start;

    img {
      max-height: 150px;
      padding: 10px;
    }
  }
}
</style>