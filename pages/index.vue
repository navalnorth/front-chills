<template>

    <div>
        <h1>Welcome</h1>
        <BoutonText background="var(--colorbg2)" textColor="var(--textcolor2)" borderSolid="var(--border2)">
             Button
        </BoutonText>
        <br>
        <TextPlay background="var(--colorbg5)" textColor="var(--textcolor3)" borderSolid="var(--border1)">
            Bouton flèche 
        </TextPlay>
        <br>
        <BoutonPlay background="var(--colorbg2)" textColor="var(--textcolor2)" borderSolid="var(--border2)">
        </BoutonPlay>
        <br>
        <BoutonPlayVideo background="var(--colorbg1)" textColor="var(--textcolor1)" borderSolid="var(--border1)">
        </BoutonPlayVideo>
        <br>
        <TextPlayVideo background="var(--colorbg1)" textColor="var(--textcolor1)" borderSolid="var(--border1)">
            Bouton flèche 
        </TextPlayVideo>
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