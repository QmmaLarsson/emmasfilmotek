<template>
  <h1 class="text-6xl text-center text-red-600 m-4">FILMER</h1>
  <AddMovie @movieAdded="getMovies()" />
  <!-- Loopar igenom alla filmer och skriver ut dem en och en till Movie-komponenten, varje film skickas som en prop till Movie-komponenten -->
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
    <Movie @deleteMovie="deleteMovie(movie._id)" v-for="movie in movies" :movie="movie" :key="movie.id" />
  </div>
</template>

<script>
import Movie from "../components/Movie.vue"
import AddMovie from "@/components/AddMovie.vue";

export default {
  //Skapa dataobjekt
  data() {
    return {
      //Array som lagrar alla filmer som hämtas
      movies: []
    }
  },
  components: {
    Movie,
    AddMovie
  },
  methods: {
    //Hämtar alla filmer från en extern webbtjänst
    async getMovies() {
      //Skickar en GET-förfrågan för att hämta filmer
      const resp = await fetch("https://moment-2-backend-ramverk-qmmalarsson.onrender.com/movies");

      const data = await resp.json();

      //Fyll movies-arrayen med hämtad data
      this.movies = data;
    },
    //Tar bort en film utifrån ett angivet ID
    async deleteMovie(id) {
      //Skickar en DELETE-förfrågan för att ta bort en film
      const resp = await fetch("https://moment-2-backend-ramverk-qmmalarsson.onrender.com/movies/" + id, {
        method: "Delete",
        headers: {
          "Accept": "application/json",
          "Content-type": "application/json"
        }
      });

      //Hämta filmerna på nytt efter att filmen har tagits bort
      this.getMovies();
    }
  },
  mounted() {
    this.getMovies();
  }
}
</script>