<template>
    <div class="tout" :class="[!isClosed || navbarFixed ? 'navbar-fixed' : '']"
        :style="{ backgroundColor: `${navbarOpacity}` }">
        <div @click="openMenu">
            <div v-if="isClosed">
                <div class="iconDiv">
                        <Icon name="ic:round-menu" size="30" class="icon" />
                </div>
            </div>
            <div v-else>
                    <div>
                        <div class="iconDiv">
                            <Icon name="material-symbols-light:close" size="30" class="icon" />
                        </div>
                        <nav class="nav">
                            <div class="navAlignement">
                                <NuxtLink to="/">Accueil</NuxtLink>
                                <NuxtLink to="/Films">Films</NuxtLink>
                                <NuxtLink to="/Series">Series</NuxtLink>
                                <NuxtLink to="/categories">Categories</NuxtLink>
                                <NuxtLink to="/NoreSelection">Notre Sélection</NuxtLink>
                                <NuxtLink to="/NotreOffre">Notre Offre</NuxtLink>
                            </div>
                        </nav>
                    </div>
            </div>
        </div>
        <div class="logo">
            <NuxtLink to="/">
            <img src="/assets/img/logoLettres.png" width="85px">
            </NuxtLink>
        </div>
        <div class="navDroite">
            <div class="iconDivSearch">
                <Icon name="lsicon:search-filled" size="25" class="icon" />
            </div>
            <div class="iconDiv">
                <NuxtLink to="/Login">
                    <Icon name="mdi:account" size="30" class="icon" />
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<script setup>
const isClosed = ref(true)
const navbarOpacity = ref('rgba(0,0,0,1)')
const navbarFixed = ref(false)

const openMenu = () => {
    isClosed.value = !isClosed.value

    if (!isClosed.value) {
        navbarOpacity.value = "rgba(0, 0, 0, .7)"
        navbarFixed.value = true
    } else {
        navbarOpacity.value = 1
        navbarFixed.value = false
    }
}

const scrollEvent = (e) => {
    const scrollTop = document.documentElement.scrollTop

    if (scrollTop === 0) {
        navbarOpacity.value = 'rgba(0,0,0,1)'
        navbarFixed.value = false
    } else {
        navbarOpacity.value = "rgba(0, 0, 0, .7)"
        navbarFixed.value = true
    }
}

onMounted(() => {
    window.addEventListener('scroll', scrollEvent)
})
</script>

<style scoped>
.tout {
    display: flex;
    justify-content: space-between;
    background-color: #000;
    padding: 15px 0;
    position: relative;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
    transition: max-height 0.5s ease, opacity 0.5s ease;
    overflow: hidden;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
    max-height: 0;
    opacity: 0;
}

.slide-fade-enter-to,
.slide-fade-leave-from {
    max-height: 1000px;
    opacity: 1;
}

.navbar-fixed {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
}

.iconDiv {
    display: flex;
    padding: 3px 8px;
}

.icon {
    cursor: pointer;
    color: white;
}

.iconDivSearch {
    display: flex;
    padding: 6px 3px;
}

.nav {
    margin-top: 10px;
    width: 100vw;
    display: flex;
    justify-content: center;
}

.navAlignement {
    display: flex;
    align-items: flex-start;
    flex-direction: column;
    width: 100%;
    max-width: 300px;
}

.navAlignement a {
    text-decoration: none;
    color: white;
    font-family: var(--fontFamilyImpact);
    font-size: 18px;
    padding: 10px 0;
    text-align: left;
    padding-left: 10px;
}

.logo {
    position: absolute;
    display: flex;
    align-items: flex-start;
    top: 5px;
    left: 36%;
    cursor: pointer;
    padding: 15px 0;
}

.navDroite {
    display: flex;
}
</style>