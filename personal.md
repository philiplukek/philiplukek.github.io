---
layout: default
title: Personal
permalink: /personal/
---
    
## Beyond research, coding, and academics : 

<section class="personal-page">
  <div class="personal-grid">
    
    <div class="flip-card" data-link="/personal/travel/">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img src="/assets/icons/travel.svg" alt="Travel">
          <h3>Travel</h3>
        </div>
        <div class="flip-card-back">
          <p>Experiences that shaped how I observe places and people.</p>
          <span class="flip-action">Explore →</span>
        </div>
      </div>
    </div>

    <div class="flip-card" data-link="/personal/movies/">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img src="/assets/icons/film.svg" alt="Movies">
          <h3>Movies</h3>
        </div>
        <div class="flip-card-back">
          <p>Stories on screen that linger longer than the credits.</p>
          <span class="flip-action">Explore →</span>
        </div>
      </div>
    </div>

    <div class="flip-card" data-link="/personal/books/">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img src="/assets/icons/books.svg" alt="Books">
          <h3>Books</h3>
        </div>
        <div class="flip-card-back">
          <p>Books that shaped how I think, not just what I know.</p>
          <span class="flip-action">Explore →</span>
        </div>
      </div>
    </div>

    <div class="flip-card" data-link="/personal/food/">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img src="/assets/icons/food.svg" alt="Food">
          <h3>Food</h3>
        </div>
        <div class="flip-card-back">
          <p>Food as memory, culture, and quiet joy.</p>
          <span class="flip-action">Explore →</span>
        </div>
      </div>
    </div>

  </div> </section>

<script>
  document.querySelectorAll('.flip-card').forEach(card => {
    card.addEventListener('click', () => {
      const link = card.dataset.link;
      if (card.classList.contains('is-flipped')) {
        window.location.href = link;
      } else {
        // First, unflip any other flipped cards (optional but recommended)
        document.querySelectorAll('.flip-card').forEach(c => c.classList.remove('is-flipped'));
        // Flip the clicked card
        card.classList.add('is-flipped');
      }
    });
  });
</script>