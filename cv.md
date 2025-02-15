---
layout: cv
title: CV
permalink: /cv/
---

<head>
    <link rel="stylesheet" href="/assets/css/terminal.css">
</head>

<body>
    <div class="loading-screen" id="loading-screen">
        <div>CV LOADING...</div>
        <div class="loading-bar" id="loading-bar"></div>
    </div>
    <div class="container" id="cv-content" style="display:none;">
        <p><strong>Kohlman Harshbarger</strong></p>
        <p>Born 1993, Boston, MA | Lives and works in Brooklyn, NY</p>
        <button onclick="returnToHome()" class="home-button">&lt; Return to Home</button>
         <h2 data-target="solo-exhibitions">SOLO EXHIBITIONS</h2>
        <div id="solo-exhibitions" class="hidden">
            <p><strong>2024</strong> - Cute Kills, Preachers Valley, New York, NY</p>
        </div>
              <h2 data-target="group-exhibitions">GROUP EXHIBITIONS</h2>
        <div id="group-exhibitions" class="hidden">
            <p><strong>2024</strong> - <a href="https://www.coreypresha.com/cpp/holiday-market" target="_blank">Holiday Market, Portal 5</a>, New York, NY</p>
            <p><strong>2024</strong> - Holiday Market, <a href="https://hesseflatow.com" target="_blank">Hesse Flatow</a>, New York, NY</p>
            <p><strong>2024</strong> - The Show of Stolen Goods, <a href="https://www.instagram.com/uhaul_gallery/" target="_blank">U-Haul Gallery</a>, New York, NY</p>
            <p><strong>2024</strong> - SPIT II, Preachers Valley, New York, NY</p>
            <p><strong>2024</strong> - Rathaus, 324 E 14th, New York, NY</p>
            <p><strong>2023</strong> - <a href="https://www.underlandgallery.com/events-past/prixfixe" target="_blank">Prix Fixe, Underland Gallery</a>, Brooklyn, NY</p>
            <p><strong>2023</strong> - Spit, Preacher’s Valley, New York, NY</p>
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
     <h2 data-target="lectures">LECTURES AND WORKSHOPS</h2>
        <div id="lectures" class="hidden">
            <p><strong>2023</strong> - <a href="https://allstnyc.com" target="_blank">Nothing But Trouble, Artist Talk, All Street Gallery</a>, New York, NY</p>
            <p><strong>2018</strong> - <a href="https://www.artshackbrooklyn.org" target="_blank">Artist Workshop, ArtShack</a>, Brooklyn, NY</p>
        </div>
       <h2 data-target="press">PRESS AND PRINTED PUBLICATIONS</h2>
        <div id="press" class="hidden">
            <p><strong>2024</strong> - <a href="https://www.blurringbooks.com/book/the-show-of-stolen-goods" target="_blank">The Show of Stolen Goods - Blurring Books</a></p>
            <p><strong>2023</strong> - Art Hustler, Issue 1</p>
            <p><strong>2024</strong> - <a href="https://news.artnet.com/art-world/uhaul-gallery-stolen-from-work-2546344" target="_blank">Stealing the Show: A Roving U-Haul Is Exhibiting Stuff People Have Liberated From the Workplace - Artnet</a></p>
            <p><strong>2022</strong> - <a href="https://www.artnews.com/list/art-news/news/nyc-art-gallery-party-o-flahertys-the-patriot-1234634325/sculptures-and-darkness/" target="_blank">Sculptures and Darkness - ARTnews</a></p>
            <p><strong>2022</strong> - <a href="https://hyperallergic.com/748364/oflahertys-opening-draws-crowds-and-cops-in-fuck-you-to-landlords/" target="_blank">O’Flaherty’s Opening Draws Crowds and Cops in ‘Fuck You’ to Landlords - Hyperallergic</a></p>
            <p><strong>2022</strong> - <a href="https://www.nytimes.com/2022/07/20/arts/design/oflahertys-gallery-east-village-art-party.html" target="_blank">O’Flaherty’s Gallery: East Village Art Party - The New York Times</a></p>
            <p><strong>2022</strong> - <a href="https://www.culturedmag.com/article/2022/07/15/new-york-gallery-oflahertys-packed-the-streetand-the-wallsfor-the-patriot-opening" target="_blank">New York Gallery O’Flaherty’s Packed the Street—and the Walls—for ‘The Patriot’ Opening - Cultured Mag</a></p>
        </div>
          <h2 data-target="collections">PUBLIC COLLECTIONS</h2>
        <div id="collections" class="hidden">
            <p><strong>2018</strong> - <a href="https://www.museumqualitynyc.com/permanent-collection" target="_blank">Museum Quality, Permanent Collection</a></p>
        </div>
    </div>
    <script>
           // Handle collapsible sections
        document.addEventListener("DOMContentLoaded", function () {
            const headers = document.querySelectorAll("h2");
            headers.forEach(header => {
                header.addEventListener("click", function () {
                    const section = document.getElementById(header.getAttribute("data-target"));
                    if (section) {
                        section.classList.toggle("hidden");
                        header.classList.toggle("open");
                    }
                });
            });
        });
function returnToHome() {
    const body = document.body;
    // Apply glitch effect
    body.classList.add('glitch');
    // Wait for glitch, then blackout
    setTimeout(() => {
        body.classList.remove('glitch');
        body.classList.add('power-down');
        // Wait for blackout, then remove CV loader and replace with home loading
        setTimeout(() => {
            // Curated list of absurd and glitchy loading messages
            const loadingMessages = [
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
                "Turning on the night mode...",
                "Launching pigeons...",
                "Reading fine print...",
                "Charging portal battery...",
                "Verifying cookies...",
                "Rebooting matrix...",
                "Allocating nostalgia buffer...",
                "Disabling gravity...",
                "Compiling quantum entanglement...",
                "Synthesizing cozy...",
                "Realigning chakras...",
                "Flattening spaghetti code...",
                "Decrypting passwords...",
                "Replacing bad choices...",
                "Defrosting universe...",
                "Bribing the loading bar...",
                "Applying vaporwave filter...",
                "Negotiating with WiFi router...",
                "Respawning home button...",
                "Summoning parallel universe...",
                "Enhancing chill...",
                "Deleting buffering issues...",
                "Processing emotions...",
                "Unboxing paradoxes...",
                "Resetting timeline...",
                "Censoring bad tweets...",
                "Downloading tomorrow...",
                "Rendering void...",
                "Disassembling atoms...",
                "Scanning for hidden files...",
                "Running final simulation...",
                "Splicing multiverse...",
                "Decoding lost messages...",
                "Erasing fingerprints...",
                "Decrypting past mistakes...",
                "Analyzing deja vu...",
                "Restoring factory settings...",
                "Performing quantum rollback...",
                "Rewiring neural pathways...",
                "Reversing entropy...",
                "Activating infinite loop...",
                "Distorting spacetime...",
                "Verifying alternate timeline...",
                "Adjusting glitch coefficient...",
                "Recalibrating event horizon...",
                "Initiating self-awareness...",
                "Patching holes in reality...",
            ];
            document.body.innerHTML = `
                <div class="home-loading-screen">
                    <div class="home-loading-text" id="loading-text">LOADING HOME...</div>
                    <div class="home-loading-bar">
                        <div class="home-bar-fill"></div>
                    </div>
                </div>
            `;
            // Animate home loading bar
            setTimeout(() => {
                document.querySelector('.home-bar-fill').classList.add('animate');
            }, 100);
            // Randomly select messages for this session
            let displayedMessages = [];
            for (let i = 0; i < 5; i++) {
                let randomIndex = Math.floor(Math.random() * loadingMessages.length);
                displayedMessages.push(loadingMessages[randomIndex]);
            }
            let index = 0;
            function updateLoadingText() {
                if (index < displayedMessages.length) {
                    document.getElementById("loading-text").innerText = displayedMessages[index];
                    index++;
                }
            }
            // Change text every 800ms (adjust for speed)
            const textInterval = setInterval(updateLoadingText, 800);
            // Stop interval and redirect after loading
            setTimeout(() => {
                clearInterval(textInterval);
                window.location.href = "/";
            }, 5000);
        }, 1000);
    }, 500);
}
        window.onload = function() {
            let bar = document.getElementById('loading-bar');
            let loadingScreen = document.getElementById('loading-screen');
            let cvContent = document.getElementById('cv-content');
            bar.style.width = '100%';
            setTimeout(() => {
                loadingScreen.style.opacity = '0';
                setTimeout(() => {
                    loadingScreen.style.display = 'none';
                    cvContent.style.display = 'block';
                }, 500);
            }, 3000);
        };
    </script>
</body>