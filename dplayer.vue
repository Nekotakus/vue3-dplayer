<template>
    <div>
      <div ref="dp0" />
    </div>
  </template>
  
<script>  
  import { onMounted } from 'vue'

  export default {
    mounted() {
      this.$nextTick(() => {
        import("dplayer").then(({ default: DPlayer }) => {
          this.dp = new DPlayer({
            container: this.$refs.dp0,
            video: {
              url: "video link",
              thumbnails: "thumbnail picture",
            },
          });
        });
      });
    },
    beforeUnmount() {
      this.dp.destroy();
    },
  };
</script>