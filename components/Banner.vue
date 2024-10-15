<template>
    <div class="banner">
        <div class="text-content">
            <p>HALLOWEEN APPROCHE...</p>
            <p class="text-content-p">Êtes-vous prêts à affronter vos pires cauchemars ?</p>
            <div class="text-content-button">
                <BoutonText class="bouton" textColor="var(--textcolorNoir)" background="var(--colorbgJaune)" borderSolid="var(--border-none)">
                    PLONGEZ DANS LA TERREUR
                </BoutonText>
            </div>
        </div>
        <div class="image-container">
            <img src="../assets/img/halloween.png" alt="Halloween">
        </div>
    </div>
    
</template>
<script setup>

</script>
<style scoped>
.banner {
    display: flex;
    justify-content: center; /* Centre le contenu */
    background-color: var(--colorbgNoir);
    max-height: 200px;
    height: 200px;
    width: 100%; 
    position: relative; /* Pour permettre aux éléments enfants de se positionner relativement */
}

.image-container {
    position: absolute;
    width: 50%; /* Modifiez ceci pour la largeur souhaitée de l'image */
    height: 100%;
    top: 0;
    right: -26%; /* Positionne le conteneur à 50% du conteneur parent */
    transform: translateX(-50%); /* Centre l'arête gauche de l'image */
}

.image-container img {
    width: 100%;
    height: 100%;
    object-fit: cover; /* Pour conserver le ratio de l'image */
   
}
.text-content {
    color:var(--textcolorBlanc);
    z-index: 1000;
    display: flex;
    justify-content: center;
    flex-direction: column;
    gap: 17px;
    width: 100%;
    padding-left: 17px;
    font-family: var(--fontFamilyAndale);
    text-transform: uppercase;
    font-size: 14px;
}


.text-content p:first-child {
    font-weight: 400;
    font-size: 24px;
    font-family: var(--fontFamilyImpact);
}
.text-content-p {
    width: 80%;
    letter-spacing: -0.3px;
}

.text-content-button { 
    width: 80%;
    margin-top: 5px;
}

</style>