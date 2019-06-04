<template>
  <div class="camera">
    <video autoplay class="feed"></video>
    <button class="snap" @click="$emit('takePicture')">SANP</button>
  </div>
</template>

<script>
export default {
  name: "Camera",
  methods: {
    init() {
      if (
        "mediaDevices" in navigator &&
        "getUserMedia" in navigator.mediaDevices
      ) {
        let constraints = {
          video: {
            width: {
              min: 640,
              ideal: 1280,
              max: 1920
            },
            height: {
              min: 360,
              ideal: 720,
              max: 1080
            }
          }
        };
        navigator.mediaDevices.getUserMedia(constraints).then(stream => {
          const videoPlayer = document.querySelector("video");
          videoPlayer.srcObject = stream;
          videoPlayer.play();
        });
      }
    }
  },
  beforeMount() {
    this.init();
  }
};
</script>

<style lang="scss" scoped>
.camera {
  width: 100vw;
  height: 100vh;
  padding: 25px;
  box-sizing: border-box;
  .feed {
    width: 100%;
    max-width: 1280px;
    margin: 0 auto;
    display: block;
    background-color: #171717;
    box-shadow: 6px 6px 12px 0px rgba(0, 0, 0, 0.35);
  }

  .snap {
    width: 75px;
    height: 75px;
    border-radius: 50%;
    background-color: transparentize($color: #ffce00, $amount: 0.5);
    border: 1px solid #171717;
    outline: none;
    margin: 0 auto;
    display: block;
    margin-top: 15px;
    cursor: pointer;
    &:hover {
      background-color: #ffce00;
    }
    &:active {
      background-color: darken($color: #ffce00, $amount: 15);
    }
  }
}
</style>
