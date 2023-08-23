<template>
    <div>
      <div ref="dp0" />
    </div>
  </template>
  
  <!-- <script>
  import { onMounted } from 'vue'
    export default {
      // 获取传值
      props: ['src'],
      setup(props) {
      // setup() 接收 props 作为第一个参数
      console.log(props.src)
    }
      mounted() {
        this.$nextTick(() => {
          import("dplayer").then(({ default: DPlayer }) => {
            this.dp = new DPlayer({
              container: this.$refs.dp0,
              video: {
                url: props.src,
              },
            });
          });
        });
      },
      beforeUnmount() {
        this.dp.destroy();
      },
    };
  </script> -->
  
  <script setup>
  import { onMounted, onBeforeUnmount, nextTick} from 'vue'
  
  // 获取传值
  const props = defineProps(['src'])
  console.log(props.src)
  
  // 渲染播放器
  onMounted(() => {
    nextTick(() => {
          import("dplayer").then(({ default: DPlayer }) => {
            this.dp = new DPlayer({
              container: this.$refs.dp0,
              video: {
                url: props.src,
              },
            });
          });
        });
  })
  
  // 销毁播放器
  onBeforeUnmount(()=>{
    this.dp.destroy();
  })
  
  </script>