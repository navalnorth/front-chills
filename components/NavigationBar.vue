<template>
    <div class="tout" :class="[!isClosed || navbarFixed ? 'navbar-fixed' : '']" :style="{ backgroundColor: `${navbarOpacity}` }">
      <div @click="openMenu">
        <div v-if="isClosed">
          <div class="iconDiv">
            <Icon name="ic:round-menu" size="30" class="icon" />
          </div>
        </div>
        <div v-else>
          <div>
            <div class="iconDiv">
              <Icon name="material-symbols-light:close" size="30" class="icon" />
            </div>
            <nav class="nav">
              <div class="navAlignement">
                <NuxtLink to="/">Accueil</NuxtLink>
                <NuxtLink to="/Films">Films</NuxtLink>
                <NuxtLink to="/Series">Series</NuxtLink>
                <NuxtLink to="/categories">Categories</NuxtLink>
                <NuxtLink to="/NoreSelection">Notre Sélection</NuxtLink>
                <NuxtLink to="/NotreOffre">Notre Offre</NuxtLink>
              </div>
            </nav>
          </div>
        </div>
      </div>
      <div class="logo">
        <NuxtLink to="/">
          <img src="/assets/img/logoLettres.png" width="85px">
        </NuxtLink>
      </div>
      <div class="navDroite">
        <div class="iconDivSearch" @click="toggleSearch">
          <Icon name="lsicon:search-filled" size="25" class="icon" />
        </div>
        <div class="iconDiv">
          <NuxtLink to="/Login">
            <Icon name="mdi:account" size="30" class="icon" />
          </NuxtLink>
        </div>
      </div>
    </div>
  
    <div :class="isSearchVisible ? 'transition transitionActive' : 'transition'">
        <div class="search-container">
          <h1>Rechercher</h1>
          <div class="search-bar">
            <div class="iconDivBar">
              <Icon name="lsicon:search-filled" size="25" class="icon" />
            </div>
            <input type="text" v-model="searchQuery" placeholder="Films, acteur...">
      
            <div v-if="filmTitle.length">
              <!-- Affiche seulement les 5 premiers films -->
              <div class="film-container">
                <div class="film" v-for="(film, index) in filmTitle.slice(0, 5)" :key="film.imdb_id">
                  <div class="film-banner">
                    <img :src="film.results.banner" alt="" />
                  </div>
                  <div>
                    <div class="film-title">{{ film.results.title }}</div>
                    <div class="film-info">
                      <div class="film-length">{{ film.results.movie_length }} min</div>
                      <div class="film-year">{{ film.results.year }}</div>
                    </div>
                  </div>
                  <div class="film-classification">{{ film.results.content_rating }}</div>
                </div>
              </div>
      
              <!-- Affiche un bouton pour voir les films restants si le nombre de films dépasse 5 -->
              <div v-if="filmTitle.length > 5">
                <button @click="showMoreFilms = !showMoreFilms" class="boutonShow">
                  {{ showMoreFilms ? 'Voir moins' : `Voir les ${filmTitle.length - 5} films supplémentaires` }}
                </button>
      
                <!-- Affiche les films restants si "Voir plus" est cliqué -->
                <div v-if="showMoreFilms" class="film-container">
                  <div class="film" v-for="(film, index) in filmTitle.slice(5)" :key="film.imdb_id">
                    <div class="film-banner">
                      <img :src="film.results.banner" alt="" />
                    </div>
                    <div>
                      <div class="film-title">{{ film.results.title }}</div>
                      <div class="film-info">
                        <div class="film-length">{{ film.results.movie_length }} min</div>
                        <div class="film-year">{{ film.results.year }}</div>
                      </div>
                    </div>
                    <div class="film-classification">{{ film.results.content_rating }}</div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
  </template>
  
<script setup>

// Contrôle de l'affichage du menu
const isClosed = ref(true)
const navbarOpacity = ref('rgba(0,0,0,1)')
const navbarFixed = ref(false)
const isSearchVisible = ref(false)
const showMoreFilms = ref(false);

const openMenu = () => {
isClosed.value = !isClosed.value

    if (!isClosed.value) {
        navbarOpacity.value = "rgba(0, 0, 0, .7)"
        navbarFixed.value = true
    } else {
        navbarOpacity.value = 1
        navbarFixed.value = false
    }
}
  
const scrollEvent = (e) => {
const scrollTop = document.documentElement.scrollTop

    if (scrollTop === 0) {
        navbarOpacity.value = 'rgba(0,0,0,1)'
        navbarFixed.value = false
    } else {
        navbarOpacity.value = "rgba(0, 0, 0, .7)"
        navbarFixed.value = true
    }
}
  
onMounted(() => {
    window.addEventListener('scroll', scrollEvent)
})

const toggleSearch = () => {
    isSearchVisible.value = !isSearchVisible.value
}

const searchQuery = ref('');
const filmTitle = ref([]);
const genre = ref(['War', 'Mystery', 'Horror', 'Crime', 'Sci-Fi', 'Thriller']);

watch(searchQuery, (newValue) => {
    if (newValue.length === 0) {

        filmTitle.value = [];
    } else if (newValue.length >= 3) {

        setTimeout(() => {
            console.log("Recherche après un délai de 2 secondes pour :", newValue);
            fetchFilmByTitle(newValue);
        }, 2000);
    }
});

  
const fetchFilmByTitle = async (title) => {
    try {
        const response = await fetch(`http://localhost:3001/api/search/film/${title}`);
        if (!response.ok) throw new Error(`Erreur lors de la récupération du film ${title}`);
        const data = await response.json();
        filmTitle.value = data.results;

        const imdbIds = filmTitle.value.map(film => film.imdb_id);
        const filmDetails = [];

        const fetchFilm = async (imdb_id) => {
        try {
            const responseFromApi = await fetch(`http://localhost:3001/api/search/film/idFilm/${imdb_id}`);
            if (!responseFromApi.ok) throw new Error(`Erreur lors de la récupération du film avec l'ID ${imdb_id}`);
            const dataFromApi = await responseFromApi.json();
            filmDetails.push(dataFromApi);
        } catch (error) {
            console.error(`Erreur lors de la récupération des détails pour le film ID ${imdb_id}:`, error);
        }
        };

        await Promise.all(imdbIds.map(imdb_id => fetchFilm(imdb_id)));
        filmTitle.value = filmDetails;

        filmTitle.value = filmTitle.value.filter(film => {
        return film.results && film.results.gen && film.results.gen.some(g => genre.value.includes(g.genre));
        });
    } catch (error) {
        console.error(`Erreur lors de la récupération des films ou des détails pour le titre ${title}:`, error);
    }
};
</script>

<style scoped>
.v-enter-active,
.v-leave-active {
  background-color: #000;
}

.v-enter-from,
.v-leave-to {
  background-color: #000;
}
.tout {
    display: flex;
    justify-content: space-between;
    background-color: #000;
    padding: 15px 0;
    position: relative;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  background-color: #000;

    transition: max-height 0.5s ease, opacity 0.5s ease;
    overflow: hidden;
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  background-color: #000;

    max-height: 0;
    opacity: 0;
}

.slide-fade-enter-to,
.slide-fade-leave-from {
  background-color: #000;

    max-height: 1000px;
    opacity: 1;
}

.navbar-fixed {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 1000;
}

.iconDiv {
    display: flex;
    padding: 3px 8px;
}

.icon {
    cursor: pointer;
    color: white;
}

.iconDivSearch {
    display: flex;
    padding: 6px 3px;
}

.nav {
    margin-top: 10px;
    width: 100vw;
    display: flex;
    justify-content: center;
}

.navAlignement {
    display: flex;
    align-items: flex-start;
    flex-direction: column;
    width: 100%;
    max-width: 300px;
}

.navAlignement a {
    text-decoration: none;
    color: white;
    font-family: var(--fontFamilyImpact);
    font-size: 18px;
    padding: 10px 0;
    text-align: left;
    padding-left: 10px;
}

.logo {
    position: absolute;
    display: flex;
    align-items: flex-start;
    top: 5px;
    left: 36%;
    cursor: pointer;
    padding: 15px 0;
}

.navDroite {
    display: flex;
}


.search-container {
    text-align: center;
    color: #fff;
    background: var(--colorbgNoir);
    font-size: 12px;
    letter-spacing: 1px;
    font-family: var(--fontFamilyImpact);
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: relative;
}

.search-bar {
    display: inline-block;
}

.search-bar input {
    width: 300px;
    padding: 10px 15px 10px 50px;
    border: none;
    outline: none;
    font-size: 16px;
    background-color: #333;
    color: #aaa;
    margin-bottom: 8px;
}

.search-bar input::placeholder {
    color: #aaa;
}

/* Positionner l'icône dans l'input */
.iconDivBar {
    position: absolute;
    left: 55px;
    top: 62px;
    transform: translateY(-50%);
}

.icon {
    color: #aaa;
    font-size: 20px; /* Ajuster la taille de l'icône si nécessaire */
}

.film-container {
    margin-top: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    background-color: var(--colorbgNoir);
}

.film {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 300px;
    width: 100%;
    padding: 5px;
    background-color: #333;
    cursor: pointer;
    margin-bottom: 8px;

}

.film-info {
    display: flex;
    justify-content: space-between;
    gap: 20px;
    font-family: var(--fontFamilyAndale);
}

.film-banner {
    width: auto;
    height: 50px;
}

.film-banner img {
    width: 100%;
    height: 100%;
}

.film-title {
    font-family: var(--fontFamilyImpact);
    font-size: 12px;

}
.film-lenght{

}
.film-gen{

}
.film-year{

}
.film-classification {

}

.boutonShow {
    margin-bottom: 8px;
}

.transition {
  height: 0px;
  transition: .3s;
}

.transitionActive {
  height: 87px;
}
</style>
