<template>

    <div>
        <h1>Welcome</h1>
        <BoutonText background="var(--colorbgBlanc)" textColor="var(--textcolorRouge)" borderSolid="var(--border2Rouge)">
             Button
        </BoutonText>
        <br>
        <TextPlay background="var(--colorbgGradientJaune)" textColor="var(--textcolorNoir)" borderSolid="var(--borderNone)">
            Bouton flèche 
        </TextPlay>
        <br>
        <BoutonPlay background="var(--colorbgBlanc)" textColor="var(--textcolorRouge)" borderSolid="var(--border2Rouge)">
        </BoutonPlay>
        <br>
        <BoutonPlayVideo background="var(--colorbgGradientRouge)" textColor="var(--textcolorBlanc)" borderSolid="var(--borderNone)">
        </BoutonPlayVideo>
        <br>
        <ToggleBorder background="var(--colorbgBlanc)" backgroundRond="var(--colorbgRouge)"/>
        <br>
        <ToggleNature />
        <br>
        <ToggleBlanc />
        <br>
        <ToggleNatureBis />
        <br>
        <TextPlayVideo background="var(--colorbgGradientRouge)" textColor="var(--textcolorBlanc)" borderSolid="var(--borderNone)">
            Bouton flèche 
        </TextPlayVideo>
        <br>
    </div>

</template>

<style scoped>
div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}
</style>