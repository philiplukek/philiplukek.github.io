---
layout: personal
title: Movies
subtitle: Cinematic journeys and long-form takes.
permalink: /personal/movies/
---

<style>
  .movies-section-title {
    font-size: 1.3rem;
    font-weight: 600;
    margin: 50px 0 18px 0;
    color: #222;
    letter-spacing: 0.02em;
    border-left: 4px solid #e8b400;
    padding-left: 12px;
  }

  .movie-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    gap: 18px;
  }

  .movie-card {
    cursor: pointer;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 12px rgba(0,0,0,0.18);
    transition: transform 0.25s ease, box-shadow 0.25s ease;
    background: #e0e0e0;
  }

  .movie-card:hover {
    transform: scale(1.04) translateY(-3px);
    box-shadow: 0 12px 28px rgba(0,0,0,0.28);
  }

  .movie-card.active {
    outline: 3px solid #e8b400;
    outline-offset: 2px;
  }

  .movie-poster {
    width: 100%;
    display: block;
    aspect-ratio: 2/3;
    object-fit: cover;
  }

  .review-drawer {
    grid-column: 1 / -1;
    display: none;
    background: #fafafa;
    border: 1px solid #e5e5e5;
    border-radius: 12px;
    padding: 28px 30px;
    margin: 4px 0 16px 0;
    animation: drawerIn 0.35s ease;
  }

  @keyframes drawerIn {
    from { opacity: 0; transform: translateY(-8px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .drawer-inner {
    display: flex;
    gap: 28px;
    align-items: flex-start;
  }

  .drawer-poster {
    width: 110px;
    flex-shrink: 0;
    border-radius: 6px;
    box-shadow: 0 4px 14px rgba(0,0,0,0.2);
  }

  .drawer-body { flex: 1; }

  .drawer-body h2 {
    margin: 0 0 6px 0;
    font-size: 1.25rem;
    color: #111;
  }

  .movie-meta {
    font-size: 0.88rem;
    color: #777;
    margin-bottom: 14px;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    align-items: center;
  }

  .movie-meta strong { color: #444; }

  .long-review {
    line-height: 1.7;
    font-size: 0.98rem;
    color: #444;
    margin-bottom: 16px;
  }

  .imdb-link {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: #e8b400;
    color: #000;
    font-weight: 700;
    font-size: 0.8rem;
    padding: 5px 12px;
    border-radius: 5px;
    text-decoration: none;
    letter-spacing: 0.04em;
    transition: background 0.2s;
  }
  .imdb-link:hover { background: #d4a400; }

  .close-btn {
    float: right;
    cursor: pointer;
    font-size: 1.4rem;
    line-height: 1;
    color: #aaa;
    transition: color 0.2s;
    margin-left: 12px;
  }
  .close-btn:hover { color: #333; }

  @media (max-width: 540px) {
    .drawer-inner { flex-direction: column; }
    .drawer-poster { width: 80px; }
  }
</style>

<div id="recently-watched-section">
  <div class="movies-section-title">🎬 Recently Watched</div>
  <div class="movie-grid" id="grid-recent"></div>
</div>

<div id="favourites-section">
  <div class="movies-section-title">⭐ All-Time Favourites</div>
  <div class="movie-grid" id="grid-favourites"></div>
</div>

<script>
// ╔══════════════════════════════════════════════════════╗
// ║  STEP 1 — Add your free TMDB API key here           ║
// ║  Get one at: themoviedb.org/settings/api            ║
// ╚══════════════════════════════════════════════════════╝
const TMDB_KEY = "8265bd1679663a7ea12ac168da84d2e8";  // ← paste your key


// ╔══════════════════════════════════════════════════════╗
// ║  STEP 2 — Add your movies                           ║
// ║                                                      ║
// ║  tmdb → number in the TMDB URL                      ║
// ║    themoviedb.org/movie/157336  →  157336           ║
// ║                                                      ║
// ║  imdb → "tt" code in the IMDb URL                   ║
// ║    imdb.com/title/tt0816692/   →  "tt0816692"       ║
// ║                                                      ║
// ║  stars → rating out of 5 (0.5 steps supported)      ║
// ╚══════════════════════════════════════════════════════╝

const recentlyWatched = [
  {
    id:     "dhurandhar2",
    tmdb:   1582770,
    imdb:   "tt39139925",
    stars:  3.5,
    review: ""
  },

{
    id:     "aadu3",
    tmdb:   1260210,
    imdb:   "tt8142672",
    stars:  3,
    review: ""
  },

  {
    id:     "sinners",
    tmdb:   1233413,
    imdb:   "tt31193180",
    stars:  4.0,
    review: ""
  },

    {
    id:     "dhurandhar",
    tmdb:   1291608,
    imdb:   "tt33014583",
    stars:  4.0,
    review: ""
  },

  // ── add more recently watched movies here ──
];

const allTimeFavourites = [
  {
    id:     "interstellar",
    tmdb:   157336,
    imdb:   "tt0816692",
    stars:  4.5,
    review: ""
  },
];


// ════════════════════════════════════════════
//   ENGINE — no need to edit below this line
// ════════════════════════════════════════════

function renderStars(rating) {
  let html = "";
  for (let i = 1; i <= 5; i++) {
    if (rating >= i) {
      html += `<span style="color:#e8b400">★</span>`;
    } else if (rating >= i - 0.5) {
      html += `<span style="position:relative;display:inline-block;color:#ddd">★<span style="position:absolute;left:0;top:0;width:50%;overflow:hidden;color:#e8b400">★</span></span>`;
    } else {
      html += `<span style="color:#ddd">★</span>`;
    }
  }
  return html;
}

function buildCard(movie) {
  return `
    <div class="movie-card" id="card-${movie.id}" onclick="toggleReview('${movie.id}')">
      <img class="movie-poster" id="poster-${movie.id}" alt="${movie.id}">
    </div>
    <div id="drawer-${movie.id}" class="review-drawer">
      <span class="close-btn" onclick="toggleReview('${movie.id}')">&times;</span>
      <div class="drawer-inner">
        <img class="drawer-poster" id="drawer-poster-${movie.id}" alt="">
        <div class="drawer-body">
          <h2 id="title-${movie.id}">Loading…</h2>
          <div class="movie-meta">
            <span>Directed by <strong id="director-${movie.id}">—</strong></span>
            <span>${renderStars(movie.stars)}</span>
          </div>
          <div class="long-review">${movie.review}</div>
          <a class="imdb-link" href="https://www.themoviedb.org/movie/${movie.tmdb}" target="_blank">IMDb ↗</a>
        </div>
      </div>
    </div>`;
}

function renderGrid(movies, gridId) {
  document.getElementById(gridId).innerHTML = movies.map(buildCard).join("");
}

async function fetchMeta(movie) {
  if (!TMDB_KEY || TMDB_KEY === "YOUR_KEY_HERE") {
    document.getElementById(`title-${movie.id}`).textContent    = "Add TMDB key to auto-fill title";
    document.getElementById(`director-${movie.id}`).textContent = "—";
    return;
  }
  try {
    const [mRes, cRes] = await Promise.all([
      fetch(`https://api.themoviedb.org/3/movie/${movie.tmdb}?api_key=${TMDB_KEY}`),
      fetch(`https://api.themoviedb.org/3/movie/${movie.tmdb}/credits?api_key=${TMDB_KEY}`)
    ]);
    const mData   = await mRes.json();
    const cData   = await cRes.json();
    const director  = cData.crew?.find(p => p.job === "Director")?.name || "Unknown";
    const year      = mData.release_date?.slice(0, 4) || "";
    const title     = `${mData.title}${year ? " (" + year + ")" : ""}`;
    const posterUrl = mData.poster_path
      ? `https://image.tmdb.org/t/p/w500${mData.poster_path}` : "";

    document.getElementById(`title-${movie.id}`).textContent    = title;
    document.getElementById(`director-${movie.id}`).textContent = director;
    if (posterUrl) {
      document.getElementById(`poster-${movie.id}`).src        = posterUrl;
      document.getElementById(`drawer-poster-${movie.id}`).src = posterUrl;
    }
  } catch (e) {
    document.getElementById(`title-${movie.id}`).textContent = "Failed to load";
    console.error("TMDB error:", movie.id, e);
  }
}

function toggleReview(id) {
  const drawer = document.getElementById("drawer-" + id);
  const card   = document.getElementById("card-" + id);
  const isOpen = drawer.style.display === "block";

  document.querySelectorAll(".review-drawer").forEach(d => d.style.display = "none");
  document.querySelectorAll(".movie-card").forEach(c => c.classList.remove("active"));

  if (!isOpen) {
    drawer.style.display = "block";
    card.classList.add("active");
    setTimeout(() => drawer.scrollIntoView({ behavior: "smooth", block: "nearest" }), 50);
  }
}

// Init
renderGrid(recentlyWatched,   "grid-recent");
renderGrid(allTimeFavourites, "grid-favourites");
[...recentlyWatched, ...allTimeFavourites].forEach(fetchMeta);
</script>