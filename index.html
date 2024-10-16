
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Reproductor Avanzado Winamp</title>
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #0d0d0d;
            margin: 0;
            color: #ffffff;
            overflow: hidden;
            position: relative;
        }
        .background-logo {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: contain;
            background-repeat: no-repeat;
            background-position: center;
            opacity: 0.1;
            z-index: -1;
        }
        .bubbles {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -2;
        }
        .bubble {
            position: absolute;
            bottom: -50px;
            background-color: rgba(0, 198, 255, 0.5);
            border-radius: 50%;
            animation: rise 10s infinite;
            animation-timing-function: ease-in-out;
        }
        @keyframes rise {
            0% {
                transform: translateY(0) scale(1);
                opacity: 0;
            }
            50% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) scale(0.5);
                opacity: 0;
            }
        }
        .player {
            width: 100%;
            max-width: 300px;
            background-color: #1c1c1c;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 20px;
            position: relative;
            z-index: 1;
        }
        .header {
            width: 100%;
            text-align: center;
            font-size: 24px;
            font-weight: bold;
            margin-bottom: 20px;
            background: linear-gradient(to right, #00c6ff, #0072ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        .logo-display picture {
            width: 100px;
            height: 100px;
            display: block;
            margin-bottom: 20px;
        }
        .controls {
            display: flex;
            justify-content: center;
            width: 100%;
            margin-bottom: 20px;
        }
        .controls button {
            background-color: #292929;
            border: 2px solid #00c6ff;
            margin: 0 10px;
            padding: 10px 20px;
            color: #00c6ff;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, color 0.3s;
        }
        .controls button:hover {
            background-color: #00c6ff;
            color: #292929;
        }
        .display {
            width: 100%;
            text-align: center;
            margin-bottom: 20px;
            position: relative;
        }
        .display #trackInfo {
            font-size: 18px;
            margin-bottom: 10px;
        }
        .display #time {
            font-size: 16px;
        }
        .playlist {
            width: 100%;
            max-height: 300px;
            overflow-y: auto;
            scrollbar-width: thin;
            scrollbar-color: #00c6ff #292929;
        }
        .playlist ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }
        .playlist li {
            display: flex;
            align-items: center;
            background-color: #292929;
            margin: 5px 0;
            padding: 10px;
            cursor: pointer;
            border-radius: 5px;
            transition: background-color 0.3s;
        }
        .playlist li:hover {
            background-color: #00c6ff;
        }
        .playlist img {
            width: 50px;
            height: 50px;
            margin-right: 15px;
            border-radius: 5px;
        }
        .playlist::-webkit-scrollbar {
            width: 8px;
        }
        .playlist::-webkit-scrollbar-track {
            background: #292929;
        }
        .playlist::-webkit-scrollbar-thumb {
            background-color: #00c6ff;
            border-radius: 10px;
            border: 2px solid #292929;
        }
    </style>
</head>
<body>
    <div class="background-logo" id="backgroundLogo"></div>
    <div class="bubbles"></div>
    <div class="player">
        <div class="header">RADIOS DE CURACAVI</div>
        <div class="logo-display" id="currentLogo">
            <picture>
                <source id="logoWebp" type="image/webp">
                <source id="logoPng" type="image/png">
                <img id="logoImg" alt="Logotipo de la estación de radio">
            </picture>
        </div>
        <div class="controls">
            <button onclick="stop()">Stop</button>
        </div>
        <div class="display">
            <div id="trackInfo">No track playing</div>
            <div id="time">00:00</div>
        </div>
        <div class="playlist">
            <ul id="playlist"></ul>
        </div>
    </div>
    <audio id="audioPlayer" src=""></audio>
    <script>
        function createBubbles() {
            const bubblesContainer = document.querySelector('.bubbles');
            for (let i = 0; i < 20; i++) {
                const bubble = document.createElement('div');
                bubble.classList.add('bubble');
                bubble.style.width = `${Math.random() * 30 + 20}px`;
                bubble.style.height = bubble.style.width;
                bubble.style.left = `${Math.random() * 100}%`;
                bubble.style.animationDuration = `${Math.random() * 5 + 5}s`;
                bubble.style.animationDelay = `${Math.random() * 5}s`;
                bubblesContainer.appendChild(bubble);
            }
        }

        let audioPlayer = document.getElementById('audioPlayer');
        let trackInfo = document.getElementById('trackInfo');
        let time = document.getElementById('time');
        let backgroundLogo = document.getElementById('backgroundLogo');
        let playlistElement = document.getElementById('playlist');
        let currentLogo = document.getElementById('currentLogo');

        let tracks = [];

        function loadM3U(url) {
            fetch(url)
                .then(response => response.text())
                .then(data => {
                    const lines = data.split('\n');
                    for (let i = 0; i < lines.length; i++) {
                        if (lines[i].startsWith('#EXTINF')) {
                            const title = lines[i].split(',')[1];
                            const src = lines[i + 1].trim();
                            const logo = lines[i + 2] && lines[i + 2].startsWith('#EXTLOGO') ? lines[i + 2].split(':')[1].trim() : '';
                            tracks.push({ title, src, logo });
                            addTrackToPlaylist(title, logo, tracks.length - 1);
                        }
                    }
                });
        }

        function addTrackToPlaylist(title, logo, index) {
            const li = document.createElement('li');
            const img = document.createElement('img');
            img.src = logo;
            li.appendChild(img);
            li.appendChild(document.createTextNode(title));
            li.onclick = () => selectTrack(index);
            playlistElement.appendChild(li);
        }

        function selectTrack(index) {
            currentTrack = index;
            loadTrack(currentTrack);
            audioPlayer.play();
        }

        function loadTrack(index) {
            audioPlayer.src = tracks[index].src;
            trackInfo.textContent = tracks[index].title;

            const logoUrl = tracks[index].logo;
            document.getElementById('logoWebp').srcset = logoUrl.replace(/\.\w+$/, '.webp');
            document.getElementById('logoPng').srcset = logoUrl.replace(/\.\w+$/, '.png');
            document.getElementById('logoImg').src = logoUrl;

            backgroundLogo.style.backgroundImage = `url(${logoUrl})`;
        }

        function stop() {
            audioPlayer.pause();
            audioPlayer.currentTime = 0;
            trackInfo.textContent = 'No track playing';
            document.getElementById('logoImg').src = '';
            document.getElementById('logoWebp').srcset = '';
            document.getElementById('logoPng').srcset = '';
        }

        audioPlayer.addEventListener('timeupdate', function() {
            let minutes = Math.floor(audioPlayer.currentTime / 60);
            let seconds = Math.floor(audioPlayer.currentTime % 60);
            time.textContent = `${minutes}:${seconds < 10 ? '0' + seconds : seconds}`;
        });

        loadM3U('https://raw.githubusercontent.com/Ruminot21/Play.m3u/refs/heads/main/Radios.m3u'); // Cambia esto por la ruta correcta de tu archivo M3U
        createBubbles(); // Llamar a la función para crear burbujas
    </script>
</body>
</html>
