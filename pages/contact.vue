<template>
    <div class="contact">
        <h1 class="titre">Contactez-nous !</h1>

    <form class="input-groupe">
        <div>
            <Icon name="ph:user-light" size="30" class="iconInput" />
            <input class="input" type="text" placeholder="Nom et Prénom">
        </div>
        <div>
            <Icon name="ic:outline-email" size="30" class="iconInput" />
            <input class="input" type="text" placeholder="Indiquez votre email" >
        </div>

        <div class="inputGoupList">
           <div class="divLabel">
            <label for="pet-select" class="labelListe">Vous nous contactez pour:</label>
           </div>
            <select name="pets" id="pet-select" class="inputListe">
                <option class="optionList">Choisir la raison</option>
                <option class="optionList">Dog</option>
                <option class="optionList">Cat</option>
                <option class="optionList">Hamster</option>
                <option class="optionList">Parrot</option>
                <option class="optionList">Spider</option>
                <option class="optionList">Goldfish</option>
            </select>
        </div>

        <div class="checkbox-container">
            <label class="content">
                <input type="checkbox">
                <span class="checkmark"></span>
                <p class="seSouvenir">En créant ce compte, j'accepte les conditions générales d'utilisation</p>
            </label>
        </div>
        <BoutonText class="buttonLogin" textColor="var(--textcolorBlanc)" background="var(--colorbgGradientRouge)"
            borderSolid="var(--borderNone)">
            Envoyer un message
        </BoutonText>

    </form>
    </div>
</template>



<script setup>

</script>



<style scoped>
.contact {
    background-color: black;
    height: 100vh;
}
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

.iconInput {
    color: white;
    opacity: 0.6;
    position: absolute;
    margin-left: 10px;
    margin-top: 8px;
}

.input {
    width: 300px;
    padding: 16px 14px;
    margin-bottom: 10px;
    border: 1px solid white;
    background-color: black;
    border-radius: 4px;
    color: white;
    font-family: var(--fontFamilyAndale);
    text-align: center;
}
.input:focus {
    outline: 1px solid white;
}
.input::placeholder {
    text-align: center;
    font-family: var(--fontFamilyAndale);
    color: white;
    opacity: 0.6;
    font-size: 13px;
}

.inputGoupList {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
.inputGoupList select option {
    width: 1000px;
}
.inputGoupList select {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    text-align: left;
}

.optionList {
    font-size: 18px; /* Taille de police des options */
    padding: 10px; /* Marges internes des options pour les agrandir */
}
.divLabel {
    width: 100%;
    margin-bottom: 2px;
}
.labelListe {
    font-family:var(--fontFamilyAndale);
    font-size: 18px;
    color: white;
    text-align: left;
}
.inputListe {
    width: 330px;
    padding: 14px 14px;
    margin-bottom: 10px;
    border: 1px solid white;
    background-color: black;
    border-radius: 4px;
    color: white;
    font-family: var(--fontFamilyAndale);
    text-align: center;
}

.mdp a {
    text-align: center;
    font-family: var(--fontFamilyAndale);
    color: white;
    font-size: 16px;
    text-decoration: underline;
    opacity: 0.7;
}

.checkbox-container {
    display: flex;
    margin-top: 10px;
    width: 300px;
}

.content {
    display: flex;
    align-items: center;
    position: relative;
    cursor: pointer;
    font-size: 22px;
}

.content input {
    position: absolute;
    opacity: 0;
    cursor: pointer;
}

.checkmark {
    position: relative;
    height: 16px;
    width: 30px;
    background-color: #000000;
    border: 1px solid white;
    border-radius: 5px;
    margin-right: 10px;
}

.content input:checked~.checkmark {
    background-color: #ee3902;
}

.checkmark:after {
    content: "";
    position: absolute;
    display: none;
}

.content input:checked~.checkmark:after {
    display: block;
}

.content .checkmark:after {
    left: 5px;
    top: 2px;
    width: 3px;
    height: 6px;
    border: solid white;
    border-width: 0 2px 2px 0;
    transform: rotate(45deg);
}

.seSouvenir {
    color: white;
    opacity: 0.7;
    font-size: 13px;
    font-family: var(--fontFamilyAndale);
}

.buttonLogin {
    width: 330px;
    height: 60px;
    font-family: var(--fontFamilyImpact);
}
</style>
