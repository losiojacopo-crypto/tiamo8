<!doctype html>
<html lang="it">
<head>
  <meta charset="utf-8">
  <title>Romantic Page</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      font-family: 'Playfair Display', serif;

      /* Sfondo dinamico */
      background: linear-gradient(135deg,
        #ff9a9e,
        #fad0c4,
        #a1c4fd,
        #c2e9fb,
        #ffdde1,
        #ee9ca7
      );
      background-size: 600% 600%;
      animation: changeBg 30s ease infinite;

      color: #ffffff;
    }

    @keyframes changeBg {
      0%   { background-position: 0% 50%; }
      20%  { background-position: 50% 100%; }
      40%  { background-position: 100% 50%; }
      60%  { background-position: 50% 0%; }
      80%  { background-position: 0% 50%; }
      100% { background-position: 0% 50%; }
    }

    h1 {
      font-size: 80px;
      margin: 0;
      line-height: 1.1;
      letter-spacing: 2px;
      font-weight: 700;
      text-shadow: 0 4px 18px rgba(0,0,0,0.4);
    }

    .script {
      font-family: 'Great Vibes', cursive;
      font-size: 110px;
      margin-top: -10px;
      text-shadow: 0 4px 18px rgba(0,0,0,0.4);
    }

    /* Animazione per singola lettera */
    .letter {
      opacity: 0;
      display: inline-block;
      transform: translateY(20px);
      animation: fadeUp 0.6s forwards;
    }

    @keyframes fadeUp {
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
  </style>
</head>
<body>
  <div>
    <h1 id="line1"></h1>
    <h1 id="line2"></h1>
    <div class="script" id="line3"></div>
  </div>

  <script>
    const line1 = "VISNE";
    const line2 = "MECUM";
    const line3 = "CONVENIRE?";

    const line1Elem = document.getElementById("line1");
    const line2Elem = document.getElementById("line2");
    const line3Elem = document.getElementById("line3");

    function typeWriterSmooth(text, element, delay = 150, callback = null) {
      let i = 0;
      function typing() {
        if (i < text.length) {
          const span = document.createElement('span');
          span.className = 'letter';
          span.style.animationDelay = (i * 0.1) + 's';
          span.textContent = text[i];
          element.appendChild(span);
          i++;
          setTimeout(typing, delay);
        } else if (callback) {
          callback();
        }
      }
      typing();
    }

    // Sequenza delle tre frasi
    typeWriterSmooth(line1, line1Elem, 150, () => {
      typeWriterSmooth(line2, line2Elem, 150, () => {
        typeWriterSmooth(line3, line3Elem, 150);
      });
    });
  </script>
</body>
</html>
