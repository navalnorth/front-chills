<template>
    <NavBar class="navbar"  :style="{ opacity: navbarOpacity }"/>
  <div class="bodyPadd" @scroll="scrollEvent">
    <NuxtRouteAnnouncer />

    <NuxtPage />

  </div>
</template>



<script setup>
const navbarOpacity = ref(1)

const scrollEvent = (e) => {
  const scrollTop = document.documentElement.scrollTop
  
  if (scrollTop === 0) {
    navbarOpacity.value = 1
  } else {
    navbarOpacity.value = 0.7
  }
}

onMounted(() => {
  window.addEventListener('scroll', scrollEvent)
})
</script>



<style scoped>
.bodyPadd {
  padding-top: 3px;
  background-color: rgb(0, 0, 0);
}
.navbar {
  position: fixed;
  z-index: 10000;
  width: 100%;
}
</style>