<script>
export default {
    data() {
        return {
            name: "",
            year: "",
            completed: false,
        }
    },
    emits: ["movieAdded"],
    methods: {
        async addMovie() {
            if (this.name.length > 1 && this.year.length > 0) {

                let movieBody = {
                    name: this.name,
                    year: this.year,
                    completed: this.completed,
                }

                const resp = await fetch("https://moment-2-backend-ramverk-qmmalarsson.onrender.com/movies", {
                    method: "POST",
                    headers: {
                        "Accept": "application/json",
                        "Content-type": "application/json"
                    },
                    body: JSON.stringify(movieBody),
                });

                const data = await resp.json();

                this.name = "";
                this.year = "";
                this.completed = false;

                this.$emit("movieAdded");
            }
        }
    }
}
</script>

<template>
    <div class="flex justify-center">
        <form @submit.prevent="addMovie()" class="border border-red-600 m-4 w-full max-w-[800px]">
            <h2 class="w-full text-4xl text-center bg-red-600 text-white p-4">Lägg till ny film</h2>
            <p class="p-4">
                <label for="name">
                    Namn:
                </label>
                <input v-model="name" id="name" type="text" name="name"
                    class="w-full p-2 border bg-red-100 border-red-600 rounded-md focus:outline-none focus:ring-2 focus:ring-red-600">
            </p>
            <br>
            <p class="p-4">
                <label for="year">
                    År:
                </label>
                <input v-model="year" id="year" type="text" name="year"
                    class="w-full p-2 border bg-red-100 border-red-600 rounded-md focus:outline-none focus:ring-2 focus:ring-red-600">
            </p>
            <p class="p-4">
                <input v-model="completed" id="yes" type="checkbox" name="yes"
                    class="w-8 h-8 focus:ring-2 focus:ring-red-600">
                <label for="minor">
                    Jag har sett filmen
                </label>
            </p>
            <input type="submit" value="Lägg till ny film"
                class="bg-red-600 text-white font-bold py-2 px-4 m-4 rounded min-w-[110px] transition-all duration-300 ease-in-out hover:scale-105">
            <input type="reset"
                class="bg-red-600 text-white font-bold py-2 px-4 rounded min-w-[110px] transition-all duration-300 ease-in-out hover:scale-105">
        </form>
    </div>
</template>