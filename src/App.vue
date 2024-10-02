<script>
export default {
  data() {
    return {
      videoRef: null, // la referencia se inicializa como null
      isMuted: false, // estado inicial del audio
    };
  },
  methods: {
    toggleMute() {
      if (this.videoRef) {
        this.isMuted = !this.isMuted;
        this.videoRef.muted = this.isMuted;
      }
    }
  },
  mounted() {
    // Obtenemos la referencia al video una vez que el componente esté montado
    this.videoRef = this.$refs.videoRef;
    // this.videoRef.addEventListener('canplaythrough', this.onVideoLoaded);
  }
  // beforeDestroy() {
  //   // Remover el listener cuando el componente sea destruido
  //   if (this.videoRef) {
  //     this.videoRef.removeEventListener('canplaythrough', this.onVideoLoaded);
  //   }
  // }
};
</script>

<template>
  <main class="container">
    <!-- <div v-if="isLoading" class="spinner-overlay">
      <div class="spinner"></div>
    </div> -->
    <video autoplay muted loop ref="videoRef">
      <source src="./assets/video/Video_3536c1.mp4" type="video/mp4">
    </video>
    <button @click="toggleMute" class="mute-btn">
      <i :class="isMuted ? 'fa-solid fa-volume-high' : 'fa-solid fa-volume-xmark'"></i>
    </button>
  </main>
</template>

<style scoped>
.container{
  width:100%;
  min-height: 100vh;
  position:relative;
}
video{
  position: absolute;
  top:0;
  left:0;
  object-fit: cover;
  width:100%;
  height:100%;
}
.mute-btn {
  position: absolute;
  top: 0;
  right: 20px;
  background-color: transparent;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  font-size: 24px;
}
@media (min-width: 768px) and (max-width: 991px){
  video{
    max-width:1200px;
    height: 100%;
    object-fit: cover;
  }
}
@media (min-width: 1025px) {
  video{
    width:100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
