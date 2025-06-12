<template>
  <div>
    <h2>Filmer</h2>

    <ul id="movies">
      <li v-for="(movie, index) in movies" :key="index">
        {{movie.title}}
        <img :src="deleteIcon" alt="Radera ikon" @click="$emit('delete-movie', index)" />
        <img
          :src="starIcon"
          alt="Betyg ikon"
          v-for="n in movie.rating"
          :key="n"
        />
      </li>
    </ul>

    <button class="btn btn-primary mt-3" @click="$emit('sort-alpha')">Sortera i alfabetisk ordning</button>
    <button class="btn btn-warning mt-3" @click="$emit('sort-rating')">Sortera efter betyg</button>
    
  </div>
</template>

<script>
import deleteIcon from '../assets/delete.png';
import starIcon from '../assets/star.png';

export default {
  props: ['movies'],
  data() {
    return {
      deleteIcon,
      starIcon
    };
  }
}
</script>
