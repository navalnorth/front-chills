<template>
    <div class="catalogue">
        <div class="title">
            <div>{{ text }}</div>
        </div>
        <div class="grid-container" :style="gridStyle">
            <!-- Première et deuxième ligne -->
            <div class="item"><img src='../assets/img/MYSTERES.png' alt="Mystères"></div>
            <div class="item"><img src='../assets/img/HORREUR.png' alt="Horreur"></div>
            <div class="item"><img src='../assets/img/GUERRE.png' alt="Guerre"></div>
            <div class="item"><img src='../assets/img/CRIMES.png' alt="Crimes"></div>

            <!-- Troisième ligne (affichée uniquement si `thirdRowShow` est vrai) -->
            <div v-if="thirdRowShow" class="item"><img src='../assets/img/SCI-FI.png' alt="Sci-Fi"></div>
            <div v-if="thirdRowShow" class="item"><img src='../assets/img/THRILLER.png' alt="Thriller"></div>
        </div>
    </div>

</template>
<script setup>

const props = defineProps({
    rows: {
        type: Number,
        default: 2
    },
    cols: {
        type: Number,
        default: 2 
    },
    thirdRowShow: {
        type: Boolean,
        default: false 
    },
    text: {
        type: String,
        defaut: 'N/A'
    }
})


const gridStyle = computed(() => ({
    display: 'grid',
    'grid-template-columns': `repeat(${props.cols}, 1fr)`,
    'grid-template-rows': `repeat(${props.thirdRowShow ? 3 : 2}, 1fr)`,
    'grid-column-gap': '0px',
    'grid-row-gap': '0px'
}))
</script>

<style scoped>
.catalogue {
    background-color: var(--colorbgNoir);
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-bottom: 24px;
}

.title {
    color: var(--textcolorBlanc);
    text-align: center;
    font-family: var(--fontFamilyAndale);
    font-size: 24px;
    margin-bottom: 24px;
}

.grid-container {
    color: var(--textcolorBlanc);
    background-color: var(--colorbgNoir);
}

.item img {
    width: 100%;
    height: auto;
    object-fit: cover;
}
</style>
