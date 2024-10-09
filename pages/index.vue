<template>

    <div>
        <div class="ban">
            <div class="slider-container">
                <div class="slider-tracker" :style="{ transform: `translateX(-${currentIndex * 100}%)` }">
                    <img v-for="name in pictureName" :src="`_nuxt/assets/img/${name}.jpg`" class="image" >
                </div>
            </div>
            
            
            <div class="overlay">
                <p class="textBan">
                    ENTREZ<br />SI VOUS L'OSEZ...<br /><span class="textP">LES FRISSONS SONT GARANTIS</span>
                </p>
                <BoutonText class="bouton" textColor="var(--textcolorNoir)" background="var(--colorbgJaune)"
                    borderSolid="var(--border-none)">
                    PLONGEZ DANS LA TERREUR
                </BoutonText>
                <div class="dots">
                    <div v-for="dot, index in pictureName" :class="checkDotClass(index)"></div>
                </div>
            </div>
        </div>
        <button @click="nextSlide" class="nextButton">
            rthryjhty
        </button>
        <button @click="prevSlide" class="prevButton">
            rthryjhty
        </button>
    </div>

</template>



<script setup>
const pictureName = ref([
    'ban1',
    'ban2',
    'ban3',
    'ban4',
    'ban5',
]);

const currentIndex = ref(0);

const nextSlide = () => {
    if (currentIndex.value == pictureName.value.length - 1) {
        currentIndex.value = 0
    } else {
        currentIndex.value++
    }
}
const prevSlide = () => {
    if (currentIndex.value !== 0) {
        currentIndex.value--
    } else {
        return
    }
}

const slide = () => {
    setInterval(() => {        
        if (currentIndex.value == pictureName.value.length - 1) {
            currentIndex.value = 0;
        } else {
            currentIndex.value++;
        }
    }, 5000);
}

const checkDotClass = (index) => {
    if (index == currentIndex.value) {
        return 'activeDot';
    }
    else {
        return 'dot';
    }
}

onMounted(() => {
    slide();
})
</script>



<style scoped>
.ban {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: flex-end;
}

.slider-container {
    display: flex;
    overflow: hidden;
    height: 600px;
    width: 100%;
}
.slider-tracker {
    display: flex;
    transition: .5s;
}
.image {
    width: 100%;
    object-fit: cover ;
    flex-shrink: 0;
}

.nextButton {
    width: 50px;
    height: 50px;
    background-color: red;
    position: absolute;
}

.overlay {
    position: absolute;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 32px;
    gap: 30px
}
.textBan {
    color: white;
    text-align: center;
    font-size: 22px;
    font-family: var(--fontFamilyAndale);
    opacity: 0.7;
    margin: 0;
    line-height: 18px;
}
.textP {
    font-size: 18px
}
.dots {
    display: flex;
    gap: 4px;
}
.dot, .activeDot {
    background-color: #D9D9D966;
    height: 6px;
    width: 6px;
    border-radius: 50%;
}
.activeDot {
    background-color: #D9D9D9CC;
}
</style>