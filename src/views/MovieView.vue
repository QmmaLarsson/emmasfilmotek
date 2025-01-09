<script>
import Movie from "../components/Movie.vue"
import AddMovie from "@/components/AddMovie.vue";

export default {
  //Dataobjekt
  data() {
    return {
      movies: []
    }
  },
  components: {
    Movie,
    AddMovie
  },
  methods: {
    async getMovies() {
      const resp = await fetch("https://moment-2-backend-ramverk-qmmalarsson.onrender.com/movies");

      const data = await resp.json();

      this.movies = data;
    },
    async deleteMovie(id) {
      const resp = await fetch("https://moment-2-backend-ramverk-qmmalarsson.onrender.com/movies/" + id, {
        method: "Delete",
        headers: {
          "Accept": "application/json",
          "Content-type": "application/json"
        }
      });

      const data = await resp.json();
      this.getMovies();
    }
  },
  mounted() {
    this.getMovies();
  }
}
</script>

<template>
  <h1 class="text-6xl text-center text-red-600 m-4">FILMER</h1>
  <!-- Loopar igenom objekten och skriver ut dem en och en -->
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
    <Movie @deleteMovie="deleteMovie(movie._id)" v-for="movie in movies" :movie="movie" :key="movie.id" />
  </div>
  <AddMovie @movieAdded="getMovies()" />
</template>