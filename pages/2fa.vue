<template>
    <div class="fa2">
        <h1 class="titre">Merci de vérifier votre adresse email</h1>
    
        <form class="input-groupe">
            <p class="textRenvoyer">
                Nous avons envoyé un email à {email}, merci de saisir le code reçu
                ci-dessous
            </p>
    
            <div class="otpinput">
                <p class="textInput">Entrez votre code</p>
                <v-otp-input class="custom-otp-input" model-value="------" focus-all focused color="white">
                </v-otp-input>
            </div>

            <BoutonText class="buttonLogin" textColor="var(--textcolorBlanc)" background="var(--colorbgGradientRouge)"
                borderSolid="var(--borderNone)">
                Créer un compte
            </BoutonText>
    
            <p class="textRenvoyer">Vous n'avez rien reçu ?</p>
            <p class="lienRenvoyer">Renvoyer le mail</p>
        </form>
    </div>
</template>

<script setup>
</script>

<style scoped>
.fa2 {
    background-color: black;
    height: 100vh;
}

.titre {
    color: white;
    font-family: var(--fontFamilyImpact);
    text-align: center;
    font-weight: 100;
    margin-top: 70px;
    line-height: 0.99;
}

.input-groupe {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

.textInput {
    font-size: 14px;
    color: white;
    opacity: 0.7;
    margin-top: 15px;
    margin-bottom: 0;
    text-align: left;
    font-family: var(--fontFamilyAndale);
    margin-left: 10px;
}
.custom-otp-input{
    padding: 0;
    margin-bottom: 20px;
}

.buttonLogin {
    width: 330px;
    height: 60px;
    font-family: var(--fontFamilyImpact);
}

.textRenvoyer {
    font-size: 12px;
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