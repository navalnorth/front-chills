<template>
    <div class="tout">
        <NavigationBar />

        <div class="filmPage">
            <div v-if="selectedFilm">
                <div class="filmContainer">
                    <div class="divBaniere">
                        <img :src="selectedFilm.banner" class="banniere" />
                    </div>
                    <div class="container">
                        <h1 class="titreFilm">{{ selectedFilm.title }}</h1>
                        <p class="duration">{{ selectedFilm.movie_length }} <strong>min</strong></p>
                        <p class="annee">{{ selectedFilm.year }}</p>

                        <p class="rating">{{ selectedFilm.rating }}</p>
                        <BoutonText class="buttonVoir" textColor="var(--textcolorBlanc)"
                            background="var(--colorbgGradientRouge)" borderSolid="var(--borderNone)">
                            Voir Film
                        </BoutonText>
                        <BoutonText class="boutonTrailer" textColor="var(--textcolorBlanc)"
                            background="var(--colorbgNoir)" borderSolid="var(--borderRouge)">
                            <NuxtLink to="/Register">Bande anonce</NuxtLink>
                        </BoutonText>
                    </div>
                </div>
                <div class="divDescription">
                    <p class="description">
                        {{ selectedFilm.description }}
                    </p>
                </div>
            </div>
            <div v-else>
                <div class="chargement">
                    <p>Chargement du film...</p>
                </div>
            </div>
        </div>


        <div class="card-container">
            <Card v-for="(film, index) in horrorFilms" :key="film.imdb_id" :imdbTitle="film.title"
                :imdbTime="film.movie_length" :imdbBanner="film.banner" :imdbRating="String(film.rating)"
                :imdbAge="String(-16)" />
        </div>
        <Arm />
        <Subtitle title="VOUS AIMEREZ AUSSI" :showImage="false" :centeredTitle="true" />
        <BannerFilm />
        <Footer />
    </div>
</template>



<script setup>
const route = useRoute()
const horrors = ref([]);
const horrorFilms = ref([]);
const selectedFilm = ref(null);

const fetchFilm = async () => {
    try {
        const response = await fetch(`http://localhost:3001/api/search/film/idFilm/${route.params.id}`);
        const data = await response.json();
        selectedFilm.value = data.results;
    } catch (error) {
        console.error(`Erreur lors de la récupération du film avec l'ID ${route.params.id}:`, error);
    }
};


const fetchHorrorGenres = async () => {
    try {
        const response = await fetch('http://localhost:3001/api/search/genre/Horror');
        if (!response.ok) throw new Error('Erreur lors de la récupération des genres');
        const data = await response.json();
        horrors.value = data.results ? data.results.slice(0, 11) : [];
    } catch (error) {
        console.error('Erreur lors de la récupération des données:', error);
    }
};
const fetchFilmDetails = async () => {
    const filmPromises = horrors.value.map(film =>
        fetch(`http://localhost:3001/api/search/film/idFilm/${film.imdb_id}`).then(res => res.json())
    );

    try {
        const filmResponses = await Promise.all(filmPromises);
        horrorFilms.value = filmResponses.map(response => response.results);
    } catch (error) {
        console.error('Erreur lors de la récupération des détails des films:', error);
    }
};


onMounted(async () => {
    await fetchFilm();
    await fetchHorrorGenres();
    await fetchFilmDetails();
});
</script>




<style scoped>
.tout {
    background-color: black;
}

.filmPage {
    color: white;
    text-align: center;
    display: flex;
    flex-direction: column;
    position: relative;
    margin-bottom: 40px;
}

.filmContainer {
    margin-top: 275px;
    width: 100%;
    height: 150px;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
}

.divBaniere {
    height: 70vh;
    width: 100%;
}
.banniere {
    height: 100%;
    width: 100%;
    opacity: 0.4;
    object-fit: cover;
    overflow: hidden;
}

.container {
    position: absolute;
    width: 100%;
    height: 100px
}
.rating {
    position: absolute;
    bottom: 0;
    left: 0;
    margin-left: 20px;
    margin-bottom: 190px;
    font-family: var(--fontFamilyAndale);
    z-index: 10;
    text-shadow:
        2px 2px 0px black,
        -2px 2px 0px black,
        2px -2px 0px black,
        -2px -2px 0px black;
}

.titreFilm {
    display: flex;
    flex-direction: column;
    position: absolute;
    bottom: 0;
    left: 0;
    margin-left: 20px;
    margin-bottom: 150px;
    font-family: var(--fontFamilyImpact);
    z-index: 10;
    text-shadow:
        2px 2px 0px black,
        -2px 2px 0px black,
        2px -2px 0px black,
        -2px -2px 0px black;
}

.annee {
    position: absolute;
    bottom: 0;
    left: 0;
    margin-left: 20px;
    margin-bottom: 135px;
    font-family: var(--fontFamilyAndale);
    font-size: 15px;
    z-index: 10;
    text-shadow:
        2px 2px 0px black,
        -2px 2px 0px black,
        2px -2px 0px black,
        -2px -2px 0px black;
}

.duration {
    position: absolute;
    bottom: 0;
    margin-left: 70px;
    margin-bottom: 135px;
    font-family: var(--fontFamilyAndale);
    font-size: 15px;
    z-index: 10;
    text-shadow:
        2px 2px 0px black,
        -2px 2px 0px black,
        2px -2px 0px black,
        -2px -2px 0px black;
}

.buttonVoir {
    position: absolute;
    bottom: 0;
    left: 0;
    margin-left: 220px;
    margin-bottom: 20px;
}

.boutonTrailer {
    bottom: 0;
    left: 0;
    position: absolute;
    margin-left: 20px;
    margin-bottom: 20px;
}

.boutonTrailer a {
    text-decoration: none;
    color: inherit;
}

.divDescription {
    position: relative;
    padding: 16px;
    width: 100%;

}

.description {
    color: white;
    line-height: 1.5;
    font-size: 14px;
}

.card-container {
    display: flex;
    overflow-x: auto;
    gap: 16px;
    padding: 10px;
    background-color: black;
}

.chargement {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
}

.chargement p {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>
