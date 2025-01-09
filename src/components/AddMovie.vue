<template>
    <div class="flex justify-center mb-8">
        <form @submit.prevent="addMovie()" class="border border-red-600 m-4 w-full max-w-[800px]">
            <h2 class="w-full text-4xl text-center bg-red-600 text-white p-4">Lägg till ny film</h2>
            <p class="p-4">
                <label for="name">
                    Namn:
                </label>
                <!-- Two-way binding mellan inputfältet och reaktiv data (name) -->
                <input v-model="name" id="name" type="text" name="name"
                    class="w-full p-2 border bg-red-100 border-red-600 rounded-md focus:outline-none focus:ring-2 focus:ring-red-600">
            </p>
            <p class="p-4">
                <label for="year">
                    År:
                </label>
                <!-- Two-way binding mellan inputfältet och reaktiv data (year) -->
                <input v-model="year" id="year" type="text" name="year"
                    class="w-full p-2 border bg-red-100 border-red-600 rounded-md focus:outline-none focus:ring-2 focus:ring-red-600">
            </p>
            <p class="p-4">
                <!-- Two-way binding mellan checkboxen och reaktiv data (completed) -->
                <input v-model="completed" id="yes" type="checkbox" name="yes"
                    class="w-8 h-8 focus:ring-2 focus:ring-red-600">
                <label for="yes">
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

<script>
export default {
    //Skapa ett reaktivt dataobjekt
    data() {
        return {
            name: "",
            year: "",
            completed: false,
        }
    },
    //Emits som skickar signaler till föräldern när en film har lagts till
    emits: ["movieAdded"],
    methods: {
        //Metod för att lägga till en ny film till webbtjänsten
        async addMovie() {
            //Kontrollerar att namn är korrekt ifyllt
            if (this.name.trim().length === 0) {
                //Visar en alert om fältet inte är ifylldt korrekt
                alert("Namn måste fyllas i!");
                return;
            }

            //Kontrollerar att år är korrekt ifyllt
            if (isNaN(this.year) || this.year <= 1900) {
                //Visar en alert om fältet inte är ifyllt korrekt
                alert("År måste fyllas i och vara en siffra högre än 1900!");
                return;
            }

            {
                let movieBody = {
                    name: this.name,
                    year: parseInt(this.year),
                    completed: this.completed,
                }

                //Skickar en POST-förfrågan för att lägga till en ny film
                const resp = await fetch("https://moment-2-backend-ramverk-qmmalarsson.onrender.com/movies", {
                    method: "POST",
                    headers: {
                        "Accept": "application/json",
                        "Content-type": "application/json"
                    },
                    body: JSON.stringify(movieBody),
                });

                const data = await resp.json();

                //Rensar dataobjekten efter att filmen lagts till
                this.name = "";
                this.year = "";
                this.completed = false;

                this.$emit("movieAdded");
            }
        }
    }
}
</script>