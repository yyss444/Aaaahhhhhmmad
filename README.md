<!DOCTYPE html>
<html>
<head>
    <title>Внимание!</title>
    <style>
        body { 
            background: black; 
            margin: 0; 
            height: 100vh; 
            color: white; 
            text-align: center; 
            font-family: Arial;
            padding-top: 45vh;
        }
    </style>
</head>
<body>
    <div id="message">Экран взорвётся через: <span id="countdown">10</span></div>
    
    <audio id="sound" controls loop style="display:none;">
        <source src="https://assets.mixkit.co/sfx/preview/mixkit-alarm-digital-clock-beep-989.mp3" type="audio/mpeg">
    </audio>

    <script>
        // Включаем звук по клику (иначе не сработает на iOS/Android)
        document.body.addEventListener('click', () => {
            const sound = document.getElementById("sound");
            sound.volume = 1.0;
            sound.play();
        });

        // Обратный отсчёт
        let seconds = 10;
        const timer = setInterval(() => {
            seconds--;
            document.getElementById("countdown").textContent = seconds;
            
            if (seconds <= 0) {
                clearInterval(timer);
                document.body.innerHTML = '<h1 style="color: red;">ПОПАЛСЯ! 😂</h1>';
                document.getElementById("sound").pause();
            }
        }, 1000);
    </script>
</body>
</html>
