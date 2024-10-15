<template>
<div class="profil">
    <NavBar />

    <h1 class="titre">MON COMPTE</h1>

    <div class="navCompte">
        <button @click="modifierProfil" class="lienCompte">
            Modifier profil
        </button>
        <button @click="modifierMdp" class="lienCompte">
            Modifier mot de passe
        </button>
        <button @click="supprimerCompte" class="lienCompte">
            Supprimer compte
        </button>
    </div>
</div>
</template>



<script setup>


</script>


<style scoped>
.profil {
    background-color: black;
    height: 100vh;
}

.titre {
    color: white;
    font-family: var(--fontFamilyImpact);
    text-align: center;
    font-weight: 100;
    margin-top: 10px;
}
</style>