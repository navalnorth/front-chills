<template>
    <NavBar class="navbar"  :style="{ opacity: navbarOpacity }"/>
  <div class="bodyPadd" @scroll="scrollEvent">
    <NuxtRouteAnnouncer />

    <NuxtPage />

    <div class="div">
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Eveniet iste quam porro sint consequuntur odit. Eaque,
      explicabo? Minima nostrum atque officia sequi distinctio quo labore rem quasi adipisci. Alias, autem.
      Lorem ipsum, dolor sit amet consectetur adipisicing elit. Quos odit provident perspiciatis, maxime nihil nesciunt
      dolor, dolore itaque error voluptas iste tempore facilis incidunt. Tempore aspernatur libero cumque ipsam
      veritatis!
    </div>

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
.div {
  height: 1000px;
  width: 100%;
  color: white;
}
</style>