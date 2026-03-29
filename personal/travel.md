---
layout: personal
title: Travel
subtitle: Places I've been, stories I carry.
permalink: /personal/travel/
---

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<style>
  .travel-stats {
    display: flex;
    gap: 28px;
    margin: 24px 0 28px 0;
    flex-wrap: wrap;
  }
  .stat-item { display: flex; flex-direction: column; }
  .stat-number {
    font-size: 1.6rem;
    font-weight: 700;
    color: #222;
    line-height: 1;
  }
  .stat-label {
    font-size: 0.8rem;
    color: #888;
    margin-top: 3px;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  #travel-map {
    width: 100%;
    height: 420px;
    border-radius: 12px;
    border: 1px solid #e0e0e0;
    margin-bottom: 40px;
    z-index: 0;
  }

  .custom-pin {
    width: 14px;
    height: 14px;
    background: #D85A30;
    border: 2.5px solid white;
    border-radius: 50%;
    box-shadow: 0 2px 6px rgba(0,0,0,0.3);
    cursor: pointer;
    transition: transform 0.15s ease;
  }
  .custom-pin:hover { transform: scale(1.4); }

  .travel-section-title {
    font-size: 1.3rem;
    font-weight: 600;
    margin: 0 0 18px 0;
    color: #222;
    border-left: 4px solid #D85A30;
    padding-left: 12px;
  }

.trip-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 32px;
  padding: 20px 0 50px 0;
}

.trip-card {
  background: white;
  padding: 12px 12px 44px 12px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.12);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  text-decoration: none;
  color: inherit;
  display: block;
  transform: rotate(-2deg);
}
.trip-card:nth-child(even) { transform: rotate(2deg); }
.trip-card:hover {
  transform: rotate(0deg) scale(1.05);
  box-shadow: 0 12px 32px rgba(0,0,0,0.18);
  z-index: 10;
}

.trip-cover {
  width: 100%;
  aspect-ratio: 1/1;
  object-fit: cover;
  display: block;
  filter: sepia(15%);
}

.trip-cover-placeholder {
  width: 100%;
  aspect-ratio: 1/1;
  display: flex;
  align-items: center;
  justify-content: center;
}

.trip-caption {
  font-family: 'Georgia', serif;
  color: #333;
  text-align: center;
  margin-top: 12px;
  font-size: 1.05rem;
}

.trip-meta-small {
  font-family: 'Georgia', serif;
  font-size: 0.8rem;
  color: #888;
  text-align: center;
  margin-top: 3px;
}

.country-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 4px;
  justify-content: center;
  margin-top: 6px;
}
.country-tag {
  font-size: 0.68rem;
  background: #f5f0ee;
  color: #a05030;
  border-radius: 20px;
  padding: 2px 8px;
  font-weight: 500;
  font-family: sans-serif;
}
</style>


<!-- <div class="travel-stats">
  <div class="stat-item">
    <span class="stat-number" id="stat-trips">0</span>
    <span class="stat-label">Trips</span>
  </div>
  <div class="stat-item">
    <span class="stat-number" id="stat-countries">0</span>
    <span class="stat-label">Countries</span>
  </div>
  <div class="stat-item">
    <span class="stat-number" id="stat-cities">0</span>
    <span class="stat-label">Cities</span>
  </div>
</div> -->

<div id="travel-map"></div>

<div class="travel-section-title">All Trips</div>
<div class="trip-grid" id="trip-grid"></div>


<script>
// ╔══════════════════════════════════════════════════════════════╗
// ║   ADD YOUR TRIPS HERE — this is the only thing to edit      ║
// ║                                                              ║
// ║  SINGLE-COUNTRY, SINGLE-PIN TRIP:                           ║
// ║   country: "India"                                          ║
// ║   lat: 32.23, lng: 77.18                                    ║
// ║                                                              ║
// ║  MULTI-COUNTRY, MULTI-PIN TRIP:                             ║
// ║   country: ["France", "Italy", "Spain"]                     ║
// ║   pins: [                                                    ║
// ║     { lat: 48.85, lng: 2.35,  city: "Paris" },              ║
// ║     { lat: 41.90, lng: 12.49, city: "Rome"  },              ║
// ║     { lat: 40.41, lng: -3.70, city: "Madrid"},              ║
// ║   ]                                                          ║
// ║                                                              ║
// ║  Both formats work — mix freely across trips.               ║
// ║                                                              ║
// ║  Get lat/lng: right-click any spot on maps.google.com       ║
// ╚══════════════════════════════════════════════════════════════╝

const trips = [

  // ── Single-pin example ──
  {
    id:       "up",
    name:     "Lucknow-Banaras-Prayagraj",
    location: "Uttar Pradesh",
    country:  "India",
    date:     "February 2026",
    lat:      27.912483234837797, 
    lng:      79.75677733285738,
    note:     "Food, Spirituality and Chaos",
    cover:    "/assets/personal/up2.jpeg",
    color:    "linear-gradient(135deg, #4a7c59, #8fbc8f)",
    page:     "/personal/travel/up/"
  },
    {
    id:       "rudranath",
    name:     "Rudranath trek",
    location: "Uttarakhand",
    country:  "India",
    date:     "October 2025",
    lat:      30.51952497795437, 
    lng:      79.31895387867016,
    note:     "A trek so GOAT-ed",
    cover:    "/assets/personal/rudranath.jpeg",
    color:    "linear-gradient(135deg, #4a7c59, #8fbc8f)",
    page:     "/personal/travel/rudranath/"
  },
    { 
    id:       "dayara",
    name:     "Dayara Bugyal trek",
    location: "Uttarakhand",
    country:  "India",
    date:     "September 2025",
    lat:      30.836180671560612, 
    lng:      78.55929999145081,
    note:     "Clean air, lush meadows and gorgeous views",
    cover:    "/assets/personal/dayara.jpeg",
    color:    "linear-gradient(135deg, #4a7c59, #8fbc8f)",
    page:     "/personal/travel/dayara/"
  },
  //   {
  //   id:       "dayara",
  //   name:     "Dayara Bugyal trek",
  //   location: "Uttarakhand",
  //   country:  "India",
  //   date:     "September 2025",
  //   lat:      30.836180671560612, 
  //   lng:      78.55929999145081,
  //   note:     "Clean air, lush meadows and gorgeous views",
  //   cover:    "",
  //   color:    "linear-gradient(135deg, #4a7c59, #8fbc8f)",
  //   page:     "/personal/travel/dayara/"
  // },
  {
    id:       "chicago",
    name:     "U.S",
    location: "Chicago, New York",
    country:  "USA",
    date:     "July 2025",
    lat:      41.88422205844864, 
    lng:      -87.64194022400514,
    note:     "Skyscrapers and rectangles everywhere",
    cover:    "/assets/personal/ny.jpg",
    color:    "linear-gradient(135deg, #4a7c59, #8fbc8f)",
    page:     "/personal/travel/usa/"
  },
  {
    id:       "japan",
    name:     "Japaaan",
    location: "Japan",
    country:  "Japan",
    date:     "May 2025",
    lat:      36.40537304253569, 
    lng:      138.19260069963303,
    note:     "I just wanna go back 10 more times",
    cover:    "/assets/personal/tokyo.jpg",
    color:    "linear-gradient(135deg, #4a7c59, #8fbc8f)",
    page:     "/personal/travel/japan/"
  },
  {
    id:       "kuari",
    name:     "Kuari pass trek",
    location: "Uttarakhand",
    country:  "India",
    date:     "March 2025",
    lat:      30.446294698709742, 
    lng:      79.56987120037952,
    note:     "A wholesome snow trek",
    cover:    "/assets/personal/kuari.jpeg",
    color:    "linear-gradient(135deg, #4a7c59, #8fbc8f)",
    page:     "/personal/travel/kuari/"
  },
  {
    id:       "europe",
    name:     "Europe 2023",
    location: "Europe",
    country:  ["Ireland", "UK", "France", "Italy"],
    date:     "June 2023",
      pins: [
    { lat: 51.89841194211231, lng: -8.477625082795807,  city: "Ireland"  },
    { lat: 51.51912730194177, lng: -0.1249545258316021, city: "U.K"   },
    { lat: 48.8567926049533, lng: 2.357331139736329, city: "France" },
    { lat: 41.896154842614884, lng: 12.46869488527149, city: "Italy" }
  ],   
    // lat:      30.446294698709742, 
    // lng:      79.56987120037952,
    note:     "My Da-Vinci code trail",
    cover:    "/assets/personal/london.jpg",
    color:    "linear-gradient(135deg, #4a7c59, #8fbc8f)",
    page:     "/personal/travel/europe/"
  },
];


// ════════════════════════════════════════════
//   ENGINE — no need to edit below this line
// ════════════════════════════════════════════

// Helpers
function getCountries(trip) {
  return Array.isArray(trip.country) ? trip.country : [trip.country];
}

function getPins(trip) {
  // Multi-pin format
  if (trip.pins && Array.isArray(trip.pins)) return trip.pins;
  // Single-pin format — wrap to same shape
  return [{ lat: trip.lat, lng: trip.lng, city: trip.location }];
}

// Stats — deduplicate countries and count total cities across all trips
const allCountries = [...new Set(trips.flatMap(getCountries))];
const totalCities  = trips.reduce((sum, t) => sum + getPins(t).length, 0);
// document.getElementById("stat-trips").textContent     = trips.length;
// document.getElementById("stat-countries").textContent = allCountries.length;
// document.getElementById("stat-cities").textContent    = totalCities;

// Map
const map = L.map("travel-map", { center: [20, 10], zoom: 2, minZoom: 2 });

L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
  attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  maxZoom: 18
}).addTo(map);

function makePin() {
  return L.divIcon({
    className: "",
    html: `<div class="custom-pin"></div>`,
    iconSize: [14, 14],
    iconAnchor: [7, 7]
  });
}

// Place all pins for every trip
trips.forEach(trip => {
  const pins = getPins(trip);
  pins.forEach(pin => {
    const marker = L.marker([pin.lat, pin.lng], { icon: makePin() }).addTo(map);
    marker.on("click", () => { window.location.href = trip.page; });
    marker.bindTooltip(
      `<strong>${trip.name}</strong><br>
       <span style="font-size:11px;color:#666">${pin.city}</span><br>
       <span style="font-size:11px;color:#888">${trip.date}</span>`,
      { direction: "top", offset: [0, -8], opacity: 1 }
    );
  });
});

// Trip cards
const grid = document.getElementById("trip-grid");
grid.innerHTML = trips.map(trip => {
  const countries = getCountries(trip);
  const countryTags = countries.length > 1
    ? `<div class="country-tags">${countries.map(c => `<span class="country-tag">${c}</span>`).join("")}</div>`
    : "";

return `
  <a class="trip-card" href="${trip.page}">
    ${trip.cover
      ? `<img class="trip-cover" src="${trip.cover}" alt="${trip.name}">`
      : `<div class="trip-cover-placeholder" style="background:${trip.color};"></div>`
    }
    <div class="trip-caption">${trip.name}</div>
    <div class="trip-meta-small">${trip.location} · ${trip.date}</div>
    ${countryTags}
  </a>`;
}).join("");
</script>