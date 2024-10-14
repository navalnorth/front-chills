<template>
    <h1 class="titre">Merci de vérifier votre adrese email</h1>

    <form class="input-groupe">
        <p class="textRenvoyer">Nous avons envoyé un email à {email}, merci de saisir le code reçu ci-dessous</p>

        <div>
            <p class="textRenvoyer">Entrez votre code</p>
        </div>
        
        <BoutonText class="buttonLogin" textColor="var(--textcolorBlanc)" background="var(--colorbgRouge)"
            borderSolid="var(--borderNone)">
            Créer un compte
        </BoutonText>

        <p class="textRenvoyer">Vous n'avez rien reçu ?</p>
        <p class="lienRenvoyer">Renvoyer le mail</p>
    </form>
</template>



<script setup>

</script>



<style scoped>
.titre {
    color: white;
    font-family: var(--fontFamilyImpact);
    text-align: center;
    font-weight: 100;
    margin-top: 70px;
}

.input-groupe {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.otp-input {
    margin-top: 20px;
    justify-content: center;
  }

.buttonLogin {
    width: 330px;
    height: 60px;
    font-family: var(--fontFamilyImpact);
}

.textRenvoyer {
    font-size: 14px;
    color: white;
    opacity: 0.7;
    margin-top: 15px;
    margin-bottom: 0;
    text-align: center;
    font-family: var(--fontFamilyAndale);
}
.lienRenvoyer {
    font-size: 14px;
    color: white;
    opacity: 0.7;
    font-family: var(--fontFamilyAndale);
    text-decoration: underline;
    margin: 0;
}
</style>
