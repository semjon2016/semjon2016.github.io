<!DOCTYPE html>
<html lang="uk">
<head>
<meta charset="UTF-8">
<title>Залік з історії України</title>

<style>

body{
font-family:Arial;
background:#f2f2f2;
margin:0;
padding:20px;
text-align:center;
}

h1{
margin-bottom:10px;
}

.controls{
margin-bottom:20px;
}

button{
padding:10px 15px;
margin:5px;
border:none;
border-radius:6px;
background:#007BFF;
color:white;
cursor:pointer;
}

button:hover{
background:#0056b3;
}

.container{
display:grid;
grid-template-columns:repeat(auto-fill,minmax(250px,1fr));
gap:20px;
}

/* FLIP CARD */

.flip-card{
background:transparent;
width:100%;
height:200px;
perspective:1000px;
cursor:pointer;
}

.flip-inner{
position:relative;
width:100%;
height:100%;
text-align:center;
transition:transform 0.6s;
transform-style:preserve-3d;
}

.flip-card.flipped .flip-inner{
transform:rotateY(180deg);
}

.flip-front, .flip-back{
position:absolute;
width:100%;
height:100%;
backface-visibility:hidden;
background:white;
border-radius:10px;
box-shadow:0 0 10px rgba(0,0,0,0.1);
display:flex;
align-items:center;
justify-content:center;
padding:15px;
}

.flip-back{
transform:rotateY(180deg);
background:#eef;
}

/* TEST MODE */

#testMode{
display:none;
}

#question{
font-size:22px;
margin:30px;
}

#answer{
display:none;
margin:20px;
font-size:18px;
background:#eef;
padding:15px;
border-radius:10px;
}

</style>
</head>

<body>

<h1>Залік з історії України</h1>

<div class="controls">

<button onclick="showCards()">👀 Картки</button>
<button onclick="showTest()">🤑 Тест</button>
<button onclick="shuffle()">🤪 Перемішати</button>

</div>

<div id="cardsMode">
<div class="container" id="cards"></div>
</div>

<div id="testMode">

<div id="question"></div>

<button onclick="showAnswer()">Показати відповідь</button>

<div id="answer"></div>

<br>

<button onclick="nextQuestion()">Наступне питання</button>

</div>

<script>

let cardsData=[

["Коли почалася Перша світова війна?","28 липня 1914 р."],
["Що таке ГУР?","Головна Українська Рада."],
["Що таке СВУ?","Союз визволення України."],
["Коли утворилась УЦР?","Березень 1917."],
["І Універсал","10 червня 1917."],
["ІІ Універсал","3 липня 1917."],
["ІІІ Універсал","7 листопада 1917."],
["IV Універсал","22 січня 1918."],
["Брестський мир","9 лютого 1918."],
["Гетьманат","Українська Держава Скоропадського."],
["Директорія","Орган влади УНР 1918."],
["Листопадовий зрив","1 листопада 1918."],
["ЗУНР","1 листопада 1918."],
["Чортківська офензива","Наступ УГА 1919."],
["Отаманщина","Влада місцевих отаманів."],
["Воєнний комунізм","Політика більшовиків 1918–1921."],
["Продрозкладка","Примусове вилучення хліба."],
["Червоний терор","Репресії більшовиків."],
["Ризький мир","18 березня 1921."],
["НЕП","1921–1928."],
["Українізація","1923–1933."],
["Індустріалізація","З 1925."],
["Перша п'ятирічка","1928–1932."],
["Друга п'ятирічка","1933–1937."],
["Колективізація","1929–1933."],
["Голодомор","1932–1933."],
["Лікнеп","Ліквідація неписьменності."],
["Конституція УРСР","1937."],
["Шахтинська справа","1928."],
["Справа СВУ","1930."]
];

let current=0;

function renderCards(){

const container=document.getElementById("cards");
container.innerHTML="";

cardsData.forEach((card,i)=>{

container.innerHTML+=`

<div class="flip-card" onclick="this.classList.toggle('flipped')">

<div class="flip-inner">

<div class="flip-front">
${card[0]}
</div>

<div class="flip-back">
${card[1]}
</div>

</div>

</div>

`;

});

}

function showCards(){

document.getElementById("cardsMode").style.display="block";
document.getElementById("testMode").style.display="none";

}

function showTest(){

document.getElementById("cardsMode").style.display="none";
document.getElementById("testMode").style.display="block";

loadQuestion();

}

function loadQuestion(){

document.getElementById("question").innerText=cardsData[current][0];
document.getElementById("answer").innerText=cardsData[current][1];
document.getElementById("answer").style.display="none";

}

function showAnswer(){

document.getElementById("answer").style.display="block";

}

function nextQuestion(){

current++;

if(current>=cardsData.length){
current=0;
}

loadQuestion();

}

function shuffle(){

cardsData.sort(()=>Math.random()-0.5);
renderCards();

}

renderCards();

</script>

</body>
</html>
