// Movie Data
const movies = [
 {
  title: "Inception",
  year: "2010",
  genre: "Sci-Fi",
  rating: "8.8/10",
  description: "A master thief who infiltrates dreams is offered a final chance at redemption: plant an idea deep within a target’s subconscious. But the deeper the team dives, the more dangerous the dreamworld becomes.",
  banner: "inception-banner.jpg",
  poster: "inception.jpg",
  cast: ["Leonardo DiCaprio", "Joseph Gordon-Levitt", "Elliot Page"]
},
{
  title: "Joker",
  year: "2019",
  genre: "Drama",
  rating: "8.5/10",
  description: "Struggling with isolation and a broken society, Arthur Fleck spirals into madness, transforming into the infamous Joker as he discovers a disturbing sense of purpose in chaos.",
  banner: "joker-banner.jpg",
  poster: "joker.jpg",
  cast: ["Joaquin Phoenix", "Robert De Niro", "Zazie Beetz"]
},
{
  title: "Jurassic World: Fallen Kingdom",
  year: "2018",
  genre: "Action/Sci-Fi",
  rating: "6.2/10",
  description: "With the island’s volcano threatening extinction for the remaining dinosaurs, Owen and Claire launch a daring rescue mission that uncovers a deadly conspiracy threatening the fate of the world.",
  banner: "jurassic-banner.jpg",
  poster: "jurassic.jpg",
  cast: ["Chris Pratt", "Bryce Dallas Howard", "Rafe Spall"]
},
{
  title: "Interstellar",
  year: "2014",
  genre: "Adventure",
  rating: "8.6/10",
  description: "As Earth faces collapse, a group of astronauts journeys beyond a wormhole in search of a new home for humanity, confronting the limits of science, time, and the power of love.",
  banner: "interstellar-banner.jpg",
  poster: "interstellar.jpg",
  cast: ["Matthew McConaughey", "Anne Hathaway", "Jessica Chastain"]
},
{
  title: "It",
  year: "2017",
  genre: "Horror",
  rating: "7.3/10",
  description: "Seven children confront a shape-shifting entity that emerges every 27 years to feed on fear, forcing them to face their deepest nightmares to survive.",
  banner: "it-banner.jpg",
  poster: "it.jpg",
  cast: ["Bill Skarsgård", "Finn Wolfhard", "Jaeden Martell"]
},
{
  title: "The Dark Knight",
  year: "2008",
  genre: "Action",
  rating: "9.0/10",
  description: "Batman faces a ruthless criminal mastermind known as the Joker, whose reign of terror pushes Gotham and its hero to the brink of moral chaos.",
  banner: "dark knight-banner.jpg",
  poster: "dark knight.jpg",
  cast: ["Christian Bale", "Heath Ledger", "Aaron Eckhart"]
},
{
  title: "Dune",
  year: "2021",
  genre: "Sci-Fi",
  rating: "8.0/10",
  description: "Destined for greatness, Paul Atreides must navigate betrayal, prophecy, and war on the desert planet Arrakis the only source of the universe’s most valuable resource.",
  banner: "dune-banner.jpg",
  poster: "dune.jpg",
  cast: ["Timothée Chalamet", "Zendaya", "Oscar Isaac"]
},
{
  title: "Encanto",
  year: "2021",
  genre: "Animation/Family",
  rating: "7.3/10",
  description: "Born into a magical family where everyone has a unique gift except her, Mirabel sets out to save the miracle that holds her family together discovering her own strength along the way.",
  banner: "encanto-banner.jpg",
  poster: "encanto.jpg",
  cast: ["Stephanie Beatriz", "John Leguizamo", "Maria Cecilia Botero"]
},
{
  title: "13 Hours",
  year: "2016",
  genre: "Action/Drama",
  rating: "7.3/10",
  description: "When a U.S. compound in Libya comes under attack, an elite security team fights through overwhelming odds to protect lives in a harrowing true-story battle for survival.",
  banner: "13hours-banner.jpg",
  poster: "13hours.jpg",
  cast: ["John Krasinski", "James Badge Dale", "Pablo Schreiber"]
},
{
  title: "Inside Out 2",
  year: "2024",
  genre: "Animation/Family",
  rating: "7.9/10",
  description: "As teenage Riley faces new challenges, a surge of unfamiliar emotions including Anxiety and Envy enters Headquarters, turning her world upside down in a heartfelt journey of growing up.",
  banner: "inside out 2-banner.jpg",
  poster: "inside out 2.jpg",
  cast: ["Amy Poehler", "Maya Hawke", "Phyllis Smith"]
},
{
  title: "John Wick: Ballerina",
  year: "2025",
  genre: "Action/Thriller",
  rating: "8.1/10",
  description: "Trained as both a dancer and an assassin, a deadly ballerina hunts down the killers of her family crossing paths with legendary hitman John Wick in the perilous criminal underworld.",
  banner: "jwballerina-banner.jpg",
  poster: "jwballerina.jpg",
  cast: ["Ana de Armas", "Keanu Reeves", "Lance Reddick"]
},
{
  title: "The Grinch",
  year: "2018",
  genre: "Animation/Family",
  rating: "8.8/10",
  description: "Determined to steal Christmas from the joyful residents of Whoville, the Grinch sets his sneaky plan in motion — only to discover that kindness can change even the coldest heart.",
  banner: "grinch-banner.jpg",
  poster: "grinch.jpg",
  cast: ["Benedict Cumberbatch", "Rashida Jones", "Kenan Thompson"]
},


];

// Inject Movies into Gallery
const gallery = document.getElementById("movie-gallery");

movies.forEach(movie => {
  const card = document.createElement("div");
  card.classList.add("movie-card");
  card.innerHTML = `
    <img src="${movie.poster}" alt="${movie.title}" />
    <div class="movie-info">
      <h3>${movie.title}</h3>
      <p>⭐ ${movie.rating} | ${movie.genre} | ${movie.year}</p>
    </div>
  `;
  card.addEventListener("click", () => updateHero(movie));
  gallery.appendChild(card);
});

// Update Hero Section Dynamically
function updateHero(movie) {
  const hero = document.getElementById("hero");
  document.getElementById("hero-title").textContent = movie.title;
  document.getElementById("hero-description").textContent = movie.description;
  document.getElementById("hero-rating").textContent = `⭐ ${movie.rating}`;
  document.getElementById("hero-genre").textContent = `• ${movie.genre}`;
  document.getElementById("hero-year").textContent = `• ${movie.year}`;
  hero.style.backgroundImage = `linear-gradient(to bottom, rgba(0,0,0,0.4), #0c0c0c), url('${movie.banner}')`;
}

// Movie Search Filter
const searchBar = document.querySelector('.search-bar');
searchBar.addEventListener('input', e => {
  const searchText = e.target.value.toLowerCase();
  document.querySelectorAll('.movie-card').forEach(card => {
    const title = card.querySelector('h3').textContent.toLowerCase();
    card.style.display = title.includes(searchText) ? '' : 'none';
  });

});
const favBtn = document.getElementById("fav-btn");
let favorites = JSON.parse(localStorage.getItem("favorites")) || [];

function updateHero(movie) {
  const hero = document.getElementById("hero");
  document.getElementById("hero-title").textContent = movie.title;
  document.getElementById("hero-description").textContent = movie.description;
  document.getElementById("hero-rating").textContent = `⭐ ${movie.rating}`;
  document.getElementById("hero-genre").textContent = `• ${movie.genre}`;
  document.getElementById("hero-year").textContent = `• ${movie.year}`;
  hero.style.backgroundImage = `linear-gradient(to bottom, rgba(0,0,0,0.4), #0c0c0c), url('${movie.banner}')`;

const castContainer = document.getElementById("hero-cast");
castContainer.innerHTML = movie.cast
  .map(actor => `<span>${actor}</span>`)
  .join("");


  // Update favorite button
  favBtn.textContent = favorites.includes(movie.title) ? "💚 Favorited" : "♡ Favorite";
  favBtn.onclick = () => toggleFavorite(movie.title);

  // Restart hero animation
const heroContent = document.querySelector(".hero-content");
heroContent.style.animation = "none";
void heroContent.offsetWidth; // force reflow to restart animation
heroContent.style.animation = "heroFadeUp 1.2s ease-out";
}

function toggleFavorite(title) {
  if (favorites.includes(title)) {
    favorites = favorites.filter(fav => fav !== title);
  } else {
    favorites.push(title);
  }
  localStorage.setItem("favorites", JSON.stringify(favorites));
  favBtn.textContent = favorites.includes(title) ? "💚 Favorited" : "♡ Favorite";
}

// Watch button (you can link it to an actual page)
document.getElementById("watch-btn").addEventListener("click", () => {
  alert("Playing movie...");
});
updateHero(movies[0]);


// OPEN POPUP
document.querySelector(".subscribe-btn").addEventListener("click", () => {
  document.getElementById("subscription-popup").style.display = "flex";
});

// CLOSE POPUP
document.getElementById("close-popup").addEventListener("click", () => {
  document.getElementById("subscription-popup").style.display = "none";
});

// Plan Buttons
document.querySelectorAll(".choose-btn").forEach(btn => {
  btn.addEventListener("click", () => {
    alert("Thank you for choosing a plan! 🎉");
  });
});


