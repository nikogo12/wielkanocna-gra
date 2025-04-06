<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8">
  <title>Wielkanocna Zgaduj-Zgadula</title>
  <style>
    body {
      font-family: 'Comic Sans MS', cursive, sans-serif;
      background: url('https://i.imgur.com/hDCZk7m.jpeg') no-repeat center center fixed;
      background-size: cover;
      text-align: center;
      color: #4B0082;
    }
    .container {
      background-color: rgba(255, 255, 255, 0.9);
      margin: 50px auto;
      padding: 20px;
      border-radius: 20px;
      width: 90%;
      max-width: 600px;
      box-shadow: 0 0 15px rgba(0,0,0,0.3);
    }
    .puzzle {
      font-size: 2em;
      letter-spacing: 10px;
      margin: 20px;
    }
    button.answer-btn {
      padding: 10px 20px;
      font-size: 1em;
      margin: 10px;
      cursor: pointer;
      border-radius: 10px;
      border: none;
      background-color: #FFD700;
      display: block;
      width: 80%;
      margin-left: auto;
      margin-right: auto;
    }
    #question {
      font-size: 1.2em;
      margin-bottom: 10px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Wielkanocna Zgaduj-Zgadula</h1>
    <div class="puzzle" id="puzzle">_ _ _ _ _ _ _ _ _</div>
    <div id="question">Kliknij przycisk, aby rozwiązać zagadkę!</div>
    <div id="answers"></div>
  </div>

  <script>
    const riddles = [
      {
        q: "Kolorowa, w święta malowana — co to?",
        options: ["A: Pisanka", "B: Marchewka", "C: Bazie"],
        correct: "a",
        l: 0
      },
      {
        q: "Ma długie uszy, marchewki szuka, skacze po łące — kto to taki?",
        options: ["A: Baranek", "B: Królik", "C: Pisklak"],
        correct: "b",
        l: 1
      },
      {
        q: "Z koszykiem w ręku dzieci odwiedza i prezenty zostawia — kto to?",
        options: ["A: Zajączek", "B: Kurczak", "C: Bocian"],
        correct: "a",
        l: 2
      },
      {
        q: "W Niedzielę Palmową ją niesiemy — co to?",
        options: ["A: Palma", "B: Szyszka", "C: Gałązka"],
        correct: "a",
        l: 3
      },
      {
        q: "Słodki wypiek z lukrem na wierzchu — co to?",
        options: ["A: Babka", "B: Chleb", "C: Bułka"],
        correct: "a",
        l: 4
      },
      {
        q: "W Lany Poniedziałek wodą cię obleje — co to?",
        options: ["A: Deszcz", "B: Śmigus", "C: Wiadro"],
        correct: "b",
        l: 5
      },
      {
        q: "Biała tkanina na stole — co to?",
        options: ["A: Serwetka", "B: Obrus", "C: Koc"],
        correct: "b",
        l: 6
      },
      {
        q: "Do niego wkładamy pokarmy do święcenia — co to?",
        options: ["A: Koszyk", "B: Torba", "C: Pudełko"],
        correct: "a",
        l: 7
      },
      {
        q: "Małe, żółte i piszczy — co to?",
        options: ["A: Kurczątko", "B: Kaczka", "C: Gąska"],
        correct: "a",
        l: 8
      }
    ];

    let currentRiddle = 0;
    let puzzle = ['_', '_', '_', '_', '_', '_', '_', '_', '_'];
    const fullWord = "WIELKANOC";

    function displayRiddle() {
      const riddle = riddles[currentRiddle];
      document.getElementById('question').innerText = riddle.q;

      const answersDiv = document.getElementById('answers');
      answersDiv.innerHTML = '';

      riddle.options.forEach(option => {
        const btn = document.createElement('button');
        btn.innerText = option;
        btn.className = 'answer-btn';
        btn.onclick = () => checkAnswer(option[0].toLowerCase());
        answersDiv.appendChild(btn);
      });

      document.getElementById('puzzle').innerText = puzzle.join(' ');
    }

    function checkAnswer(selected) {
      if (selected === riddles[currentRiddle].correct) {
        puzzle[riddles[currentRiddle].l] = fullWord[riddles[currentRiddle].l];
        document.getElementById('puzzle').innerText = puzzle.join(' ');
        currentRiddle++;
        if (currentRiddle < riddles.length) {
          setTimeout(displayRiddle, 500);
        } else {
          document.getElementById('question').innerText = "Brawo! Odkryłeś całe hasło!";
          document.getElementById('answers').innerHTML = "";
        }
      } else {
        alert("Ups! To nie ta odpowiedź.");
      }
    }

    // Start
    displayRiddle();
  </script>
</body>
</html>
