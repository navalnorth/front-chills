<template>
    <div class="grid-container">
        <div class="item item1"><Card /></div>
        <div class="item item2">
            <div class="item2-title">
                <p>TITRE DE FILM \/</p>
            </div>
            <div class="item2-info">
                <p>Durée <span> | </span>Réalisateur</p>
            </div>
            <div class="item2-desc">
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda eveniet distinctio commodi nobis ad maiores omnis explicabo mollitia! Odio, repellendus. Dolor, numquam eos accusamus ea nihil non nisi nulla consequatur adipisci dignissimos tempora, esse beatae magni animi illum sit eius dolorem? Incidunt odio sequi, magnam maxime placeat nihil quaerat similique.</p>
            </div>
        </div>
        <div class="item item3">
            <BoutonText class="bouton" textColor="var(--textcolorBlanc)" background="var(--colorbgNoir)" borderSolid="var(--borderRouge)">
                BANDE ANNONCE
            </BoutonText>
        </div>
        <div class="item item4">
            <BoutonText class="bouton" textColor="var(--textcolorBlanc)" background="var(--colorbgRouge)" borderSolid="var(--borderRouge)">
                VOIR LE FILM
            </BoutonText>
        </div>
    </div>
</template>

<script setup>


</script>

<style scoped>
.grid-container {
    display: grid;
    grid-template-columns: 1fr 1fr; 
    grid-template-rows: auto auto; 
    gap: 10px; 
    padding: 20px;
    background-color: var(--colorbgNoir); 
}

.item {
    color: white;
    display: flex;
    flex-direction: column;
}

.item1, .item2 {
    height: 233px;
    font-size: 10px;
    font-family: var(--fontFamilyAndale);
}

.item1 {
    display: flex;
    align-items: center;
}

.item2-title, .item2-info {
    text-align: left; /* Aligne le texte à gauche */
}
.item2-title {
    font-size: 14px;
}
.item2-info {
    margin-bottom: 20px;
    font-size: 10px;
}
.item2-title p,
.item2-info p {
    margin: 0; /* Supprime les marges par défaut */
}

.item2-desc {
    font-family: var(--fontFamilyMention);
}

.item3, .item4 {
    min-height: 50px;

    display: flex;
    align-items: center;
}

.bouton {
    font-size: 16px;
    padding: 10px 4px;
    width: 100%;
}
</style>
