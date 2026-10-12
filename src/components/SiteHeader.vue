<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
const menuOpen = ref(false)
const menuButton = ref(null)
function onNavigation(event) {
  if (event.target.closest('a')) menuOpen.value = false
}
function onKeydown(event) {
  if (event.key === 'Escape' && menuOpen.value) {
    menuOpen.value = false
    menuButton.value?.focus()
  }
}
onMounted(() => document.addEventListener('keydown', onKeydown))
onBeforeUnmount(() => document.removeEventListener('keydown', onKeydown))
</script>

<template>
<header class="header"><a class="brand" href="#home" aria-label="禾间小馆首页"><span class="brand-seal">禾</span><span>禾间小馆<small>HEJIAN RESTAURANT</small></span></a><button id="menu-toggle" aria-controls="site-nav" :aria-expanded="menuOpen" :aria-label="menuOpen ? '关闭导航' : '打开导航'" ref="menuButton" @click="menuOpen = !menuOpen">☰</button><nav :class="{ 'is-open': menuOpen }" @click="onNavigation" id="site-nav" aria-label="主导航"><a href="#home">首页</a><a href="#menu">招牌菜品</a><a href="#story">小馆故事</a><a href="#visit">到店指南</a></nav><a class="header-cta" href="#visit">来禾间坐坐 <span>↗</span></a></header>
</template>
