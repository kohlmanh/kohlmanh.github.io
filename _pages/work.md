---
layout: null
title: Work
permalink: /work/
excerpt: "artwork"
---
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Work - Kohlman Harshbarger</title>
  <link rel="stylesheet" href="/assets/css/work.css">
  <link rel="stylesheet" href="/assets/css/terminal.css">
  <link rel="stylesheet" href="/assets/css/style.css">
  <style>
    body {
      overflow-y: auto !important; /* Force scrolling to be enabled */
      height: auto !important; /* Allow body to expand with content */
      min-height: 100vh;
      animation: none !important; /* Prevent flashing/flickering */
    }  
    .container {
      padding-top: 70px; /* Space for fixed header */
      padding-bottom: 40px; /* Bottom padding for scrolling */
    }
    .home-button {
      font-size: 28px;
      font-weight: bold;
      position: fixed; /* Keep button visible while scrolling */
      top: 20px;
      left: 20px;
      z-index: 1001;
      background: rgba(0, 0, 0, 0.7);
      padding: 10px 15px;
      border-radius: 5px;
      color: #00ff00;
      text-decoration: none;
      border: 1px solid #00ff00;
      box-shadow: 0 0 10px #00ff00;
    }  
    .home-button:hover {
      background: rgba(0, 255, 0, 0.2);
    }
    .art-grid {
      display: grid;
      grid-template-columns: 1fr;
      grid-gap: 45px;
      margin: 0 auto;
      max-width: 1200px;
    }
    .art-item {
      margin-bottom: 15px;
      cursor: pointer;
    }
    .art-image-grid {
      display: block !important;
      opacity: 1 !important;
      width: 100%;
      height: auto;
      max-height: 1000px;
      object-fit: contain;
    }
    .art-title {
      margin-top: 12px;
      text-align: center;
      font-size: 18px;
    }
    /* Loading screen styles */
    .loading-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: black;
      color: #00ff00;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 3000;
    }
    /* Override any styles that might be preventing scrolling */
    html, body {
      overflow: auto !important;
    }
    /* Improve modal and close button visibility */
    .modal {
      background: rgba(0, 0, 0, 0.9);
    }
    .close-button {
      position: absolute;
      top: 20px;
      right: 20px;
      font-size: 40px;
      background: rgba(0, 0, 0, 0.7);
      color: #ff0000; /* Red for better visibility */
      width: 50px;
      height: 50px;
      border-radius: 25px;
      border: 2px solid #ff0000;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      box-shadow: 0 0 15px #ff0000;
      z-index: 2001;
    }
    .close-button:hover {
      background: rgba(255, 0, 0, 0.3);
      transform: scale(1.1);
    }
    /* Year ticker */
    .year-ticker {
      position: fixed;
      top: 20px;
      right: 20px;
      font-size: 28px !important;
      font-weight: bold;
      z-index: 1001;
      background: rgba(0, 0, 0, 0.7);
      padding: 10px 15px;
      border-radius: 5px;
      color: #00ff00;
      border: 1px solid #00ff00;
      box-shadow: 0 0 10px #00ff00;
    }
    /* Improved modal navigation */
    #modal-prev, #modal-next {
      background: rgba(0, 0, 0, 0.7);
      color: #00ff00;
      border: 2px solid #00ff00;
      width: 50px;
      height: 80px;
      font-size: 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 0 15px #00ff00;
    }
    #modal-prev:hover, #modal-next:hover {
      background: rgba(0, 255, 0, 0.2);
    } 
    /* Improve modal content */
    .modal-content {
      padding: 30px;
      border: 1px solid #00ff00;
      box-shadow: 0 0 20px #00ff00;
    }
    .modal-content p {
      margin: 10px 0;
      font-size: 18px;
    }
  </style>
</head>
<body>
  <!-- Loading Screen -->
  <div class="loading-screen" id="loading-screen">
    <div>WORK LOADING...</div>
    <div class="loading-bar"></div>
  </div>

  <div class="header">WORK</div>
  <div class="container">
    <a href="javascript:void(0)" onclick="returnToHome()" class="home-button">&lt; Back to Home</a>
    <div id="year-ticker" class="year-ticker"></div>
    <!-- Page content -->
    <div id="work-content" style="display:none;">
      <div class="art-grid" id="art-grid">
        {% assign works = site.data.artindex %}
        {% if works %}
          {% assign years = works | group_by: "Year" | sort: "name" | reverse %}
          {% for year in years %}
            {% for work in year.items %}
              {% assign imagePath = work.ImageFilename | split: ',' | first | strip %}
              <div class="art-item" data-year="{{ year.name }}" onclick="openModal('{{ work.ImageFilename | escape }}', '{{ work.Title | escape }}', '{{ work.Material | escape }}', '{{ work.Dimensions | escape }}', '{{ work.Description | escape }}')">
                <img src="{{ site.baseurl }}/assets/images/{{ imagePath }}" alt="{{ work.Title | strip }}" class="art-image-grid">
                <p class="art-title">{{ work.Title | strip }}</p>
              </div>
            {% endfor %}
          {% endfor %}
        {% else %}
          <p>No artwork data found.</p>
        {% endif %}
      </div>
    </div>
  </div>

  <!-- Modal Structure for Image Enlargement -->
  <div id="image-modal" class="modal">
    <div class="modal-content">
      <button class="close-button" onclick="closeModal()">&times;</button>
      <img id="modal-image" src="" alt="">
      <p id="modal-title"></p>
      <p id="modal-material"></p>
      <p id="modal-dimensions"></p>
      <p id="modal-description"></p>
      <button id="modal-prev" class="carousel-arrow prev" onclick="navigateModal(-1)">&#10094;</button>
      <button id="modal-next" class="carousel-arrow next" onclick="navigateModal(1)">&#10095;</button>
    </div>
  </div>

  <script>
    // Carousel Functionality
    function moveCarousel(button, direction) {
      const carousel = button.parentElement;
      const items = carousel.querySelectorAll('.carousel-item');
      let activeIndex = Array.from(items).findIndex(item => item.classList.contains('active'));

      items[activeIndex].classList.remove('active');

      activeIndex += direction;

      if (activeIndex >= items.length) {
        activeIndex = 0;
      } else if (activeIndex < 0) {
        activeIndex = items.length - 1;
      }

      items[activeIndex].classList.add('active');
    }

    // Year Ticker Functionality
    function updateYearOnScroll() {
      const items = document.querySelectorAll('.art-item');
      let currentYear = '';
      let scrollPosition = window.scrollY + window.innerHeight / 2;
      items.forEach(item => {
        const rect = item.getBoundingClientRect();
        const itemTop = rect.top + window.scrollY;
        const itemBottom = itemTop + rect.height;
        if (scrollPosition >= itemTop && scrollPosition <= itemBottom) {
          currentYear = item.getAttribute('data-year');
        }
      });
      const ticker = document.getElementById('year-ticker');
      if (ticker && currentYear) {
        ticker.textContent = currentYear;
      }
    }

    // Modal Functionality
    let currentIndex = 0;
    let currentItems = [];

    function openModal(imageFilename, title, material, dimensions, description) {
      const modal = document.getElementById('image-modal');
      const modalImage = document.getElementById('modal-image');
      const modalTitle = document.getElementById('modal-title');
      const modalMaterial = document.getElementById('modal-material');
      const modalDimensions = document.getElementById('modal-dimensions');
      const modalDescription = document.getElementById('modal-description');

      currentItems = imageFilename.split(',');
      currentIndex = 0;

      modalImage.src = `/assets/images/${currentItems[currentIndex].trim()}`;
      modalTitle.textContent = title;
      modalMaterial.textContent = `Material: ${material}`;
      modalDimensions.textContent = `Dimensions: ${dimensions}`;
      modalDescription.textContent = `Description: ${description}`;

      modal.style.display = 'flex';
      
      // Add keyboard controls for modal
      document.addEventListener('keydown', handleKeyPress);
    }

    function closeModal() {
      const modal = document.getElementById('image-modal');
      modal.style.display = 'none';
      
      // Remove keyboard event listener when modal is closed
      document.removeEventListener('keydown', handleKeyPress);
    }
    
    // Handle keyboard navigation in modal
    function handleKeyPress(e) {
      if (e.key === 'Escape') {
        closeModal();
      } else if (e.key === 'ArrowLeft') {
        navigateModal(-1);
      } else if (e.key === 'ArrowRight') {
        navigateModal(1);
      }
    }

    function navigateModal(direction) {
      currentIndex += direction;

      if (currentIndex >= currentItems.length) {
        currentIndex = 0;
      } else if (currentIndex < 0) {
        currentIndex = currentItems.length - 1;
      }

      const modalImage = document.getElementById('modal-image');
      modalImage.src = `/assets/images/${currentItems[currentIndex].trim()}`;
    }
    
    // Return to Home functionality
    function returnToHome() {
      const body = document.body;
      
      // Add glitch effect
      body.classList.add('glitch');
      setTimeout(() => {
        body.classList.remove('glitch');
        body.classList.add('power-down');
        
        setTimeout(() => {
          // Random selection of loading messages
          const allMessages = [
            "Navigating home...",
            "Loading grass...",
            "Wrangling ducks...",
            "Compiling memories...",
            "Tuning reality...",
            "Synchronizing vibes...",
            "Adjusting atmosphere...",
            "Calibrating coziness...",
            "Preparing existential crisis...",
            "Evicting ghosts...",
            "Defragmenting dreams...",
            "Unpacking nostalgia...",
            "Rendering nostalgia...",
            "Debugging childhood...",
            "Deleting bad decisions...",
            "Pouring a drink...",
            "Checking if door is locked...",
            "Refilling existential dread..."
          ];
          
          // Randomly pick 4 messages
          let loadingMessages = [];
          for (let i = 0; i < 4; i++) {
            const randomIndex = Math.floor(Math.random() * allMessages.length);
            loadingMessages.push(allMessages[randomIndex]);
          }
          
          // Create home loading screen
          const homeLoadingScreen = document.createElement('div');
          homeLoadingScreen.className = 'home-loading-screen';
          
          const loadingText = document.createElement('div');
          loadingText.className = 'home-loading-text';
          loadingText.id = 'loading-text';
          loadingText.textContent = 'Navigating home...';
          
          const loadingBarContainer = document.createElement('div');
          loadingBarContainer.className = 'home-loading-bar';
          
          const barFill = document.createElement('div');
          barFill.className = 'home-bar-fill';
          
          loadingBarContainer.appendChild(barFill);
          homeLoadingScreen.appendChild(loadingText);
          homeLoadingScreen.appendChild(loadingBarContainer);
          
          // Clear the body and add the loading screen
          document.body.innerHTML = '';
          document.body.appendChild(homeLoadingScreen);
          
          // Trigger the animation
          setTimeout(() => {
            barFill.classList.add('animate');
          }, 100);
          
          // Update loading text
          let index = 0;
          function updateLoadingText() {
            if (index < loadingMessages.length) {
              document.getElementById("loading-text").innerText = loadingMessages[index];
              index++;
            }
          }
          
          const textInterval = setInterval(updateLoadingText, 800);
          
          // Navigate to home page
          setTimeout(() => {
            clearInterval(textInterval);
            window.location.href = "/";
          }, 5000);
        }, 1000);
      }, 500);
    }

    // Initialize page loading
    window.onload = function() {
      // Stop all animations that might cause flashing
      document.body.style.animation = 'none';
      document.documentElement.style.animation = 'none';
      
      // Make sure overflow is enabled
      document.documentElement.style.overflow = 'auto';
      document.body.style.overflow = 'auto';
      
      // Show loading screen for 3 seconds
      setTimeout(() => {
        document.getElementById('loading-screen').style.opacity = '0';
        document.getElementById('loading-screen').style.transition = 'opacity 0.5s ease';
        
        setTimeout(() => {
          document.getElementById('loading-screen').style.display = 'none';
          document.getElementById('work-content').style.display = 'block';
          
          // Initialize Year Ticker
          updateYearOnScroll();
        }, 500);
      }, 3000);
    };
    
    // Add event listeners
    window.addEventListener('scroll', updateYearOnScroll);
    
    // Add click outside to close modal
    window.addEventListener('click', function(event) {
      const modal = document.getElementById('image-modal');
      if (event.target === modal) {
        closeModal();
      }
    });
  </script>
</body>
</html>