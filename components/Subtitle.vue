<template>
    <div class="subtitle" :style="backgroundStyle">
        <p>
            {{ props.title }}
        </p>
    </div>
</template>

<script setup>

import griffeTitre from '@/assets/img/griffeTitre.png';

const props = defineProps({
    title: {
        type: String,
        default: 'N/A'
    },
    showImage: {
        type: Boolean,
        default: false
    },
    centeredTitle: {
        type: Boolean,
        default: false
    }

});

const backgroundStyle = computed(() => {
    return {
        backgroundImage: props.showImage ? `url(${griffeTitre})` : 'none',
        backgroundSize: 'cover',
        backgroundPosition: '-50px center',
        backgroundRepeat: 'no-repeat',
        height: '40px',
        color: 'var(--textcolorBlanc)',
        fontFamily: 'var(--fontFamily)',
        paddingLeft: '17px',
        position: 'relative',
        overflow: 'visible',
        display: 'flex',
        justifyContent: props.centeredTitle ? 'center' : 'none',
        backgroundColor: 'black',
    };
});

</script>

<style scoped>
.subtitle {
    display: flex;
}
.subtitle p {
    margin: 0;
    position: relative;
    display: flex;
    align-items: center;

}
</style>
