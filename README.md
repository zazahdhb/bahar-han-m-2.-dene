<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Benimle Barışır Mısın Zeynep?</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #fdf0f5; /* Daha soft bir pembe tonu */
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            text-align: center;
            padding: 20px; /* Kenar boşluğu eklendi */
            box-sizing: border-box;
        }
        .container {
            position: relative;
        }
        h1 {
            color: #ff69b4; /* Canlı pembe */
            font-size: 2.2em;
            margin-bottom: 30px;
        }
        .buttons {
            display: flex;
            gap: 20px;
            justify-content: center;
            flex-wrap: wrap; /* Küçük ekranlar için butonların alta geçmesini sağlar */
        }
        button {
            padding: 15px 30px;
            font-size: 1.2em;
            cursor: pointer;
            border: none;
            border-radius: 10px;
            transition: all 0.3s ease;
            color: white;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
            font-weight: bold;
        }
        #evet-btn {
            background-color: #28a745; /* Yeşil */
        }
        #hayir-btn {
            background-color: #dc3545; /* Kırmızı */
        }
        #evet-btn:hover {
            transform: scale(1.1);
        }
        #hayir-btn:hover {
            opacity: 0.8;
        }
        .mesaj {
            display: none;
            color: #333;
            padding: 30px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.25);
            max-width: 500px; /* Mesaj kutusuna maksimum genişlik */
        }
        .mesaj h2 {
            color: #ff69b4;
        }
        .mesaj p {
            font-size: 1.2em;
            line-height: 1.6;
        }

        /* Mobil cihazlar için ek düzenlemeler */
        @media (max-width: 480px) {
            h1 {
                font-size: 1.8em;
            }
            button {
                padding: 12px 25px;
                font-size: 1em;
            }
            .mesaj p {
                font-size: 1em;
            }
        }
    </style>
</head>
<body>

    <div class="container" id="secim-container">
        <h1>Benimle Barışır Mısın Zeynep?</h1>
        <div class="buttons">
            <button id="evet-btn">EVET!</button>
            <button id="hayir-btn">Hayır</button>
        </div>
    </div>

    <div class="mesaj" id="barisma-mesaji">
        <h2>Canım Kuzenim Benim!</h2>
        <p>
            Barıştığın için o kadar mutlu oldum ki anlatamam Zeynep! <br>
            Seni kırdığım için gerçekten çok ama çok özür dilerim. <br>
            Biliyorum bir hataydı ama sensiz hiç tadım tuzum yok. <br>
            Lütfen beni affet ve eskisi gibi yine bol bol gülelim olur mu?
        </p>
    </div>

    <!-- MÜZİK DOSYASINI BURADAN ÇAĞIRIYORUZ. İSİM TAM OLARAK 'muzik.mp3' OLMALI -->
    <audio id="barisma-muzigi" src="muzik.mp3" loop></audio>

    <script>
        const evetBtn = document.getElementById('evet-btn');
        const hayirBtn = document.getElementById('hayir-btn');
        const secimContainer = document.getElementById('secim-container');
        const barismaMesaji = document.getElementById('barisma-mesaji');
        const barismaMuzigi = document.getElementById('barisma-muzigi');

        let hayirTiklamaSayisi = 0;
        let evetButtonScale = 1;
        const buyumeOrani = 0.25;

        // "Hayır" butonuna her tıklandığında "Evet" butonunu büyüten fonksiyon
        hayirBtn.addEventListener('click', () => {
            hayirTiklamaSayisi++;
            if (hayirTiklamaSayisi <= 5) {
                evetButtonScale += buyumeOrani;
                evetBtn.style.transform = `scale(${evetButtonScale})`;
                evetBtn.style.padding = `${15 + hayirTiklamaSayisi * 4}px ${30 + hayirTiklamaSayisi * 8}px`;
                evetBtn.style.fontSize = `${1.2 + hayirTiklamaSayisi * 0.15}em`;
            }
            // 5. tıklamadan sonra "Hayır" butonu kaybolur
            if (hayirTiklamaSayisi === 5) {
                hayirBtn.style.display = 'none';
            }
        });

        // "Evet" butonuna tıklandığında barışma mesajını gösterir ve müziği başlatır
        evetBtn.addEventListener('click', () => {
            secimContainer.style.display = 'none';
            barismaMesaji.style.display = 'block';
            barismaMuzigi.play().catch(error => {
                // Tarayıcılar bazen otomatik müzik çalmayı engelleyebilir.
                // Bu yüzden hatayı konsolda gösteriyoruz.
                console.error("Müzik çalınırken bir hata oluştu:", error);
            });
        });
    </script>

</body>
</html>
