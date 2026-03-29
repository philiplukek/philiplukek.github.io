---
layout: personal
title: Books
subtitle: My digital library and recent discoveries.
permalink: /personal/books/
---

<style>
  .shelf-section { margin-bottom: 60px; }
  .shelf-title {
    font-size: 1.6rem;
    font-weight: 700;
    margin-bottom: 30px;
    border-bottom: 1px solid #ddd;
    padding-bottom: 10px;
    color: #333;
  }

  .bookshelf {
    display: flex;
    flex-wrap: wrap;
    gap: 40px;
    justify-content: flex-start;
  }

  /* The Book Container */
  .book-item {
    position: relative;
    display: inline-block;
  }

  .book-card {
    display: block;
    width: 130px;
    height: 195px;
    box-shadow: 4px 6px 12px rgba(0,0,0,0.15);
    border-radius: 3px;
    transition: transform 0.2s ease-in-out;
    background: #f0f0f0; /* Fallback */
  }

  .book-cover {
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 3px;
  }

  /* The Tooltip (Review) */
  .book-tooltip {
    visibility: hidden;
    width: 220px;
    background-color: #2c3e50;
    color: #fff;
    text-align: center;
    border-radius: 8px;
    padding: 15px;
    position: absolute;
    z-index: 10;
    bottom: 110%; /* Place it above the book */
    left: 50%;
    margin-left: -110px; /* Center it */
    opacity: 0;
    transition: opacity 0.3s, transform 0.3s;
    transform: translateY(10px);
    box-shadow: 0 10px 20px rgba(0,0,0,0.2);
    font-size: 0.9rem;
    pointer-events: none; /* Stops it from flickering */
  }

  /* Arrow for Tooltip */
  .book-tooltip::after {
    content: "";
    position: absolute;
    top: 100%;
    left: 50%;
    margin-left: -5px;
    border-width: 5px;
    border-style: solid;
    border-color: #2c3e50 transparent transparent transparent;
  }

  /* Hover Effects */
  .book-item:hover .book-card {
    transform: scale(1.05);
  }

  .book-item:hover .book-tooltip {
    visibility: visible;
    opacity: 1;
    transform: translateY(0);
  }

  .rating { color: #ffcc00; margin-bottom: 5px; display: block; }
</style>


<div class="shelf-section">
  <div class="shelf-title">📖 Recent Reads</div>
  <div class="bookshelf">

      <!-- <div class="book-item">
      <a href="https://www.goodreads.com/book/show/11.The_Hitchhiker_s_Guide_to_the_Galaxy" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9781400052929-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐⭐⭐</span>
        "Incredibly witty. It taught me that the answer to life is 42, but the question is much harder to find."
      </div>
    </div> -->

    <div class="book-item">
      <a href="https://www.goodreads.com/book/show/45857086-the-burning-god" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9780008339142-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐</span>
        Third and final part of the Poppy war trilogy. A fitting end to the series. Writing felt amateurish at times. 
      </div>
    </div>

    <div class="book-item">
      <a href="https://www.goodreads.com/book/show/41212753-the-dragon-republic" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9780062662637-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐1/2</span>
        Second part of the Poppy war trilogy. The plot and the characters get darker. 
      </div>
    </div>

    <div class="book-item">
      <a href="https://www.goodreads.com/book/show/35068705-the-poppy-war" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9780062662590-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐1/2</span>
        Starts as a young adult fiction, making the reader invested in another harry potter-istic universe. And then Voilaa !!!
      </div>
    </div>

    <div class="book-item">
      <a href="https://www.goodreads.com/book/show/1232.The_Shadow_of_the_Wind" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9780753821206-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐⭐</span>
        The setting, the mystery and the plotline is incredible. Though the latter reveals are typical, the book maintains momentum to keep the reader engaged. The brilliant first chapter captures the emotions of every book reader with their favourite book. Looking forward to the rest of the books from the same universe. 
      </div>
    </div>

    <div class="book-item">
      <a href="https://www.goodreads.com/book/show/58662236-small-things-like-these" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9780802158741-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐⭐</span>
        Short novel. Serious setting. Painful turn of events. Very well written. 
      </div>
    </div>

    <div class="book-item">
      <a href="https://https://www.goodreads.com/book/show/57945316-babel" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9780063021426-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐1/2</span>
        A popular page-turner. The setting was interesting with a minimal fantasy in the backdrop of actual reality and history. I liked reading it. Though it could carry mixed opinions. 
      </div>
    </div>

    <div class="book-item">
      <a href="https://www.goodreads.com/book/show/25489025-the-vegetarian" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9780553448184-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐1/2</span>
        A pretty serious book. Can't say thats what I thought of getting into and hence was a tough read for me. 
      </div>
    </div>

    <div class="book-item">
      <a href="https://www.goodreads.com/book/show/25726346-karikkottakkari" target="_blank" class="book-card">
        <img src="https://images.isbndb.com/covers/11420073485081.jpg" 
        class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐⭐</span>
        Vinoy Thomas's firt work, dealing with classism, casteism and racism among Christianity in Kerala. A very compelling read throughout, and the first-timer mistakes can be easily forgiven.  
      </div>
    </div>

    <div class="book-item">
      <a href="https://www.goodreads.com/book/show/20613611-malice" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9781250035608-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐1/2</span>
        I am a fan of Higashino thrillers and this one was an absolute page-turner for me. I think I finished it in 2/3 days or so. That being said, the whole plot and execution felt slightly underwhelming once I finished and looked back. 
      </div>
    </div>

  </div>
</div>

<div class="shelf-section">
  <div class="shelf-title">✨ All-Time Favorites</div>
  <div class="bookshelf">

    <!-- <div class="book-item">
      <a href="https://www.goodreads.com/book/show/25489025-the-vegetarian" target="_blank" class="book-card">
        <img src="https://covers.openlibrary.org/b/isbn/9780553448184-L.jpg" class="book-cover" alt="Book">
      </a>
      <div class="book-tooltip">
        <span class="rating">⭐⭐⭐⭐⭐</span>
        "Incredibly witty. It taught me that the answer to life is 42, but the question is much harder to find."
      </div>
    </div> -->

</div>
</div>