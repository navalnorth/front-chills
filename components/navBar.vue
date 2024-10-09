<template>
    <div class="tout">
        <div @click="derouler">
            <div v-if="burger" class="iconDiv">
                <Icon name="ic:round-menu" size="30" class="icon"/>
            </div>
            <div v-else>
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
        <div class="logo">
            <img src="assets\img\logoLettres.png" width="85px">
        </div>
        <div class="navDroite">
            <div class="iconDivSearch">
                <Icon name="lsicon:search-filled" size="25" class="icon" />
            </div>
            <div class="iconDiv">
                <Icon name="mdi:account" size="30" class="icon" />
            </div>
        </div>
    </div>
</template>



<script setup>
const burger = ref(true)

const derouler = () => {
    burger.value = !burger.value
}
</script>



<style scoped>
.tout {
    display: flex;
    justify-content: space-between;
    background-color: #000000;
    padding: 15px 0;
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