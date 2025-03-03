---
layout: null
title: Contact
permalink: /contact/
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Terminal</title>
    <style>
        * {margin: 0; padding: 0; box-sizing: border-box; font-family: 'Courier New', monospace;}
        body {background-color: #000; margin: 0; padding: 0; overflow: hidden;}
        .terminal {width: 650px; height: 650px; position: absolute; top: 270px; left: 50%; transform: translateX(-50%); overflow: hidden; background-color: #000; color: #00ff00; display: none; padding: 30px;}
        .terminal-content {width: 100%; height: 100%; overflow-y: auto; overflow-x: hidden; padding-bottom: 30px;}
        .line {white-space: pre-wrap; min-height: 1em; line-height: 1.5;}
        .cursor {display: inline-block; width: 0.6em; height: 1.2em; background-color: #00ff00; vertical-align: text-bottom; animation: blink 1s step-end infinite; margin-left: 0;}
        .input-area {position: fixed; bottom: 30px; left: 50%; transform: translateX(-50%); width: 590px; display: flex; align-items: center; background-color: #000; padding: 10px 0;}
        #terminal-input {background-color: transparent; color: #00ff00; border: none; outline: none; font-family: 'Courier New', monospace; font-size: inherit; width: 100%; padding: 0; margin: 0; caret-color: #00ff00;}
        #cursor-placeholder {display: none;}
        @keyframes blink {0%, 100% { opacity: 1; } 50% { opacity: 0; }}
        a {color: #00ff00; text-decoration: none;}
        a:hover {text-decoration: underline;}
        .hidden {display: none;}
        .home-button {position: fixed; top: 124px; left: 20px; background: black; color: #00ff00; font-family: "Courier New", Courier, monospace; font-size: 16px; font-weight: bold; cursor: pointer; text-shadow: 0 0 5px #00ff00; padding: 5px 10px; z-index: 2000; border: 2px solid #00ff00; box-shadow: 0 0 10px #00ff00; transition: all 0.3s ease;}
        .home-button:hover {color: #ffffff; text-shadow: 0 0 10px #00ff00; transform: scale(1.05);}
        .loading-screen {position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: black; display: flex; flex-direction: column; align-items: center; justify-content: center; z-index: 3000; padding-top: 250px;}
        #loading-text {color: #00ff00; font-size: 20px; margin-bottom: 20px; font-family: "Courier New", Courier, monospace; text-transform: uppercase;}
        .progress-bar {width: 300px; height: 6px; background: #333; position: relative;}
        .progress {position: absolute; left: 0; top: 0; height: 100%; width: 0; background: #00ff00; transition: width 0.3s ease;}
        .home-loading-screen {position: fixed; top: 0; left: 0; width: 100%; height: 100%; display: flex; flex-direction: column; justify-content: flex-start; align-items: center; background-color: black; z-index: 3000; opacity: 0; visibility: hidden; transition: opacity 0.5s ease; padding-top: 250px;}
        .home-loading-text {color: #00ff00; font-size: 24px; margin-bottom: 20px; font-family: "Courier New", Courier, monospace;}
        .home-loading-bar {width: 700px; height: 10px; background: rgba(0, 0, 0, 0.8); border: 1px solid #00ff00; position: relative; overflow: hidden;}
        .home-bar-fill {position: absolute; left: 0; top: 0; height: 100%; width: 0; background-color: #00ff00; transition: width 5s linear;}
        .home-bar-fill.animate {width: 100%;}
        @keyframes glitch {0% { opacity: 1; transform: translateX(0); } 20% { opacity: 0.8; transform: translateX(-10px); } 40% { opacity: 1; transform: translateX(10px); } 60% { opacity: 0.8; transform: translateX(-5px); } 80% { opacity: 1; transform: translateX(5px); } 100% { opacity: 1; transform: translateX(0); }}
        .glitch {animation: glitch 0.5s forwards;}
        @keyframes powerDown {0% { opacity: 1; } 100% { opacity: 0; }}
        .power-down {animation: powerDown 1s forwards;}
        body.transitioning .home-loading-screen {visibility: visible !important; opacity: 1 !important; display: flex !important; z-index: 9999 !important;}
    </style>
</head>
<body>
    <!-- Loading Screen -->
    <div class="loading-screen" id="loading-screen">
        <div id="loading-text">CONTACT TERMINAL LOADING...</div>
        <div class="progress-bar">
            <div class="progress" id="loading-progress"></div>
        </div>
    </div> 
    <!-- Return to Home Loading Screen -->
    <div class="home-loading-screen" id="home-loading-screen">
        <div class="home-loading-text" id="home-loading-text">Navigating home...</div>
        <div class="home-loading-bar">
            <div class="home-bar-fill" id="home-bar-fill"></div>
        </div>
    </div>  
    <div class="terminal" id="terminal">
        <div class="terminal-content" id="terminalContent">
            <!-- Lines will be added here by JavaScript -->
        </div>
        <div class="input-area">
            <input type="text" id="terminal-input" autofocus>
            <span id="cursor-placeholder"></span>
        </div>
    </div>
    <!-- Return to Home Button -->
    <button onclick="returnToHome()" class="home-button">&lt; Return to Home</button>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            const terminalContent = document.getElementById('terminalContent');
            const input = document.getElementById('terminal-input');
            const terminal = document.getElementById('terminal');
            const loadingScreen = document.getElementById('loading-screen');
            const loadingProgress = document.getElementById('loading-progress');
            let currentPrompt = "";  // Empty prompt        
            // Start the loading animation
            let width = 0;
            const loadingInterval = setInterval(() => {
                if (width >= 100) {
                    clearInterval(loadingInterval);
                    loadingScreen.style.opacity = '0';
                    loadingScreen.style.transition = 'opacity 0.5s ease';
                    setTimeout(() => {
                        loadingScreen.style.display = 'none';
                        terminal.style.display = 'block';
                        startTerminal();
                    }, 500);
                } else {
                    width += 1;
                    loadingProgress.style.width = width + '%';
                }
            }, 30);
            function startTerminal() {
                // Commands and scripts to run
                const initialCommands = [
                    { text: "Welcome stranger, I'm PAL3000 here to assist you.", type: "output", delay: 50 },
                    { text: "", type: "newline" },
                    { text: "I can provide contact information upon request.", type: "output", delay: 50 },
                    { text: "", type: "newline" },
                    { text: "Type 'help' to see available commands.", type: "output", delay: 50 },
                    { text: "", type: "newline" }
                ];      
                // Start the initial animation
                runCommandSequence(initialCommands); 
                // Make sure the input is always focused
                document.addEventListener('click', function() {
                    input.focus();
                });
                input.addEventListener('keydown', function(event) {
                    if (event.key === 'Enter') {
                        const command = input.value.trim().toLowerCase();
                        input.value = '';
                        // Add the command to the terminal without showing the prompt
                        const commandLine = document.createElement('div');
                        commandLine.className = 'line command';
                        commandLine.textContent = command;
                        terminalContent.appendChild(commandLine);
                        addLine('', 'newline');
                        // Process the command
                        processCommand(command);
                        // Scroll to bottom
                        terminalContent.scrollTop = terminalContent.scrollHeight;
                    }
                });
            }
            function processCommand(command) {
                let skipPrompt = false;
                switch(command) {
                    case 'help':
                        showHelp();
                        break;
                    case 'contact':
                        showContact();
                        break;
                    case 'email':
                        showEmail();
                        break;
                    case 'instagram':
                        showInstagram();
                        break;
                    case 'objects':
                    case 'everythings':
                    case 'design':
                        showObjects();
                        break;
                    case 'music':
                    case 'soundcloud':
                        showMusic();
                        break;
                    case 'about':
                        showAbout();
                        break;
                    case 'clear':
                        clearTerminal();
                        break;
                    case 'secret':
                        showSecret();
                        break;
                    case '':
                        // Do nothing for empty command
                        break;
                    default:
                        addLine(`Command not found: ${command}. Type 'help' for available commands.`, 'error');
                        addLine('', 'newline');
                }
                // No need to add prompt anymore with fixed input
            }
            function showContact() {
                addLine('Loading contact information...', 'output');
                addLine('', 'newline');
                setTimeout(() => {
                    addLine('Discreet, intelligent, good hands, bad habits.', 'output');
                    addLine('Seeking serious inquiries, stolen moments, unwritten futures.', 'output');
                    addLine('', 'newline');
                    addLine('Email: kohlman.harshbarger@gmail.com', 'output');
                    addLine('Instagram: https://instagram.com/kohlman.harshbarger', 'output');
                    addLine('Objects: https://everythings.world', 'output');
                    addLine('Music: https://soundcloud.com/kohlmanh', 'output');
                    addLine('', 'newline');
                    // Add a new prompt after the delay
                    addLine(currentPrompt, 'prompt', false, true);
                }, 800);               
                // Return to prevent adding another prompt immediately
                return true;
            }          
            function showEmail() {
                addLine('Email: kohlman.harshbarger@gmail.com', 'output');
                addLine('', 'newline');
            }          
            function showInstagram() {
                addLine('Instagram: https://instagram.com/kohlman.harshbarger', 'output');
                addLine('', 'newline');
            }         
            function showObjects() {
                addLine('Objects: https://everythings.world', 'output');
                addLine('', 'newline');
            }         
            function showMusic() {
                addLine('Music: https://soundcloud.com/kohlmanh', 'output');
                addLine('', 'newline');
            }          
            function showAbout() {
                addLine('Discreet, intelligent, good hands, bad habits.', 'output');
                addLine('Seeking serious inquiries, stolen moments, unwritten futures. No time wasters, no cops.', 'output');
            }   
            function showHelp() {
                addLine('Available commands:', 'output');
                addLine('  email     - Show email address', 'output');
                addLine('  instagram - Show Instagram profile', 'output');
                addLine('  objects   - Show design works', 'output');
                addLine('  music     - Show SoundCloud profile', 'output');
                addLine('  about     - Show about information', 'output');
                addLine('  clear     - Clear the terminal', 'output');
                addLine('', 'newline');
            }  
            function showSecret() {
                addLine('You found a secret command.', 'output');
                addLine('', 'newline');
                addLine(`
         _..._
       .'     '.
      /    .-""-\\
     /   .'     )
     |  /      /|
     | |      / |
     | \\     /  |
     |  '.  /   |
      \\   '    /
       '.___..'
`, 'output');
                addLine('', 'newline');
                addLine('The whole moon and the entire sky', 'output');
                addLine('are reflected in one cumdrop on the ass.', 'output');
                addLine('', 'newline');
            }     
            function clearTerminal() {
                while (terminalContent.firstChild) {
                    terminalContent.removeChild(terminalContent.firstChild);
                }
            }      
            function addLine(text, className, withCursor = false, isFinalPrompt = false) {
                // Don't add empty lines when there's already an empty line at the end
                if (text === '' && className === 'newline') {
                    const lastChild = terminalContent.lastChild;
                    if (lastChild && lastChild.textContent === '') {
                        return;
                    }
                }        
                const line = document.createElement('div');
                line.className = 'line ' + className;      
                if (className === 'prompt') {
                    currentPrompt = text;      
                    if (isFinalPrompt) {
                        // We don't need this with fixed input area
                        return;
                    }
                } 
                if (withCursor) {
                    const textSpan = document.createElement('span');
                    textSpan.textContent = text;
                    line.appendChild(textSpan);     
                    const cursor = document.createElement('span');
                    cursor.className = 'cursor';
                    line.appendChild(cursor);
                } else {
                    line.textContent = text;
                }  
                terminalContent.appendChild(line);
                terminalContent.scrollTop = terminalContent.scrollHeight;
            }
            async function runCommandSequence(commands) {
                for (const cmd of commands) {
                    if (cmd.type === 'prompt') {
                        currentPrompt = cmd.text;     
                        if (cmd.waitForInput) {
                            // We don't need this anymore with fixed input area
                        } else {
                            addLine(cmd.text, 'prompt');
                        }
                    } else if (cmd.type === 'command') {
                        await typeText(cmd.text, cmd.delay || 50);
                    } else if (cmd.type === 'output' || cmd.type === 'newline') {
                        if (cmd.delay) {
                            await sleep(cmd.delay);
                        }
                        addLine(cmd.text, cmd.type);
                    }
                }      
                // Focus the input when done
                input.focus();
            }    
            async function typeText(text, delay) {
                const line = document.createElement('div');
                line.className = 'line command';
                terminalContent.appendChild(line);   
                for (let i = 0; i < text.length; i++) {
                    line.textContent += text[i];
                    await sleep(delay);
                }
            } 
            function sleep(ms) {
                return new Promise(resolve => setTimeout(resolve, ms));
            }
            // Keep input focused and handle window resizing
            window.addEventListener('resize', () => {
                window.scrollTo(0, document.body.scrollHeight);
            }); 
            input.focus();
        });
        // Return to Home function with loading transition
        function returnToHome() {
            // Add transitioning class to body
            document.body.classList.add('transitioning');            
            // Apply glitch effect
            document.body.classList.add('glitch');            
            setTimeout(() => {
                document.body.classList.remove('glitch');               
                // Hide terminal and button
                document.getElementById('terminal').style.display = 'none';
                document.querySelector('.home-button').style.display = 'none';                
                // Show the home loading screen
                const homeLoadingScreen = document.getElementById('home-loading-screen');
                homeLoadingScreen.style.visibility = 'visible';
                homeLoadingScreen.style.opacity = '1';
                homeLoadingScreen.style.display = 'flex';           
                // Expanded list of fun loading messages
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
                    "Turning on the night mode..."
                ];         
                // Start animation with a slight delay to ensure screen is visible
                setTimeout(() => {
                    document.getElementById('home-bar-fill').classList.add('animate');                 
                    // Update loading text with random messages
                    let index = 0;
                    const shuffledMessages = [...loadingMessages].sort(() => 0.5 - Math.random());
                    function updateLoadingText() {
                        if (index < 5) {
                            document.getElementById('home-loading-text').innerText = shuffledMessages[index];
                            index++;
                        }
                    }                   
                    const textInterval = setInterval(updateLoadingText, 800);                  
                    // Navigate to home page
                    setTimeout(() => {
                        clearInterval(textInterval);
                        window.location.href = "/";
                    }, 5000);
                }, 100);
            }, 500);
        }
    </script>
</body>
</html>