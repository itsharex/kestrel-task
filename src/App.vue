<template>
  <el-config-provider :locale="locale">
    <router-view />
  </el-config-provider>
</template>
<script setup>
import { onMounted } from 'vue'
import { invoke } from '@tauri-apps/api/tauri'
import locale from 'element-plus/dist/locale/zh-cn.mjs'
onMounted(() => {
  // window.addEventListener('contextmenu', (e) => e.preventDefault(), false)
  document.addEventListener('DOMContentLoaded', () => {
    // This will wait for the window to load, but you could
    // run this function on whatever trigger you want
    setTimeout(() => {
      invoke('close_splashscreen')
    }, 1000)
  })
})
</script>
