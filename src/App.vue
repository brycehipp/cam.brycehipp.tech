<template>
  <div class="h-screen w-screen">
    <div class="bg-gray-500 h-screen w-screen flex justify-center px-5">
      <CamViewer />
    </div>
  </div>
</template>

<script>
import CamViewer from './components/CamViewer.vue'

export default {
  name: 'App',
  components: {
    CamViewer,
  },
}
</script>
