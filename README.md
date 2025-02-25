<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouTube Music Player</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background: #000; color: white; }
        .player-container { margin-top: 20px; }
        img { width: 300px; border-radius: 10px; }
        button { padding: 10px 20px; margin: 10px; border: none; cursor: pointer; font-size: 16px; }
        #play { background: green; color: white; }
        #pause { background: red; color: white; }
    </style>
</head>
<body>

    <h2>YouTube Audio Player</h2>
    <div class="player-container">
        <img id="thumbnail" src="" alt="Thumbnail">
        <br>
        <button id="play">▶ Play</button>
        <button id="pause">⏸ Pause</button>
    </div>

    <iframe id="player" width="0" height="0" src="https://www.youtube.com/embed/3JZ_D3ELwOQ?autoplay=0&controls=0&loop=1" frameborder="0" allow="autoplay"></iframe>

    <script>
        let videoId = "3JZ_D3ELwOQ"; // YouTube Video ID (change this to play another song)

        document.getElementById('play').addEventListener('click', function() {
            document.getElementById('player').src = `https://www.youtube.com/embed/${videoId}?autoplay=1&controls=0&loop=1`;
        });

        document.getElementById('pause').addEventListener('click', function() {
            document.getElementById('player').src = `https://www.youtube.com/embed/${videoId}?autoplay=0&controls=0&loop=1`;
        });

        fetch(`https://noembed.com/embed?url=https://www.youtube.com/watch?v=${videoId}`)
            .then(response => response.json())
            .then(data => document.getElementById('thumbnail').src = data.thumbnail_url);
    </script>

</body>
</html>
