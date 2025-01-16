# Moment 3 i kursen DT193G, Fullstacks-utveckling med ramverk
**Namn:** Emma Larsson\
**Student-ID:** emla2309

### Beskrivning av webbplats
Detta är en webbapplikation för att visa och hantera filmer. Webbapplikationen visar en lista med filmer, och användare kan själva lägga till och ta bort filmer från listan. Tanken är att man ska lägga till filmer som man har sett och filmer som man inte har sett, men som man önskar se någon gång i framtiden. En film innehåller information om filmens namn, releasedatum och om användaren har sett filmen eller inte.

Projektet är en SPA-applikation och skapades med hjälp av Vue.js (https://vuejs.org/).

### Beskrivning av lösning
**Hämta, skicka och radera data**\
För att hämta, skicka och radera data till en extern webbtjänst används Fetch API. De HTTP-anrop som används är GET, POST och DELETE. Den webbtjänst som används är https://moment-2-backend-ramverk-qmmalarsson.onrender.com/movies.

**Movie.vue**\
Komponenten Movie.vue används för att visa information om varje enskild film. Den tar emot filmens data som props från MovieView.vue och skriver ut informationen i en tabell. Den information som visas är filmen namn, releasedatum och om användaren har sett filmen eller inte. Varje film har även en "Ta bort"-knapp som gör det möjligt föt användaren att radera filmen från listan. Det som händer om användaren klickar på knappen är att en DELETE-förfrågan med filmens individuella ID skickas till webbtjänsten.

**AddMovie.vue**\
Komponenten AddMovie.vue används för att lägga till en ny film. Ett formulär samlar in information om filmen och two-way binding används för att uppdatera ett dataobjekt med reaktiva variabler. När användaren klickar på knappen "Lägg till" skickas en POST-förfrågan med den insamlade datan för att lägga till filmen på den externa webbtjänsten.

Komponenten använder även emits för att kommunicera med sin föräldrakomponent. När en film har lagts till skickar AddMovie.vue ett meddelande till MovieView.vue, som då uppdaterar listan med filmer på webbapplikationen.

### Installera projekt

För att installera och börja använda projektet, följ nedanstående steg:
* Klona projektet från Github. För att göra detta, nagivera till den mapp där du vill spara projektet, skriv in "git clone" följt av Github-repots URL.
* Installera beroenden. För att göra detta använd kommandot "npm install".
* Kör projektet. För att göra detta använd kommandot "npm run dev".
* Kommandot för att bygga projektet är "npm run build".
