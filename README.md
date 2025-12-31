<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>For My Baby</title>
    <style>
        /* General Styles */
        body {
            margin: 0;
            font-family: 'Segoe UI', sans-serif;
            background: linear-gradient(135deg, #f2e9ff, #d6c7ff);
            color: #3a2d5c;
        }

        .container {
            max-width: 900px;
            margin: auto;
            padding: 40px 20px;
        }

        .card {
            background: #ffffffcc;
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 10px 25px rgba(90, 60, 150, 0.15);
            width: 100%;
            box-sizing: border-box;
        }

        h1, h2 {
            text-align: center;
            color: #5a3ea1;
        }

        h1 {
            font-size: 2.8rem;
        }

        h2 {
            font-size: 1.6rem;
        }

        p {
            line-height: 1.7;
            font-size: 1.05rem;
            white-space: pre-line; /* keeps line breaks */
        }

        .button {
            background: #c9b8ff;
            border: none;
            border-radius: 30px;
            padding: 12px 24px;
            font-size: 1rem;
            cursor: pointer;
            color: #3a2d5c;
            transition: all 0.3s ease;
            margin: 8px auto;
            display: block;
        }

        .button:hover {
            background: #b19cff;
            transform: scale(1.05);
        }

        .hidden {
            max-height: 0;
            opacity: 0;
            transform: translateY(10px);
            overflow: hidden;
            margin-top: 15px;
            font-style: italic;
            transition: max-height 0.8s ease, opacity 0.5s ease, transform 0.5s ease;
        }

        .hidden.show {
            max-height: none; /* removes cut-off for long messages */
            opacity: 1;
            transform: translateY(0);
        }

        .duck {
            font-size: 3rem;
            cursor: pointer;
            display: block;
            margin: 0 auto 10px;
            text-align: center;
        }

        footer {
            text-align: center;
            opacity: 0.7;
            margin-top: 40px;
            font-style: italic;
        }

        /* Mobile Responsive */
        @media (max-width: 600px) {
            .container {
                padding: 20px 10px;
            }

            h1 {
                font-size: 2rem;
            }

            h2 {
                font-size: 1.3rem;
            }

            .button {
                padding: 10px 20px;
                font-size: 0.9rem;
            }

            #hazbinDuck {
                width: 40%;
                max-width: 120px;
            }

            #lastMessage {
                text-align: center;
                padding: 0 10px;
                word-wrap: break-word;
            }
        }
    </style>

    <script>
        // Toggle open-when messages
        function toggleMessage(id) {
            const el = document.getElementById(id);
            if (!el) return;
            el.classList.toggle('show');
            el.dataset.opened = 'true';
            checkAllOpened();
            duckReact();
        }

        // Check if all messages are opened
        function checkAllOpened() {
            const messages = document.querySelectorAll('[id^="msg"]');
            const opened = Array.from(messages).every(m => m.dataset.opened === 'true');

            if (opened) {
                const final = document.getElementById('finalMessage');
                const last = document.getElementById('lastMessage');
                if (final) final.classList.add('show');
                if (last) last.classList.add('show');
            }
        }

        // Duck animation reaction
        function duckReact() {
            const duck = document.getElementById('hazbinDuck');
            if (!duck) return;
            duck.style.transform = 'scale(1.1) rotate(-3deg)';
            setTimeout(() => {
                duck.style.transform = 'scale(1) rotate(0deg)';
            }, 300);
        }

        // Duck click handler
        function duckClick() {
            const audio = document.getElementById('duckSound');
            const text = document.getElementById('duckText');
            if (audio) {
                audio.currentTime = 0;
                audio.play();
            }
            if (text) {
                text.style.opacity = '1';
                setTimeout(() => (text.style.opacity = '0.6'), 800);
            }
            duckReact();
        }
    </script>
</head>

<body>
    <div class="container">

        <!-- Duck Section -->
        <div class="card">
            <h1>heyyy babiiii!</h1>
            <p style="text-align: center;">I've been cooking this up for a few days along with the dictionary, I hope you didn't guess that I'm making you a website but there's still a message here.</p>
            <div style="text-align:center;">
                <img id="hazbinDuck" src="https://media.tenor.com/7hZ5dZKp2JQAAAAC/hazbin-hotel-duck.gif" alt="Hazbin Duck" />
                <span class="duck" onclick="duckClick()">🦆</span>
                <p id="duckText" style="font-size:0.9rem; opacity:0.6;">click me</p>
                <audio id="duckSound">
                    <source src="https://www.myinstants.com/media/sounds/duck-quack.mp3" type="audio/mpeg" />
                </audio>
            </div>
        </div>

        <!-- Open When Messages -->
        <div class="card">
            <h2>A few things I like about you</h2>
            <div style="text-align:center;">
                <button class="button" onclick="toggleMessage('msg1')">uno</button>
                <p id="msg1" class="hidden">How you always make me laugh when I’m sad - your stupid jokes, I laugh while crying. You somehow know exactly what to say or do to lift my mood. I love how you comfort me when I’m down or not in the mood, and how you respect it instead of forcing anything and honestly… the way you ragebait me on purpose just to hear you say that soft little “sorry” after? I can’t even stay mad - marupok</p>

                <button class="button" onclick="toggleMessage('msg2')">dos</button>
                <p id="msg2" class="hidden">How you reassure me when I overthink over little things - your change of typings, the feeling of you not liking me anymore. Even when my thoughts get messy and repetitive, you stay and assure me gently, like it’s never a bother even though I know it can be (hehe). You make my mind feel lighter without making me feel silly for worrying.</p>

                <button class="button" onclick="toggleMessage('msg3')">tre</button>
                <p id="msg3" class="hidden">How patient and understanding you are with me lalo na when I’m being stubborn about taking care of myself kapag may sakit na ako, inuubo, may bali etc or when you’re trying to stop me from doing something stupid like... fiddling with stuff when I'm bored. You don’t get mad or give up... you just stay, guide me, and care in the calmest way.</p>

                <button class="button" onclick="toggleMessage('msg4')">quattro</button>
                <p id="msg4" class="hidden">Your kindness, even from the very start - when friends pa lang tayo and even nung hindi pa kita ganun kilala I had a hunch na you were kind ; not the mayabang type ganun and you fit my standards without even trying, and that still amazes me. You felt like such a breath of fresh air — talking to you felt natural, you were sincere, and comforting in a way I didn’t even know I needed.</p>

                <button class="button" onclick="toggleMessage('msg5')">lima</button>
                <p id="msg5" class="hidden">The way you get excited about the most mundane things lalo na sa fixation mo sa ducks, hatsune miku, the shows you mentioned dati na you watch with Min Min, winning sa MLBB rounds niyo sa room, when I give you “mwa mwa’s,” and especially when I send you pictures - how you freak out and send all those cute reactions, I'd catch myself giggling over that. Weird pero seeing you light up over those little things makes my heart melt. One of my favorite things to see on you.</p>

                <button class="button" onclick="toggleMessage('msg6')">zes</button>
                <p id="msg6" class="hidden">How thoughtful you are. You do such small sweet things, not because you have to, but just because you want to and it feels the most when you do. Your effort, intention, love and care behind it just makes everything feel so special.</p>

                <button class="button" onclick="toggleMessage('msg7')">siete</button>
                <p id="msg7" class="hidden"> For simply being you, you don't try to fit in with any trend and standard - i like that about you, my nerdy baby. The most favorite person to talk to, laugh with, and think about without any reason other than the fact that you’re you.</p>
            </div>
        </div>

        <!-- Original Final Message -->
        <div class="card">
            <h2 id="finalMessage" class="hidden">Waittt, there's more !!!</h2>
        </div>

        <!-- New Last Message Section -->
        <div class="card">
            <h2>READ IT POOOOO</h2>
            <div id="lastMessage" class="hidden" style="text-align:center;">
                <p>hallooooo!</p>

                <p>all i want to say is thank you for making me feel happy, safe, and loved on days i didn’t. a huge thanks to me for being fc (feeling close), because if i wasn’t, our relationship wouldn’t have bloomed into this. tbh, whole goal ko talaga ng senior high school was to not fall in love with a classmate because i thought it was stupid, waste of time kasi all the boys in our section dati wasn't any of my type and yet here i am, making another letter, completely defeated by my own heart (your fault btw).</p>

                <p>i didn’t plan for you, i didn’t expect us to be anything other than being friends - best friends. you just slowly sneaked into my life until suddenly you were everywhere (⁠ ⁠╹⁠▽⁠╹⁠ ⁠) in my thoughts, my routines, my jokes, my quiet moments and now I'm here, thinking back how insane our transition was lalo na sa nicknames - from dave, dabe, dabe dabe dabe, daveing under water (fav), dabe na mataray/masungit to my baby, love love, love, babi, babe etc.</p>

                <p>thank you for loving me the way you do (⁠｡⁠•́⁠︿⁠•̀⁠｡⁠) softly, patiently, consistently. thank you for holding my hand, for saying “pahinga” when i forget to rest, for worrying about me even when i’m being stubborn and pushing me to do what's best for me. thank you for choosing me even on days i’m messy, dramatic, clingy, or too much.</p>

                <p>loving you feels chaotic in the best way. it makes my heart race, my brain short-circuit, and my smile appears out of nowhere. but at the same time, it feels safe. like i finally found a place where i can just exist and be loved for it.</p>

                <p>i don’t know where this will take us, maybe I'll sagot you na to be my boyfriend, part ways (don't, please I'm not ready for this yet) but i know this much... i want it to be you (like i said dati I'm not giving up on us) through the laughter, the chaos, the soft moments, the bad days, the good days, all of it.</p>

                <p>im ending this message with a kiss (⁠っ⁠˘⁠з⁠(⁠˘⁠⌣⁠˘⁠ ⁠) and a hug ＼⁠(⁠^⁠o⁠^⁠)⁠／</p>
            </div>
        </div>

        <footer>I love you, always my mataray na dabe :P</footer>
    </div>
</body>
