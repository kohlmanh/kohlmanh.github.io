---
layout: null
title: "Home"
permalink: /
markdown: false
---
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>{{ page.title }}</title>
  <link rel="icon" href="{{ site.baseurl }}favicon.ico" type="image/x-icon" />
  <link rel="stylesheet" href="{{ site.baseurl }}assets/css/terminal.css">
  <style>
    /* Reset styles */
    html, body {
      width: 100%;
      height: 100%;
      margin: 0;
      padding: 0;
      overflow: hidden;
      background: url('{{ site.baseurl }}assets/images/duckhunt-background.jpg') no-repeat center center fixed;
      background-size: cover;
      cursor: url('{{ site.baseurl }}assets/images/crosshair.cur'), auto;
    }
    /* Game area */
    #game-container {
      position: absolute;
      width: 100%;
      height: 100%;
      z-index: 5;
    }
    /* Ducks - doubled from original 80px to 160px */
    .duck {
      position: absolute;
      width: 160px;
      height: 160px;
      background-size: contain;
      background-repeat: no-repeat;
      cursor: url('{{ site.baseurl }}assets/images/crosshair.cur'), auto;
      z-index: 10;
    }
    /* Increased font size for duck labels to match larger duck size */
    .duck span {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: white;
      font-size: 1.5em;
      font-weight: bold;
      text-shadow: 2px 2px 4px #000000;
      pointer-events: none;
    }
    /* Explosion effect - also increased for better proportion with larger ducks */
    .explosion {
      position: absolute;
      width: 180px;
      height: 180px;
      background: url('{{ site.baseurl }}assets/images/explosion.png') no-repeat center center;
      background-size: contain;
      pointer-events: none;
      animation: fadeOut 0.6s ease-out forwards;
      z-index: 20;
    }
    @keyframes fadeOut {
      from { opacity: 1; }
      to { opacity: 0; }
    }
  </style>
</head>
<body>
  <div id="game-container"></div>

  <script>
    const ducks = [
      { id: 'duck1', image: 'duck1.gif', url: '{{ site.baseurl }}cv', label: 'CV' },
      { id: 'duck2', image: 'duck2.gif', url: '{{ site.baseurl }}about', label: 'ABOUT' },
      { id: 'duck3', image: 'duck3.gif', url: '{{ site.baseurl }}contact', label: 'CONTACT' },
      { id: 'duck4', image: 'duck4.gif', url: '{{ site.baseurl }}work', label: 'WORK' }
    ];

    const gameContainer = document.getElementById('game-container');

    // Track duck positions for shot detection
    let duckPositions = [];

    function getRandomPosition() {
      // Updated to account for doubled duck size
      const duckWidth = 160;
      const duckHeight = 160;
      return {
        x: Math.random() * (window.innerWidth - duckWidth),
        y: Math.random() * (window.innerHeight / 2 - duckHeight) // Keep ducks above the bottom half
      };
    }

    function spawnDucks() {
      ducks.forEach((duck) => {
        const { x, y } = getRandomPosition();

        const duckElement = document.createElement('div');
        duckElement.id = duck.id;
        duckElement.className = 'duck';
        duckElement.style.backgroundImage = `url('{{ site.baseurl }}assets/images/${duck.image}')`;
        duckElement.setAttribute('data-url', duck.url);
        duckElement.style.left = `${x}px`;
        duckElement.style.top = `${y}px`;

        const label = document.createElement('span');
        label.textContent = duck.label;
        duckElement.appendChild(label);
        gameContainer.appendChild(duckElement);

        // Initialize movement
        moveDuck(duckElement);
      });
    }

    function moveDuck(duckElement) {
      // Reduced speed for much larger ducks
      let dx = 1.5 + Math.random() * 1.5; 
      let dy = 1.5 + Math.random() * 1.5;

      function animate() {
        let x = parseFloat(duckElement.style.left);
        let y = parseFloat(duckElement.style.top);

        // Bounce off edges
        if (x + duckElement.offsetWidth > window.innerWidth || x < 0) {
          dx = -dx;
          // Flip the duck image horizontally when changing direction
          duckElement.style.transform = dx > 0 ? 'scaleX(1)' : 'scaleX(-1)';
        }
        if (y + duckElement.offsetHeight > window.innerHeight / 2 || y < 0) {
          dy = -dy;
        }

        // Update position
        duckElement.style.left = `${x + dx}px`;
        duckElement.style.top = `${y + dy}px`;

        // Update duck position in our tracking array
        updateDuckPosition(duckElement);

        requestAnimationFrame(animate);
      }

      animate();
    }

    function updateDuckPosition(duckElement) {
      const rect = duckElement.getBoundingClientRect();
      const duckInfo = {
        id: duckElement.id,
        element: duckElement,
        url: duckElement.getAttribute('data-url'),
        left: rect.left,
        right: rect.right,
        top: rect.top,
        bottom: rect.bottom
      };
      
      // Update or add this duck's position
      const index = duckPositions.findIndex(duck => duck.id === duckElement.id);
      if (index !== -1) {
        duckPositions[index] = duckInfo;
      } else {
        duckPositions.push(duckInfo);
      }
    }

    function isPointInDuck(x, y, duck) {
      return x >= duck.left && x <= duck.right && y >= duck.top && y <= duck.bottom;
    }

    function createExplosion(x, y) {
      const explosion = document.createElement('div');
      explosion.className = 'explosion';
      explosion.style.left = `${x - 90}px`; // Adjusted for larger explosion
      explosion.style.top = `${y - 90}px`; // Adjusted for larger explosion
      document.body.appendChild(explosion);
      explosion.addEventListener('animationend', () => explosion.remove());
    }

    // Shoot anywhere on the screen
    document.body.addEventListener('click', (event) => {
      const audio = new Audio('{{ site.baseurl }}assets/sounds/gunshot.mp3');
      audio.play();
      createExplosion(event.clientX, event.clientY);
      
      // Check if we hit a duck
      for (const duck of duckPositions) {
        if (isPointInDuck(event.clientX, event.clientY, duck)) {
          // Hit a duck! Navigate to its URL after a short delay
          setTimeout(() => {
            window.location.href = duck.url;
          }, 600);
          break;
        }
      }
    });

    // Ensure ducks are properly positioned on window resize
    window.addEventListener('resize', () => {
      // Clear existing ducks
      const existingDucks = document.querySelectorAll('.duck');
      existingDucks.forEach(duck => duck.remove());
      
      // Reset duck positions tracking
      duckPositions = [];
      
      // Respawn ducks in valid positions
      spawnDucks();
    });

    // Initialize the game and start tracking duck positions
    window.onload = function() {
      spawnDucks();
      
      // Start position tracking for all ducks
      setInterval(() => {
        document.querySelectorAll('.duck').forEach(updateDuckPosition);
      }, 100); // Update positions 10 times per second
    };
  </script>
</body>
</html>