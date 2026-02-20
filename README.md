<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>I'm Sorry! 🥺</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #fce4ec; /* Soft Pink */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            text-align: center;
        }

        #container {
            padding: 20px;
        }

        img {
            height: 200px;
            margin-bottom: 20px;
            border-radius: 15px;
        }

        h1 {
            color: #d81b60;
            font-size: 2rem;
        }

        .buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            align-items: center;
            margin-top: 20px;
        }

        button {
            padding: 15px 25px;
            font-size: 1.2rem;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        #yesBtn {
            background-color: #4caf50;
            color: white;
        }

        #noBtn {
            background-color: #f44336;
            color: white;
            position: relative;
        }

        .success-msg {
            display: none;
        }
    </style>
</head>
<body>

    <div id="container">
        <img id="mainGif" src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueG56Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3ImZXA9djFfaW50ZXJuYWxfZ2lmX2J5X2lkJmN0PWc/3o7TKVUn7iM8FMEU24/giphy.gif" alt="Cute GIF">
        
        <h1 id="question">Sorry... Forgive me? 🥺</h1>

        <div class="buttons" id="buttonGroup">
            <button id="yesBtn">Yes</button>
            <button id="noBtn">No</button>
        </div>
    </div>

    <script>
        const phrases = [
            "No",
            "Pookie Sorry...",
            "Please????",
            "If you don't I'll be Very sad..",
            "REALLY SAD.... 🥺",
            "Don't do this to me 👉👈",
            "Last Chance....?"
        ];

        // Replace these with links to different GIFs for each stage
        const gifs = [
            "https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueG56Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3ImZXA9djFfaW50ZXJuYWxfZ2lmX2J5X2lkJmN0PWc/3o7TKVUn7iM8FMEU24/giphy.gif", // initial
            "https://media.giphy.com/media/7SF5scGB2AFrO/giphy.gif", // sad
            "https://media.giphy.com/media/OPU6wUKARAyXG/giphy.gif", // sadder
            "https://media.giphy.com/media/qQdL532ZANUSMAFBAS/giphy.gif", // crying
            "https://media.giphy.com/media/26BRv0ThflsHCqCg8/giphy.gif"  // desperate
        ];

        let noCount = 0;
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const mainGif = document.getElementById('mainGif');
        const question = document.getElementById('question');

        noBtn.addEventListener('click', () => {
            noCount++;
            
            // 1. Change text on No button
            if (noCount < phrases.length) {
                noBtn.innerText = phrases[noCount];
            }

            // 2. Make Yes button bigger
            const currentSize = parseFloat(window.getComputedStyle(yesBtn).fontSize);
            yesBtn.style.fontSize = (currentSize * 1.5) + 'px';
            yesBtn.style.padding = (currentSize * 1.2) + 'px';

            // 3. Change GIF
            if (noCount < gifs.length) {
                mainGif.src = gifs[noCount];
            }

            // 4. THE DODGE (on the last chance)
            if (noCount >= phrases.length - 1) {
                noBtn.style.position = 'absolute';
                moveButton();
                noBtn.addEventListener('mouseover', moveButton);
            }
        });

        function moveButton() {
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
            noBtn.style.left = `${x}px`;
            noBtn.style.top = `${y}px`;
        }

        yesBtn.addEventListener('click', () => {
            document.getElementById('buttonGroup').style.display = 'none';
            question.innerText = "Yay! Besties again! ❤️";
            mainGif.src = "https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHpueG56Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3R6Z3ImZXA9djFfaW50ZXJuYWxfZ2lmX2J5X2lkJmN0PWc/MDJ9IbxxvDUQM/giphy.gif"; // Happy GIF
        });
    </script>
</body>
</html>
