<template>
  <form @submit.prevent="submitForm">
    <fieldset>
      <legend>Lägg till en film</legend>

      <label for="title-field">Title:</label>
      <input type="text" id="title-field" class="form-control" v-model="title">

      <label for="rating-field">Betyg:</label>

      <select id="rating-field" class="form-control" v-model.number="rating">
        <option value="0">Välj betyg här...</option>
        <option v-for="n in 5" :value="n">{{n}}</option>
      </select>

      <input type="submit" class="btn btn-success mt-3" value="Spara film">

    </fieldset>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: "",
      rating: 0
    };
  },
  methods: {
    // Denna funktion körs när användaren klickar på spara film knappen. Kollar så titel och betyg inte är tomt.
    submitForm() {
      if (this.title == "") {
        alert("Du måste fylla i en titel!");
        return;
      }
      if (this.rating == 0) {
        alert("Du måste sätta ett betyg!");
        return;
      }
      this.$emit('add-movie', { title: this.title, rating: this.rating })
      this.title = "";
      this.rating = 0;
    }
  }
}
</script>
