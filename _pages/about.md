---
layout: null
title: About
permalink: /about/
---
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>About - Kohlman Harshbarger</title>
  <link rel="stylesheet" href="/assets/css/style.css">
  <link rel="stylesheet" href="/assets/css/terminal.css">
  <style>
    /* Reset and prevent flashing */
    body {
      animation: none !important;
      overflow: hidden !important;
      margin: 0;
      padding: 0;
      background: black;
      color: #00ff00;
      font-family: "Courier New", Courier, monospace;
      height: 100vh;
      width: 100vw;
    }
    /* Enhanced home button */
    .home-button {
      position: fixed;
      top: 20px;
      left: 20px;
      background: black;
      color: #00ff00;
      font-family: "Courier New", Courier, monospace;
      font-size: 24px;
      font-weight: bold;
      cursor: pointer;
      text-shadow: 0 0 5px #00ff00;
      padding: 5px 10px;
      z-index: 2000;
      border: 2px solid #00ff00;
      box-shadow: 0 0 10px #00ff00;
      transition: all 0.3s ease;
    }
    
    .home-button:hover {
      color: #ffffff;
      text-shadow: 0 0 10px #00ff00;
      transform: scale(1.05);
    }
    
    /* Loading screen styling */
    .loading-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: black;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      z-index: 3000;
    }
    
    #loading-text {
      color: #00ff00;
      font-size: 24px;
      margin-bottom: 20px;
      font-family: "Courier New", Courier, monospace;
      text-transform: uppercase;
    }
    
    .progress-bar {
      width: 300px;
      height: 6px;
      background: #333;
      position: relative;
    }
    
    .progress {
      position: absolute;
      left: 0;
      top: 0;
      height: 100%;
      width: 0;
      background: #00ff00;
      transition: width 0.3s ease;
    }
    
    /* Words container positioning */
    .words-container {
      position: fixed;
      width: 100%;
      height: 100%;
      top: 0;
      left: 0;
    }
    
    /* Enhanced flying words */
    .flying-word {
      position: absolute;
      font-size: 3.5rem;
      color: #00ff00;
      text-shadow: 0 0 10px currentColor;
      cursor: pointer;
      user-select: none;
      white-space: nowrap;
      font-weight: bold;
      z-index: 10;
      will-change: transform, left, top;
      transition-property: left, top, transform;
      transition-timing-function: cubic-bezier(0.34, 1.56, 0.64, 1);
      transition-duration: 0.8s;
    }

    .flying-word:hover {
      color: #ffffff !important;
      text-shadow: 0 0 15px currentColor;
      z-index: 100;
      transform: scale(1.2);
    }
    
    .assembled .flying-word {
      transform: rotate(0) !important;
    }
    
    /* Home loading screen styles for exit animation */
    .home-loading-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      background-color: black;
      z-index: 3000;
    }
    
    .home-loading-text {
      color: #00ff00;
      font-size: 24px;
      margin-bottom: 20px;
      font-family: "Courier New", Courier, monospace;
    }
    
    .home-loading-bar {
      width: 700px;
      height: 10px;
      background: rgba(0, 0, 0, 0.8);
      border: 1px solid #00ff00;
      position: relative;
      overflow: hidden;
    }
    
    .home-bar-fill {
      position: absolute;
      left: 0;
      top: 0;
      height: 100%;
      width: 0;
      background-color: #00ff00;
      transition: width 5s linear;
    }
    
    .home-bar-fill.animate {
      width: 100%;
    }
    
    /* Glitch and power-down effects */
    @keyframes glitch {
      0% { opacity: 1; transform: translateX(0); }
      20% { opacity: 0.8; transform: translateX(-10px); }
      40% { opacity: 1; transform: translateX(10px); }
      60% { opacity: 0.8; transform: translateX(-5px); }
      80% { opacity: 1; transform: translateX(5px); }
      100% { opacity: 1; transform: translateX(0); }
    }
    
    .glitch {
      animation: glitch 0.5s forwards;
    }
    
    @keyframes powerDown {
      0% { opacity: 1; }
      100% { opacity: 0; }
    }
    
    .power-down {
      animation: powerDown 1s forwards;
    }
    
    /* Explosion effect */
    @keyframes explode {
      0% { 
        transform: scale(1) rotate(0); 
        opacity: 1;
      }
      100% { 
        transform: scale(1.5) rotate(var(--random-rotate)); 
        opacity: 0;
      }
    }
    
    .exploding {
      animation: explode 0.5s forwards;
    }
    
    /* Assembled sentence area */
    .sentence-area {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      pointer-events: none;
    }
    
    .sentence-container {
      width: 80%;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      pointer-events: all;
    }
  </style>
</head>
<body>
  <!-- Loading Screen -->
  <div class="loading-screen" id="loading-screen">
    <div id="loading-text">ABOUT PAGE LOADING...</div>
    <div class="progress-bar">
      <div class="progress" id="loading-progress"></div>
    </div>
  </div>

  <main id="about-content" style="display:none;">
    <!-- Flying Words -->
    <div class="words-container" id="words-container">
      <span class="flying-word" data-index="0">Kohlman</span>
      <span class="flying-word" data-index="1">Harshbarger</span>
      <span class="flying-word" data-index="2">is</span>
      <span class="flying-word" data-index="3">a</span>
      <span class="flying-word" data-index="4">transdisciplinary</span>
      <span class="flying-word" data-index="5">artist</span>
      <span class="flying-word" data-index="6">whose</span>
      <span class="flying-word" data-index="7">work</span>
      <span class="flying-word" data-index="8">investigates</span>
      <span class="flying-word" data-index="9">the</span>
      <span class="flying-word" data-index="10">crannies</span>
      <span class="flying-word" data-index="11">between</span>
      <span class="flying-word" data-index="12">sculpture</span>
      <span class="flying-word" data-index="13">installation</span>
      <span class="flying-word" data-index="14">and</span>
      <span class="flying-word" data-index="15">sound</span>
    </div>

    <!-- Return to Home Button -->
    <button onclick="returnToHome()" class="home-button">&lt; Return to Home</button>
  </main>

  <script>
    // Available colors for bouncing words
    const colors = [
      '#00ff00', // Green
      '#ff00ff', // Magenta
      '#00ffff', // Cyan
      '#ffff00', // Yellow
      '#ff0000', // Red
      '#0000ff'  // Blue
    ];
    
    // Original sentence in correct order
    const sentenceOrder = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15];
    
    window.onload = function() {
      // Start the loading animation
      let width = 0;
      const loadingProgress = document.getElementById('loading-progress');
      const interval = setInterval(() => {
        if (width >= 100) {
          clearInterval(interval);
          
          // Fade out loading screen
          document.getElementById('loading-screen').style.opacity = '0';
          document.getElementById('loading-screen').style.transition = 'opacity 0.5s ease';
          
          // Show content
          setTimeout(() => {
            document.getElementById('loading-screen').style.display = 'none';
            document.getElementById('about-content').style.display = 'block';
            
            // Initialize words
            initializeWords();
          }, 500);
        } else {
          width += 1;
          loadingProgress.style.width = width + '%';
        }
      }, 30);
    };
    
    let isAssembled = false;
    let animationFrame = null;
    
    function initializeWords() {
      const words = document.querySelectorAll('.flying-word');
      const container = document.getElementById('words-container');
      const containerWidth = window.innerWidth;
      const containerHeight = window.innerHeight;
      
      // Set fixed positions across the entire screen
      const positions = [
        // Left side
        { x: containerWidth * 0.1, y: containerHeight * 0.2 },
        { x: containerWidth * 0.15, y: containerHeight * 0.5 },
        { x: containerWidth * 0.2, y: containerHeight * 0.8 },
        { x: containerWidth * 0.25, y: containerHeight * 0.3 },
        
        // Center area
        { x: containerWidth * 0.4, y: containerHeight * 0.15 },
        { x: containerWidth * 0.5, y: containerHeight * 0.4 },
        { x: containerWidth * 0.45, y: containerHeight * 0.65 },
        { x: containerWidth * 0.55, y: containerHeight * 0.75 },
        
        // Right side
        { x: containerWidth * 0.7, y: containerHeight * 0.25 },
        { x: containerWidth * 0.8, y: containerHeight * 0.6 },
        { x: containerWidth * 0.75, y: containerHeight * 0.4 },
        { x: containerWidth * 0.85, y: containerHeight * 0.7 },
        
        // Additional positions for all words
        { x: containerWidth * 0.3, y: containerHeight * 0.2 },
        { x: containerWidth * 0.6, y: containerHeight * 0.3 },
        { x: containerWidth * 0.2, y: containerHeight * 0.6 },
        { x: containerWidth * 0.7, y: containerHeight * 0.8 }
      ];
      
      // Initialize each word with a position and color
      words.forEach((word, index) => {
        // Get position (cycle through if more words than positions)
        const position = positions[index % positions.length];
        
        // Initial random color
        const colorIndex = Math.floor(Math.random() * colors.length);
        word.style.color = colors[colorIndex];
        word.dataset.colorIndex = colorIndex;
        
        // Store original color
        word.dataset.originalColor = colors[colorIndex];
        
        // Set initial position
        word.style.left = `${position.x}px`;
        word.style.top = `${position.y}px`;
        
        // Set random rotation
        const rotation = Math.random() * 20 - 10;
        word.style.transform = `rotate(${rotation}deg)`;
        
        // Set velocities (make sure they move in different directions)
        word.dataset.vx = (Math.random() * 3 + 1) * (Math.random() > 0.5 ? 1 : -1);
        word.dataset.vy = (Math.random() * 3 + 1) * (Math.random() > 0.5 ? 1 : -1);
        
        // Set to handle color change on bounce
        word.dataset.changeColor = "false";
        
        // Turn off transitions initially
        word.style.transitionDuration = "0s";
      });
      
      // Start animation
      setTimeout(() => {
        startAnimation();
      }, 50);
      
      // Add click listener to toggle between flying and assembled
      container.addEventListener('click', toggleWordState);
    }
    
    function startAnimation() {
      if (isAssembled) return;
      
      const words = document.querySelectorAll('.flying-word');
      
      // Turn off transitions for smooth animation
      words.forEach(word => {
        word.style.transitionDuration = "0s";
      });
      
      const containerWidth = window.innerWidth;
      const containerHeight = window.innerHeight;
      
      function animateWords() {
        if (isAssembled) {
          cancelAnimationFrame(animationFrame);
          return;
        }
        
        words.forEach((word) => {
          // Get current position
          let x = parseFloat(word.style.left);
          let y = parseFloat(word.style.top);
          
          // Get velocities
          let vx = parseFloat(word.dataset.vx);
          let vy = parseFloat(word.dataset.vy);
          
          // Move word
          x += vx;
          y += vy;
          
          // Get dimensions
          const rect = word.getBoundingClientRect();
          const wordWidth = rect.width;
          const wordHeight = rect.height;
          
          // Check boundaries and bounce
          let changeColor = false;
          
          if (x <= 0 || x + wordWidth >= containerWidth) {
            // Horizontal bounce
            word.dataset.vx = -vx;
            changeColor = true;
            
            // Keep in bounds
            if (x <= 0) x = 0;
            if (x + wordWidth >= containerWidth) x = containerWidth - wordWidth;
          }
          
          if (y <= 0 || y + wordHeight >= containerHeight) {
            // Vertical bounce
            word.dataset.vy = -vy;
            changeColor = true;
            
            // Keep in bounds
            if (y <= 0) y = 0;
            if (y + wordHeight >= containerHeight) y = containerHeight - wordHeight;
          }
          
          // Change color on bounce
          if (changeColor) {
            let colorIndex = parseInt(word.dataset.colorIndex);
            colorIndex = (colorIndex + 1) % colors.length;
            word.style.color = colors[colorIndex];
            word.dataset.colorIndex = colorIndex;
            
            // Update original color
            word.dataset.originalColor = colors[colorIndex];
          }
          
          // Apply new position
          word.style.left = `${x}px`;
          word.style.top = `${y}px`;
        });
        
        animationFrame = requestAnimationFrame(animateWords);
      }
      
      animationFrame = requestAnimationFrame(animateWords);
    }
    
    function toggleWordState() {
      if (!isAssembled) {
        // Assemble words in the center
        assembleWords();
        isAssembled = true;
      } else {
        // Scatter words with explosion effect
        explodeWords();
        isAssembled = false;
      }
    }
    
    function assembleWords() {
      // Cancel animation
      cancelAnimationFrame(animationFrame);
      
      const container = document.getElementById('words-container');
      const containerWidth = window.innerWidth;
      const containerHeight = window.innerHeight;
      
      // Create sentence area if it doesn't exist
      let sentenceArea = document.querySelector('.sentence-area');
      if (!sentenceArea) {
        sentenceArea = document.createElement('div');
        sentenceArea.className = 'sentence-area';
        container.appendChild(sentenceArea);
      }
      
      // Create sentence container if it doesn't exist
      let sentenceContainer = document.querySelector('.sentence-container');
      if (!sentenceContainer) {
        sentenceContainer = document.createElement('div');
        sentenceContainer.className = 'sentence-container';
        sentenceArea.appendChild(sentenceContainer);
      }
      
      // Add assembled class to container
      container.classList.add('assembled');
      
      // Calculate layout for the sentence
      const words = Array.from(document.querySelectorAll('.flying-word'));
      const sentenceWords = sentenceOrder.map(index => words.find(word => parseInt(word.dataset.index) === index));
      
      // Calculate positions for a centered paragraph layout
      const containerCenter = { x: containerWidth / 2, y: containerHeight / 2 };
      const lineWidth = containerWidth * 0.8;
      const wordSpacing = 20;
      const lineHeight = 80;
      
      let currentX = (containerWidth - lineWidth) / 2;
      let currentY = containerCenter.y - 50;
      let currentLineWidth = 0;
      
      // Position words in the sentence order
      sentenceWords.forEach((word, index) => {
        // Turn on transitions
        word.style.transitionDuration = `${0.8 + index * 0.05}s`;
        
        // Get word dimensions
        const rect = word.getBoundingClientRect();
        const wordWidth = rect.width;
        
        // Check if we need to wrap to a new line
        if (currentX + wordWidth > containerWidth - (containerWidth - lineWidth) / 2 && currentLineWidth > 0) {
          currentX = (containerWidth - lineWidth) / 2;
          currentY += lineHeight;
          currentLineWidth = 0;
        }
        
        // Stagger the transitions
        setTimeout(() => {
          // Position word
          word.style.left = `${currentX}px`;
          word.style.top = `${currentY}px`;
          word.style.transform = 'rotate(0deg)';
          word.style.zIndex = 20 + index;
        }, index * 50);
        
        // Update position for next word
        currentX += wordWidth + wordSpacing;
        currentLineWidth += wordWidth + wordSpacing;
      });
    }
    
    function explodeWords() {
      // Get the words in their assembled positions
      const container = document.getElementById('words-container');
      const words = document.querySelectorAll('.flying-word');
      const containerWidth = window.innerWidth;
      const containerHeight = window.innerHeight;
      
      // Create a flash effect
      const flash = document.createElement('div');
      flash.style.position = 'fixed';
      flash.style.top = '0';
      flash.style.left = '0';
      flash.style.width = '100%';
      flash.style.height = '100%';
      flash.style.backgroundColor = 'white';
      flash.style.opacity = '0.3';
      flash.style.zIndex = '999';
      flash.style.transition = 'opacity 0.3s ease';
      document.body.appendChild(flash);
      
      // Fade out flash
      setTimeout(() => {
        flash.style.opacity = '0';
        setTimeout(() => {
          flash.remove();
        }, 300);
      }, 50);
      
      // Remove assembled class
      container.classList.remove('assembled');
      
      // Explode words in sequence
      words.forEach((word, index) => {
        // Set a random target position in a quadrant
        const quadrant = index % 4;
        let targetX, targetY;
        
        // Force distribution into quadrants
        const padding = 80;
        
        switch(quadrant) {
          case 0: // Top left
            targetX = Math.random() * (containerWidth / 2 - padding) + padding;
            targetY = Math.random() * (containerHeight / 2 - padding) + padding;
            break;
          case 1: // Top right
            targetX = Math.random() * (containerWidth / 2 - padding) + containerWidth / 2;
            targetY = Math.random() * (containerHeight / 2 - padding) + padding;
            break;
          case 2: // Bottom left
            targetX = Math.random() * (containerWidth / 2 - padding) + padding;
            targetY = Math.random() * (containerHeight / 2 - padding) + containerHeight / 2;
            break;
          case 3: // Bottom right
            targetX = Math.random() * (containerWidth / 2 - padding) + containerWidth / 2;
            targetY = Math.random() * (containerHeight / 2 - padding) + containerHeight / 2;
            break;
        }
        
        // Set random rotation for explosion effect
        const rotateAmount = Math.random() * 60 - 30;
        
        // Set explosion transition with staggered delays
        word.style.transitionDuration = '0.6s';
        word.style.transitionDelay = `${index * 30}ms`;
        word.style.transitionTimingFunction = 'cubic-bezier(0.22, 1, 0.36, 1)';
        
        // Apply explosion effect
        setTimeout(() => {
          word.style.left = `${targetX}px`;
          word.style.top = `${targetY}px`;
          word.style.transform = `rotate(${rotateAmount}deg)`;
        }, 50 + index * 20);
        
        // Set velocities for after explosion
        const dirX = (targetX > parseFloat(word.style.left)) ? 1 : -1;
        const dirY = (targetY > parseFloat(word.style.top)) ? 1 : -1;
        
        word.dataset.vx = (Math.random() * 3 + 1) * dirX;
        word.dataset.vy = (Math.random() * 3 + 1) * dirY;
      });
      
      // Remove sentence container after explosion
      setTimeout(() => {
        const sentenceArea = document.querySelector('.sentence-area');
        if (sentenceArea) {
          sentenceArea.remove();
        }
        
        // Reset transitions and start animation
        words.forEach(word => {
          word.style.transitionDuration = '0s';
          word.style.transitionDelay = '0s';
        });
        
        startAnimation();
      }, 800);
    }
    
    // Return to Home function with enhanced loading screen
    function returnToHome() {
      const body = document.body;
      // Add glitch effect
      body.classList.add('glitch');
      setTimeout(() => {
          body.classList.remove('glitch');
          body.classList.add('power-down');
          setTimeout(() => {
              // Expanded list of fun loading messages
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
                  "Rearranging clouds...",
                  "Debugging childhood...",
                  "Deleting bad decisions...",
                  "Pouring a drink...",
                  "Checking if door is locked...",
                  "Refilling existential dread...",
                  "Locating lost socks...",
                  "Converting bad vibes to good ones...",
                  "Flipping reality switch...",
                  "Turning on the night mode..."
              ];
              
              // Randomly pick messages for this session
              let loadingMessages = [];
              const shuffledMessages = [...allMessages].sort(() => 0.5 - Math.random());
              for (let i = 0; i < 5; i++) {
                  loadingMessages.push(shuffledMessages[i]);
              }
              
              // Create home loading screen with About page styling
              document.body.innerHTML = `
                  <div class="home-loading-screen">
                      <div class="home-loading-text" id="loading-text">Loading home...</div>
                      <div class="home-loading-bar">
                          <div class="home-bar-fill"></div>
                      </div>
                  </div>
              `;
              
              // Animate loading bar
              setTimeout(() => {
                  document.querySelector('.home-bar-fill').classList.add('animate');
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
    
    // Handle window resize
    window.addEventListener('resize', () => {
      if (!isAssembled) {
        // Cancel existing animation
        cancelAnimationFrame(animationFrame);
        
        // Reinitialize positions for flying words
        initializeWords();
      } else {
        // Reassemble for new screen size
        assembleWords();
      }
    });
  </script>
</body>
</html>