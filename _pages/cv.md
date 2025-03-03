---
layout: null
title: CV
permalink: /cv/
---
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CV - Kohlman Harshbarger</title>
    <link rel="stylesheet" href="/assets/css/terminal.css">
    <link rel="stylesheet" href="/assets/css/style.css">
   <style>
    /* Additional styles specific to CV page */
    html, body {
        height: 100%;
        overflow-y: auto; /* Enable vertical scrolling */
    } 
    body {
        font-size: 22px;
        padding: 20px;
    }
    #cv-content {
        padding-bottom: 40px; /* Add bottom padding for better scrolling */
    }
    .cv-header {
        margin-bottom: 40px;
        border-bottom: 2px solid #00ff00;
        padding-bottom: 20px;
        text-align: center;
    }
    .cv-header h1 {
        font-size: 38px;
        margin-bottom: 15px;
        letter-spacing: 2px;
    }
    .cv-header p {
        font-size: 24px;
    }
    h2 {
        font-size: 30px;
        letter-spacing: 2px;
        margin-top: 40px;
        margin-bottom: 20px;
        padding-bottom: 10px;
    }
    .section-content {
        display: none;
        padding-left: 20px;
        margin-bottom: 30px;
    }
    .section-content.visible {
        display: block;
    }
    .section-content p {
        margin-bottom: 16px;
        font-size: 22px;
    }
    strong {
        font-size: 24px;
        text-shadow: 0 0 8px #00ff00;
    }
    a {
        color: #00ff00;
        text-decoration: none;
        border-bottom: 1px dotted #00ff00;
        transition: all 0.2s ease;
    }
    a:hover {
        color: #ffffff;
        text-shadow: 0 0 5px #00ff00;
        border-bottom: 1px solid #ffffff;
    }
    .home-button {
        position: fixed;
        top: 20px;
        left: 20px;
        font-size: 32px;
        font-weight: bold;
        z-index: 1000; /* Ensure button stays on top when scrolling */
    }
    /* Ensure loading screen is visible and styled properly */
    .loading-screen {
        z-index: 3000;
        font-size: 36px;
    }
</style>
</head>
<body>
    <div class="loading-screen" id="loading-screen">
        <div>CV LOADING...</div>
        <div class="loading-bar"></div>
    </div>
    <button onclick="returnToHome()" class="home-button">&lt; Return to Home</button>
    <div id="cv-content" style="display:none;">
        <div class="cv-header">
            <h1>Kohlman Harshbarger</h1>
            <p>Born 1993, Boston, MA | Lives and works in Brooklyn, NY</p>
        </div>
        <h2 onclick="toggleSection('solo-exhibitions')">SOLO EXHIBITIONS</h2>
        <div id="solo-exhibitions" class="section-content">
            <p><strong>2024</strong> - Cute Kills, Preachers Valley, New York, NY</p>
        </div>
        <h2 onclick="toggleSection('group-exhibitions')">GROUP EXHIBITIONS</h2>
        <div id="group-exhibitions" class="section-content">
            <p><strong>2024</strong> - <a href="https://www.coreypresha.com/cpp/holiday-market" target="_blank">Holiday Market, Portal 5</a>, New York, NY</p>
            <p><strong>2024</strong> - Holiday Market, <a href="https://hesseflatow.com" target="_blank">Hesse Flatow</a>, New York, NY</p>
            <p><strong>2024</strong> - The Show of Stolen Goods, <a href="https://www.instagram.com/uhaul_gallery/" target="_blank">U-Haul Gallery</a>, New York, NY</p>
            <p><strong>2024</strong> - SPIT II, Preachers Valley, New York, NY</p>
            <p><strong>2024</strong> - Rathaus, 324 E 14th, New York, NY</p>
            <p><strong>2023</strong> - <a href="https://www.underlandgallery.com/events-past/prixfixe" target="_blank">Prix Fixe, Underland Gallery</a>, Brooklyn, NY</p>
            <p><strong>2023</strong> - Spit, Preacher's Valley, New York, NY</p>
            <p><strong>2023</strong> - <a href="https://allstnyc.com/3rd:-nothing-but-trouble" target="_blank">Nothing But Trouble, All Street Gallery</a>, New York, NY</p>
            <p><strong>2022</strong> - <a href="https://www.oflahertysnyc.com/patriot" target="_blank">The Patriot, O'Flaherty's</a>, New York, NY</p>
            <p><strong>2022</strong> - <a href="https://triggeringdjgallery.com/Hot-Dog" target="_blank">Hot Dog: A Group Show, Triggering DJ</a>, Brooklyn, NY</p>
            <p><strong>2021</strong> - For the Trees, Plein Air Show in Prospect Park, Brooklyn, NY</p>
            <p><strong>2021</strong> - Bailey House Auction & Artsy, Online</p>
            <p><strong>2020</strong> - Flux Factory Annual Auction & Artsy, Online</p>
            <p><strong>2018</strong> - <a href="https://designmcr.com/events/transient-space" target="_blank">Transient Space, Design Manchester Festival</a>, Manchester, UK (with PlayLab)</p>
            <p><strong>2017</strong> - Holiday Market, Museum Quality Gallery, Brooklyn, NY</p>
            <p><strong>2016</strong> - Salon Show, Greenpoint Gallery, Brooklyn, NY</p>
        </div>
        <h2 onclick="toggleSection('lectures')">LECTURES AND WORKSHOPS</h2>
        <div id="lectures" class="section-content">
            <p><strong>2023</strong> - <a href="https://allstnyc.com" target="_blank">Nothing But Trouble, Artist Talk, All Street Gallery</a>, New York, NY</p>
            <p><strong>2018</strong> - <a href="https://www.artshackbrooklyn.org" target="_blank">Artist Workshop, ArtShack</a>, Brooklyn, NY</p>
        </div>
        <h2 onclick="toggleSection('press')">PRESS AND PRINTED PUBLICATIONS</h2>
        <div id="press" class="section-content">
            <p><strong>2024</strong> - <a href="https://www.blurringbooks.com/book/the-show-of-stolen-goods" target="_blank">The Show of Stolen Goods - Blurring Books</a></p>
            <p><strong>2023</strong> - Art Hustler, Issue 1</p>
            <p><strong>2024</strong> - <a href="https://news.artnet.com/art-world/uhaul-gallery-stolen-from-work-2546344" target="_blank">Stealing the Show: A Roving U-Haul Is Exhibiting Stuff People Have Liberated From the Workplace - Artnet</a></p>
            <p><strong>2022</strong> - <a href="https://www.artnews.com/list/art-news/news/nyc-art-gallery-party-o-flahertys-the-patriot-1234634325/sculptures-and-darkness/" target="_blank">Sculptures and Darkness - ARTnews</a></p>
            <p><strong>2022</strong> - <a href="https://hyperallergic.com/748364/oflahertys-opening-draws-crowds-and-cops-in-fuck-you-to-landlords/" target="_blank">O'Flaherty's Opening Draws Crowds and Cops in 'Fuck You' to Landlords - Hyperallergic</a></p>
            <p><strong>2022</strong> - <a href="https://www.nytimes.com/2022/07/20/arts/design/oflahertys-gallery-east-village-art-party.html" target="_blank">O'Flaherty's Gallery: East Village Art Party - The New York Times</a></p>
            <p><strong>2022</strong> - <a href="https://www.culturedmag.com/article/2022/07/15/new-york-gallery-oflahertys-packed-the-streetand-the-wallsfor-the-patriot-opening" target="_blank">New York Gallery O'Flaherty's Packed the Street—and the Walls—for 'The Patriot' Opening - Cultured Mag</a></p>
        </div>  
        <h2 onclick="toggleSection('collections')">PUBLIC COLLECTIONS</h2>
        <div id="collections" class="section-content">
            <p><strong>2018</strong> - <a href="https://www.museumqualitynyc.com/permanent-collection" target="_blank">Museum Quality, Permanent Collection</a></p>
        </div>
    </div>
    <script>
        function toggleSection(sectionId) {
            const section = document.getElementById(sectionId);
            const header = event.currentTarget;    
            section.classList.toggle('visible');
            header.classList.toggle('open');
        }
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
                    // Create home loading screen like in about page
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
        window.onload = function() {
            // Show loading screen for 3 seconds
            setTimeout(() => {
                document.getElementById('loading-screen').style.opacity = '0';
                document.getElementById('loading-screen').style.transition = 'opacity 0.5s ease';
                setTimeout(() => {
                    document.getElementById('loading-screen').style.display = 'none';
                    document.getElementById('cv-content').style.display = 'block';
                    // Auto-open first section after loading
                    const firstSection = document.querySelector('h2');
                    if (firstSection) {
                        const sectionId = firstSection.getAttribute('onclick').match(/['"](.*)['"]/)[1];
                        toggleSection(sectionId);
                        firstSection.classList.add('open');
                    }
                }, 500);
            }, 3000);
        };
    </script>
</body>
</html>