<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Benimle Barışır Mısın?</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #fdefee;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            text-align: center;
        }
        .container { position: relative; }
        h1 { color: #e91e63; font-size: 2.5em; margin-bottom: 30px; }
        .buttons { display: flex; gap: 20px; justify-content: center; }
        button {
            padding: 15px 30px;
            font-size: 1.2em;
            cursor: pointer;
            border: none;
            border-radius: 10px;
            transition: all 0.3s ease;
            color: white;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
        }
        #evet-btn { background-color: #4CAF50; }
        #hayir-btn { background-color: #f44336; }
        #evet-btn:hover { transform: scale(1.1); }
        #hayir-btn:hover { opacity: 0.8; }
        .mesaj {
            display: none;
            color: #333;
            padding: 30px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.25);
        }
        .mesaj h2 { color: #e91e63; }
        .mesaj p { font-size: 1.2em; line-height: 1.6; }
    </style>
</head>
<body>

    <div class="container" id="secim-container">
        <h1>Benimle Tekrar Barışır Mısın?</h1>
        <div class="buttons">
            <button id="evet-btn">EVET!</button>
            <button id="hayir-btn">Hayır</button>
        </div>
    </div>

    <div class="mesaj" id="barisma-mesaji">
        <h2>Seni Çok Seviyorum!</h2>
        <p>
            Barıştığımız için dünyanın en mutlu insanı benim! <br>
            Yaşattığım her şey için gerçekten çok üzgünüm. <br>
            Biliyorum, kelimeler hatalarımı düzeltmeye yetmez ama telafi etmek için her şeyi yapacağım. <br>
            Tek istediğim sana o güzel gülümsemeni geri verebilmek. Affet beni.
        </p>
    </div>

    <!-- MÜZİK DOSYASINI BURADAN ÇAĞIRIYORUZ. İSİM TAM OLARAK 'muzik.mp3' OLMALI -->
    <audio id="barisma-muzigi" src="muzik.mp3"></audio>

    <script>
        const evetBtn = document.getElementById('evet-btn');
        const hayirBtn = document.getElementById('hayir-btn');
        const secimContainer = document.getElementById('secim-container');
        const barismaMesaji = document.getElementById('barisma-mesaji');
        const barismaMuzigi = document.getElementById('barisma-muzigi');

        let hayirTiklamaSayisi = 0;
        let evetButtonScale = 1;
        const buyumeOrani = 0.25;

        hayirBtn.addEventListener('click', () => {
            hayirTiklamaSayisi++;
            if (hayirTiklamaSayisi <= 5) {
                evetButtonScale += buyumeOrani;
                evetBtn.style.transform = `scale(${evetButtonScale})`;
                evetBtn.style.padding = `${15 + hayirTiklamaSayisi * 4}px ${30 + hayirTiklamaSayisi * 8}px`;
                evetBtn.style.fontSize = `${1.2 + hayirTiklamaSayisi * 0.15}em`;
            }
            if (hayirTiklamaSayisi === 5) {
                hayirBtn.style.display = 'none';
            }
        });

        evetBtn.addEventListener('click', () => {
            secimContainer.style.display = 'none';
            barismaMesaji.style.display = 'block';
            barismaMuzigi.play().catch(error => {
                console.error("Müzik çalınırken hata oluştu:", error);
            });
        });
    </script>

</body>
</html>
