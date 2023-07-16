# quizzv5
amélioration de mon quizz


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quizz</title>
</head>
<body>
  <div id="menu-container">
    <button class="menu-btn" onclick="startQuiz('general')">Général</button>
    <button class="menu-btn" onclick="startQuiz('histoire')">Histoire</button>
    <button class="menu-btn" onclick="startQuiz('culture')">Culture</button>
    <button class="menu-btn" onclick="startQuiz('sport')">Sport</button>
    <button class="menu-btn" onclick="startQuiz('foot')">Foot</button>
    <button class="menu-btn" onclick="startQuiz('anime')">Anime</button>
    <button class="menu-btn" onclick="startQuiz('animaux')">Animaux</button>
</div>

<h1>Quiz</h1>

<div id="quiz-container">
    <h2 id="question"></h2>
    <div id="options"></div>
    <button id="submit-btn">Suivant</button>
</div>

<div id="result-container">
    <h2 id="result"></h2>
    <p id="correct-answer"></p>
</div>

<div id="scores-container">
    <h2>Vos scores :</h2>
    <ul id="scores"></ul>
    <button id="restart-btn" onclick="restartQuiz()">Recommencer</button>
    <button id="reset-scores-btn" onclick="resetScores()">Réinitialiser les scores</button>
</div>
<script>
 const quizData = {
  general: [
    {
      question: "Quelle est la capitale de la France ?",
      options: ["Paris", "Londres", "Rome", "Madrid"],
      answer: "Paris",
    },
    {
      question: "Quelle est la plus grande planète du système solaire ?",
      options: ["Jupiter", "Mars", "Saturne", "Terre"],
      answer: "Jupiter",
    },
    {
      question: "Quelle est la monnaie du Japon ?",
      options: ["Le yen", "L'euro", "Le dollar américain", "La livre sterling"],
      answer: "Le yen",
    },
    {
      question: "Quelle est la plus grande île du monde ?",
      options: ["Le Groenland", "Madagascar", "Bornéo", "La Nouvelle-Guinée"],
      answer: "Le Groenland",
    },
    {
      question: "Qui a découvert l'Amérique ?",
      options: ["Christophe Colomb", "Vasco de Gama", "Ferdinand Magellan", "James Cook"],
      answer: "Christophe Colomb",
    },
    {
      question: "Quel est le plus grand désert du monde ?",
      options: ["Le Sahara", "Le Gobi", "Le Kalahari", "L'Antarctique"],
      answer: "L'Antarctique",
    },
    {
      question: "Quel est le plus grand animal terrestre ?",
      options: ["L'éléphant d'Afrique", "La girafe", "L'hippopotame", "Le rhinocéros blanc"],
      answer: "L'éléphant d'Afrique",
    },
    {
      question: "Quel pays a remporté la Coupe du Monde de football 2018 ?",
      options: ["La France", "Le Brésil", "L'Allemagne", "L'Espagne"],
      answer: "La France",
    },
    {
      question: "Quel est le plus grand océan du monde ?",
      options: ["L'océan Pacifique", "L'océan Atlantique", "L'océan Indien", "L'océan Arctique"],
      answer: "L'océan Pacifique",
    },
    {
      question: "Quel est le plus haut sommet du monde ?",
      options: ["L'Everest", "Le Mont Blanc", "Le Kilimandjaro", "Le Mont McKinley"],
      answer: "L'Everest",
    },
  ],
  histoire: [
    {
      question: "Quelle est la date de la Révolution française ?",
      options: ["1789", "1799", "1804", "1815"],
      answer: "1789",
    },
    {
      question: "Qui a écrit 'Les Misérables' ?",
      options: ["Victor Hugo", "Émile Zola", "Gustave Flaubert", "Honoré de Balzac"],
      answer: "Victor Hugo",
    },
    {
      question: "Quel événement a déclenché la Première Guerre mondiale ?",
      options: [
        "L'assassinat de l'archiduc François-Ferdinand",
        "La révolution russe",
        "Le bombardement de Pearl Harbor",
        "La chute du mur de Berlin",
      ],
      answer: "L'assassinat de l'archiduc François-Ferdinand",
    },
    {
      question: "Quel roi de France a été guillotiné pendant la Révolution ?",
      options: ["Louis XVI", "Louis XIV", "Louis XIII", "Napoléon Bonaparte"],
      answer: "Louis XVI",
    },
    {
      question: "Quel pays a été le premier à atteindre la Lune ?",
      options: ["Les États-Unis", "L'Union soviétique", "La Chine", "Le Royaume-Uni"],
      answer: "Les États-Unis",
    },
    {
      question: "Quel événement a marqué la fin de la Seconde Guerre mondiale en Europe ?",
      options: [
        "La capitulation de l'Allemagne",
        "Le bombardement de Pearl Harbor",
        "La déclaration de guerre",
        "La chute de Berlin",
      ],
      answer: "La capitulation de l'Allemagne",
    },
    {
      question: "Qui a été le premier président des États-Unis ?",
      options: ["George Washington", "Thomas Jefferson", "Abraham Lincoln", "John F. Kennedy"],
      answer: "George Washington",
    },
    {
      question: "Quel pays a colonisé une grande partie de l'Amérique du Sud au XVIe siècle ?",
      options: ["L'Espagne", "La France", "Le Portugal", "L'Angleterre"],
      answer: "L'Espagne",
    },
    {
      question: "Quelle était la capitale de l'Empire romain ?",
      options: ["Rome", "Athènes", "Alexandrie", "Byzance"],
      answer: "Rome",
    },
    {
      question: "Quel événement a marqué le début de la Renaissance ?",
      options: [
        "La chute de l'Empire romain d'Occident",
        "La découverte de l'Amérique",
        "La publication des '95 thèses' de Martin Luther",
        "La construction de la Tour Eiffel",
      ],
      answer: "La chute de l'Empire romain d'Occident",
    },
  ],
  culture: [
    {
      question: "Qui a peint la Joconde ?",
      options: ["Leonardo da Vinci", "Pablo Picasso", "Vincent van Gogh", "Michel-Ange"],
      answer: "Leonardo da Vinci",
    },
    {
      question: "Quel pays a remporté la Coupe du Monde de football 2018 ?",
      options: ["La France", "Le Brésil", "L'Allemagne", "L'Espagne"],
      answer: "La France",
    },
    {
      question: "Quel est le plus grand festival de musique au monde ?",
      options: ["Coachella", "Glastonbury", "Tomorrowland", "Woodstock"],
      answer: "Tomorrowland",
    },
    {
      question: "Quel est l'auteur de la pièce de théâtre 'Roméo et Juliette' ?",
      options: [
        "William Shakespeare",
        "Victor Hugo",
        "Molière",
        "Anton Tchekhov",
      ],
      answer: "William Shakespeare",
    },
    {
      question: "Quel est le tableau le plus célèbre de Salvador Dalí ?",
      options: ["La Persistance de la mémoire", "Les Demoiselles d'Avignon", "La Nuit étoilée", "Les Tournesols"],
      answer: "La Persistance de la mémoire",
    },
    {
      question: "Quel groupe de musique a interprété la chanson 'Bohemian Rhapsody' ?",
      options: ["Queen", "The Beatles", "Led Zeppelin", "Nirvana"],
      answer: "Queen",
    },
    {
      question: "Quelle est la nationalité de l'écrivain Gabriel García Márquez ?",
      options: ["Colombienne", "Mexicaine", "Argentine", "Espagnole"],
      answer: "Colombienne",
    },
    {
      question: "Quel mouvement artistique est connu pour ses toiles de paysages impressionnistes ?",
      options: ["L'impressionnisme", "Le cubisme", "Le surréalisme", "L'expressionnisme"],
      answer: "L'impressionnisme",
    },
    {
      question: "Qui a écrit la pièce de théâtre 'Hamlet' ?",
      options: ["William Shakespeare", "Molière", "Anton Tchekhov", "Victor Hugo"],
      answer: "William Shakespeare",
    },
    {
      question: "Quel est le compositeur de la symphonie 'La Neuvième' ?",
      options: ["Ludwig van Beethoven", "Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Franz Schubert"],
      answer: "Ludwig van Beethoven",
    },
  ],

  anime: [
  {
    question: "Quel est le nom du personnage principal dans 'Naruto' ?",
    options: ["Naruto Uzumaki", "Sasuke Uchiha", "Kakashi Hatake", "Sakura Haruno"],
    answer: "Naruto Uzumaki",
  },
  {
    question: "Quel est le nom du personnage principal dans 'Demon Slayer' ?",
    options: ["Tanjiro Kamado", "Zenitsu Agatsuma", "Nezuko Kamado", "Inosuke Hashibira"],
    answer: "Tanjiro Kamado",
  },
  {
    question: "Quel est le nom du personnage principal dans 'One Piece' ?",
    options: ["Monkey D. Luffy", "Roronoa Zoro", "Nami", "Usopp"],
    answer: "Monkey D. Luffy",
  },
  {
    question: "Quel est le nom du personnage principal dans 'Attack on Titan' ?",
    options: ["Eren Yeager", "Mikasa Ackerman", "Armin Arlert", "Levi Ackerman"],
    answer: "Eren Yeager",
  },
  {
    question: "Quel est le nom du personnage principal dans 'My Hero Academia' ?",
    options: ["Izuku Midoriya", "Katsuki Bakugo", "Shoto Todoroki", "Ochaco Uraraka"],
    answer: "Izuku Midoriya",
  },
  {
    question: "Quel est le nom du personnage principal dans 'Fullmetal Alchemist' ?",
    options: ["Edward Elric", "Alphonse Elric", "Roy Mustang", "Winry Rockbell"],
    answer: "Edward Elric",
  },
  {
    question: "Quel est le nom du personnage principal dans 'Death Note' ?",
    options: ["Light Yagami", "L Lawliet", "Misa Amane", "Ryuk"],
    answer: "Light Yagami",
  },
  {
    question: "Quel est le nom du personnage principal dans 'Dragon Ball Z' ?",
    options: ["Goku", "Vegeta", "Gohan", "Piccolo"],
    answer: "Goku",
  },
  {
    question: "Quel est le nom du personnage principal dans 'Hunter x Hunter' ?",
    options: ["Gon Freecss", "Killua Zoldyck", "Kurapika", "Leorio Paradinight"],
    answer: "Gon Freecss",
  },
  {
    question: "Quel est le nom du personnage principal dans 'One Punch Man' ?",
    options: ["Saitama", "Genos", "Speed-o'-Sound Sonic", "Tatsumaki"],
    answer: "Saitama",
  },
  {
    question: "Dans l'anime 'My Hero Academia', quel est le nom de la ville où se déroule l'histoire ?",
    options: ["Musutafu", "U.A. High", "Kamino Ward", "Hosu City"],
    answer: "Musutafu",
  },
  {
    question: "Dans l'anime 'Attack on Titan', quel est le nom de la formation militaire dont font partie les personnages principaux ?",
    options: ["Scouts de reconnaissance", "Brigade spéciale", "Légion d'élite", "Garde royale"],
    answer: "Scouts de reconnaissance",
  },
  {
    question: "Dans l'anime 'Death Note', quel est le surnom donné au mystérieux détective qui enquête sur Kira ?",
    options: ["L Lawliet", "N", "Near", "Mello"],
    answer: "L Lawliet",
  },
  {
    question: "Dans l'anime 'Fullmetal Alchemist', quel est le nom de l'alchimiste d'État surnommé 'Fullmetal' en raison de ses membres métalliques ?",
    options: ["Edward Elric", "Alphonse Elric", "Roy Mustang", "Alex Louis Armstrong"],
    answer: "Edward Elric",
  },
  {
    question: "Dans l'anime 'One Piece', quel est le fruit du démon que mange le personnage principal Monkey D. Luffy ?",
    options: ["Gomu Gomu no Mi", "Mera Mera no Mi", "Hito Hito no Mi", "Ope Ope no Mi"],
    answer: "Gomu Gomu no Mi",
  },
  {
    question: "Dans l'anime 'Naruto', quel est le nom de la technique secrète utilisée par le personnage principal pour créer des clones de lui-même ?",
    options: ["Kage Bunshin no Jutsu", "Rasengan", "Chidori", "Harem no Jutsu"],
    answer: "Kage Bunshin no Jutsu",
  },
  {
    question: "Dans l'anime 'Demon Slayer', quel est le nom de l'épée utilisée par les chasseurs de démons ?",
    options: ["Nichirin Blade", "Tsuba", "Nezuko Sword", "Sun Breath"],
    answer: "Nichirin Blade",
  }
],
foot: [
    {
      question: "Quelle équipe a remporté la Coupe du Monde de football en 2018 ?",
      options: ["La France", "L'Allemagne", "Le Brésil", "L'Espagne"],
      answer: "La France",
    },
    {
      question: "Qui est le meilleur buteur de tous les temps en Coupe du Monde ?",
      options: ["Marta", "Cristiano Ronaldo", "Lionel Messi", "Miroslav Klose"],
      answer: "Miroslav Klose",
    },
    {
      question: "Combien de joueurs y a-t-il dans une équipe de football sur le terrain ?",
      options: ["9", "10", "11", "12"],
      answer: "11",
    },
    {
      question: "Quelle est la durée d'un match de football ?",
      options: ["60 minutes", "75 minutes", "90 minutes", "105 minutes"],
      answer: "90 minutes",
    },
    {
      question: "Qui a remporté le Ballon d'Or en 2021 ?",
      options: ["Lionel Messi", "Robert Lewandowski", "Cristiano Ronaldo", "Kylian Mbappé"],
      answer: "Lionel Messi",
    },
    {
      question: "Quelle équipe a remporté le plus de Ligue des Champions de l'UEFA ?",
      options: ["Real Madrid", "FC Barcelone", "Bayern Munich", "Liverpool"],
      answer: "Real Madrid",
    },
    {
      question: "Qui est l'entraîneur de l'équipe nationale du Brésil en 2021 ?",
      options: ["Tite", "Jurgen Klopp", "Pep Guardiola", "Zinedine Zidane"],
      answer: "Tite",
    },
    {
      question: "Quelle est la plus grande rivalité de clubs en football espagnol ?",
      options: ["Barcelone vs. Real Madrid", "Atletico Madrid vs. Sevilla", "Real Madrid vs. Valencia", "Barcelone vs. Atletico Madrid"],
      answer: "Barcelone vs. Real Madrid",
    },
    {
      question: "Quel pays a remporté le plus de Coupes d'Afrique des Nations de football ?",
      options: ["Égypte", "Cameroun", "Nigeria", "Ghana"],
      answer: "Égypte",
    },
    {
      question: "Qui a été le meilleur buteur de la Coupe du Monde de football 2014 ?",
      options: ["Thomas Müller", "Lionel Messi", "Neymar", "James Rodriguez"],
      answer: "James Rodriguez",
    },
    {
      question: "Quel joueur a remporté le plus de Ballons d'Or dans l'histoire du football ?",
      options: ["Lionel Messi", "Cristiano Ronaldo", "Pelé", "Diego Maradona"],
      answer: "Lionel Messi",
    },
    {
      question: "Quel club a remporté le plus de titres de la Premier League anglaise ?",
      options: ["Manchester United", "Liverpool", "Chelsea", "Arsenal"],
      answer: "Manchester United",
    },
    {
      question: "Quel pays a remporté la Coupe du Monde de football le plus de fois ?",
      options: ["Brésil", "Allemagne", "Italie", "Argentine"],
      answer: "Brésil",
    },
    {
      question: "Qui a remporté la Ligue des Champions de l'UEFA en 2021 ?",
      options: ["Chelsea", "Manchester City", "Bayern Munich", "Paris Saint-Germain"],
      answer: "Chelsea",
    },
    {
      question: "Quelle est la nationalité de l'entraîneur de l'équipe nationale d'Angleterre en 2021 ?",
      options: ["Anglaise", "Allemande", "Espagnole", "Italienne"],
      answer: "Allemande",
    },
  ],

animaux: [
    {
      question: "Quel est le plus grand animal terrestre ?",
      options: ["L'éléphant d'Afrique", "La girafe", "L'hippopotame", "Le rhinocéros blanc"],
      answer: "L'éléphant d'Afrique",
    },
    {
      question: "Quel est l'oiseau national des États-Unis ?",
      options: ["L'aigle chauve", "Le faucon pèlerin", "Le dindon sauvage", "Le moqueur chat"],
      answer: "L'aigle chauve",
    },
    // Ajoutez d'autres questions sur les animaux ici
    {
      question: "Quel est le plus grand poisson du monde ?",
      options: ["Le requin baleine", "Le grand requin blanc", "Le mérou géant", "Le marlin bleu"],
      answer: "Le requin baleine",
    },
    {
      question: "Quel est le plus grand félin du monde ?",
      options: ["Le tigre de Sibérie", "Le lion", "Le guépard", "Le léopard"],
      answer: "Le tigre de Sibérie",
    },
    {
      question: "Combien de bras possède une pieuvre ?",
      options: ["6", "8", "10", "12"],
      answer: "8",
    },
    {
      question: "Quel est l'oiseau qui ne vole pas mais qui nage très bien ?",
      options: ["Le manchot empereur", "Le colibri", "Le moineau", "Le corbeau"],
      answer: "Le manchot empereur",
    },
    {
      question: "Quel est le plus grand reptile vivant sur terre ?",
      options: ["Le crocodile du Nil", "Le lézard géant de Komodo", "La tortue géante des Galapagos", "Le caïman"],
      answer: "Le lézard géant de Komodo",
    },
    {
      question: "Quel est le plus grand oiseau du monde ?",
      options: ["L'autruche", "Le condor des Andes", "Le casoar à casque", "Le cygne trompette"],
      answer: "L'autruche",
    },
    {
      question: "Quel est l'animal le plus rapide sur terre ?",
      options: ["Le guépard", "L'antilope saïga", "Le lièvre", "Le kangourou"],
      answer: "Le guépard",
    },
    {
      question: "Quel est le plus grand serpent venimeux du monde ?",
      options: ["Le cobra royal", "La vipère de Russell", "Le mamba noir", "La morsure d'amour"],
      answer: "Le cobra royal",
    },
    {
      question: "Quel est l'oiseau le plus grand et le plus lourd capable de voler ?",
      options: ["L'albatros", "Le pélican", "La cigogne", "Le flamant"],
      answer: "L'albatros",
    },
    {
      question: "Quel est le plus grand mammifère marin ?",
      options: ["La baleine bleue", "L'orque", "Le dauphin", "Le cachalot"],
      answer: "La baleine bleue",
    },
    {
      question: "Quel est l'animal le plus venimeux du monde ?",
      options: ["La méduse-boîte", "Le scorpion empereur", "La mygale", "Le serpent taïpan"],
      answer: "La méduse-boîte",
    },
    {
      question: "Quel est le plus grand insecte du monde ?",
      options: ["Le coléoptère titan", "Le papillon morpho", "La mante religieuse", "Le scarabée rhinocéros"],
      answer: "Le coléoptère titan",
    },
    {
      question: "Quel est le plus grand animal marin ?",
      options: ["La baleine bleue", "Le calmar géant", "Le requin pèlerin", "Le cachalot"],
      answer: "La baleine bleue",
    },
    {
      question: "Quel est le plus grand prédateur terrestre ?",
      options: ["L'ours blanc", "Le tigre de Sibérie", "Le lion", "Le loup gris"],
      answer: "L'ours blanc",
    },
  ],

  sport: [
    {
      question: "Quel joueur a remporté le Ballon d'Or en 2020 ?",
      options: ["Lionel Messi", "Cristiano Ronaldo", "Robert Lewandowski", "Neymar"],
      answer: "Robert Lewandowski",
    },
    {
      question: "Quelle équipe a remporté la Ligue des Champions en 2021 ?",
      options: ["Chelsea", "Manchester City", "Real Madrid", "Paris Saint-Germain"],
      answer: "Chelsea",
    },
    {
      question: "Quel pays a remporté la Coupe du Monde de rugby 2019 ?",
      options: ["L'Afrique du Sud", "La Nouvelle-Zélande", "L'Angleterre", "L'Australie"],
      answer: "L'Afrique du Sud",
    },
    {
      question: "Quel est le record du monde du saut en hauteur masculin ?",
      options: ["2,45 m", "2,43 m", "2,42 m", "2,40 m"],
      answer: "2,45 m",
    },
    {
      question: "Quelle joueuse de tennis a remporté le plus de titres du Grand Chelem en simple ?",
      options: ["Margaret Court", "Serena Williams", "Steffi Graf", "Martina Navratilova"],
      answer: "Margaret Court",
    },
    {
      question: "Quel est le club de football le plus titré en Angleterre ?",
      options: ["Manchester United", "Liverpool", "Arsenal", "Chelsea"],
      answer: "Manchester United",
    },
    {
      question: "Quel est le pays d'origine du pilote de Formule 1 Lewis Hamilton ?",
      options: ["Le Royaume-Uni", "L'Allemagne", "La France", "Le Brésil"],
      answer: "Le Royaume-Uni",
    },
    {
      question: "Quel est le pays d'origine du judoka Teddy Riner ?",
      options: ["La France", "Le Japon", "Les États-Unis", "Le Brésil"],
      answer: "La France",
    },
    {
      question: "Quel est le record du monde du marathon masculin ?",
      options: ["2:01:39", "2:02:57", "2:03:23", "2:04:32"],
      answer: "2:01:39",
    },
    {
      question: "Quel pays a remporté le plus de médailles d'or aux Jeux olympiques d'été de 2021 ?",
      options: ["Les États-Unis", "La Chine", "Le Japon", "L'Australie"],
      answer: "Les États-Unis",
    },
  ],
};

const questionElement = document.getElementById("question");
const optionsElement = document.getElementById("options");
const submitButton = document.getElementById("submit-btn");
const restartButton = document.getElementById("restart-btn");
const resultContainer = document.getElementById("result-container");
const resultElement = document.getElementById("result");
const correctAnswerElement = document.getElementById("correct-answer");
const scoresContainer = document.getElementById("scores-container");
const scoresElement = document.getElementById("scores");

const numberOfQuestions = 8; // Nombre de questions à poser
let currentTheme = "";
let currentQuestion = 0;
let score = 0;
let scores = [];
let correctAnswers = [];
let shuffledQuestions = [];

function shuffleQuestions() {
  shuffledQuestions = quizData[currentTheme].sort(() => Math.random() - 0.5);
}

function loadQuestion() {
  const currentQuizData = shuffledQuestions[currentQuestion];
  questionElement.innerText = currentQuizData.question;

  while (optionsElement.firstChild) {
    optionsElement.removeChild(optionsElement.firstChild);
  }

  currentQuizData.options.forEach((option) => {
    const button = document.createElement("button");
    button.innerText = option;
    optionsElement.appendChild(button);
    button.addEventListener("click", selectOption);
  });
}

function selectOption(e) {
  const selectedButton = e.target;
  const answer = shuffledQuestions[currentQuestion].answer;

  if (selectedButton.innerText === answer) {
    score++;
  } else {
    correctAnswers.push({
      question: shuffledQuestions[currentQuestion].question,
      correctAnswer: answer,
    });
  }

  currentQuestion++;

  if (currentQuestion < numberOfQuestions) {
    loadQuestion();
  } else {
    showResult();
  }
}

function showResult() {
  questionElement.style.display = "none";
  optionsElement.style.display = "none";
  submitButton.style.display = "none";

  resultElement.innerText = `Votre score : ${score}/${numberOfQuestions}`;
  resultContainer.style.display = "block";

  scores.push(score);
  saveScores();
  showScores();
  showCorrectAnswers();
}

function showCorrectAnswers() {
  correctAnswerElement.innerText = "Réponses incorrectes :\n\n";
  correctAnswers.forEach((item) => {
    correctAnswerElement.innerText += `Question : ${item.question}\nRéponse correcte : ${item.correctAnswer}\n\n`;
  });
}

function showScores() {
  scoresElement.innerHTML = "";

  for (let i = 0; i < scores.length; i++) {
    const scoreItem = document.createElement("li");
    scoreItem.innerText = `Score ${i + 1}: ${scores[i]}/${numberOfQuestions}`;
    scoresElement.appendChild(scoreItem);
  }

  scoresContainer.style.display = "block";
}

function saveScores() {
  localStorage.setItem("quizScores", JSON.stringify(scores));
}

function loadScores() {
  const savedScores = localStorage.getItem("quizScores");

  if (savedScores) {
    scores = JSON.parse(savedScores);
    showScores();
  }
}

function startQuiz(theme) {
  currentTheme = theme;
  currentQuestion = 0;
  score = 0;
  correctAnswers = [];
  shuffledQuestions = [];

  resultContainer.style.display = "none";
  scoresContainer.style.display = "none";

  shuffleQuestions();
  loadQuestion();
}

function restartQuiz() {
  currentQuestion = 0;
  score = 0;
  correctAnswers = [];
  shuffledQuestions = [];

  resultContainer.style.display = "none";
  scoresContainer.style.display = "none";

  shuffleQuestions();
  loadQuestion();
}

function resetScores() {
  scores = [];
  localStorage.removeItem("quizScores");
  scoresContainer.style.display = "none";
}

shuffleQuestions();
loadScores();
</script>

</body>
</html>

<style>
  body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 20px;
    background-color: #f9f9f9;
}

nav {
    background-color: #292f3f;
    padding: 10px;
}

nav ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
}

nav li {
    margin: 0 10px;
}

nav a {
    color: #fff;
    text-decoration: none;
    font-size: 18px;
}

nav a:hover {
    color: #007bff;
}

h1 {
    color: #414141;
    text-align: center;
    margin-bottom: 30px;
}

#quiz-container {
    max-width: 500px;
    margin: 0 auto;
    background-color: #fff;
    border-radius: 15px;
    padding: 20px;
    box-shadow: 0px 0px 15px 5px rgba(0,0,0,0.06);
}

h2 {
    color: #414141;
}

#options {
    display: flex;
    flex-direction: column;
    margin-top: 20px;
}

button {
    margin: 10px 0;
    background-color: #007BFF;
    color: #fff;
    border: none;
    padding: 15px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    border-radius: 5px;
    cursor: pointer;
    box-shadow: 0px 10px 20px -10px rgba(0,123,255,0.25);
    transition: all 0.3s ease;
}

button:hover {
    background-color: #0056b3;
    box-shadow: 0px 15px 20px -10px rgba(0,56,179,0.25);
    transform: translateY(-3px);
}

button:active {
    transform: translateY(-1px);
    box-shadow: 0px 5px 10px -5px rgba(0,56,179,0.25);
}

#result-container, #scores-container {
    margin-top: 40px;
    text-align: center;
    background-color: #fff;
    border-radius: 15px;
    padding: 20px;
    box-shadow: 0px 0px 15px 5px rgba(0,0,0,0.06);
}

ul {
    list-style: none;
    padding: 0;
}

li {
    margin: 10px 0;
}

#correct-answer {
    margin-top: 20px;
    background-color: #f9f9f9;
    border-radius: 5px;
    padding: 10px;
}

#correct-answer p {
    margin: 10px 0;
}

#correct-answer p:first-child {
    font-weight: bold;
}

#correct-answer p:not(:first-child) {
    margin-left: 20px;
}

#menu-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            margin-bottom: 20px;
        }

        .menu-btn {
            margin: 5px;
            padding: 10px 15px;
            font-size: 16px;
            border-radius: 5px;
            border: none;
            background-color: #007BFF;
            color: #fff;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        .menu-btn:hover {
            background-color: #0056b3;
        }

        @media only screen and (max-width: 600px) {
            .menu-btn {
                width: 100%;
                margin-bottom: 5px;
            }
        }
    </style>


