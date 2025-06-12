<template>
  <div class="wrapper">
    <h1>Min filmlista</h1>
    <movieForm @add-movie="addMovie" />

    <hr />
    
    <list
      :movies="movies"
      @delete-movie="deleteMovie"
      @sort-alpha="orderByAlphaButton"
      @sort-rating="orderByGradeButton"
    />
  </div>
</template>

<script>
import movieForm from './components/movieForm.vue'
import list from './components/list.vue'

export default {
  components: { movieForm, list },
  data() {
    return {
      movies: []
    }
  },
  methods: {
    // Tillåter användaren att lägga till en ny film i listan, ge titel och betyg. Ger även felmeddelande om titel eller betyg inte är ifyllt
    addMovie(movie) {
      this.movies.push(movie);
    },
    // Denna körs när användaren klickar på radera knappen och raderar filmen från listan
    deleteMovie(index) {
      this.movies.splice(index, 1);
    },
    // Denna körs när användaren klickar på sortera alfabetisk ordning knappen och sorterar då filmerna i alfabetisk ordning
    orderByAlphaButton() {
      this.movies.sort(function (a, b) {
        return a.title.localeCompare(b.title);
      });
    },
    // Denna körs när användaren klickar på sortera efter betyg knappen och sorterar då filmerna efter betyg
    orderByGradeButton() {
      this.movies.sort(function (a, b) {
        if (a.rating > b.rating) return -1;
        if (a.rating < b.rating) return 1;
        return 0;
      });
    }
  }
}
</script>

<style>
@import './style.css';
</style>
