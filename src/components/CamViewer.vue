<template>
  <div class="flex self-center">
    <div v-if="error" class="bg-white p-4 rounded-lg">
      <p>{{error}}</p>
    </div>
    <video v-else autoplay="true" class="rounded-lg" ref="videoElem"></video>
  </div>
</template>

<script>
export default {
  data() {
    return {
      error: null,
    }
  },

  mounted() {
    this.useCamera()
  },

  methods: {
    async useCamera() {
      if (navigator.mediaDevices.getUserMedia) {
        try {
          const videoStream = await navigator.mediaDevices.getUserMedia({
            video: true,
          })
          this.$refs.videoElem.srcObject = videoStream
          this.error = null
        } catch (error) {
          this.error =
            'Camera access is blocked. Please reload and enable to continue.'
          console.error('Something went wrong!', error)
        }
      } else {
        this.error = 'Browser does not support camera. Please upgrade 😅'
      }
    },
  },
}
</script>

<style>
</style>
