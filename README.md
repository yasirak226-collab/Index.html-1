<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vivi x Gloo</title>

<style>
body{
margin:0;
padding:0;
height:100vh;
display:flex;
justify-content:center;
align-items:center;
background:#5a189a;
font-family:Arial, sans-serif;
color:white;
text-align:center;
overflow:hidden;
}

.container{
z-index:2;
}

h1{
font-size:24px;
margin-bottom:30px;
}

button{
padding:12px 25px;
font-size:16px;
border:none;
border-radius:25px;
cursor:pointer;
margin:10px;
}

#yesBtn{
background:gold;
}

#noBtn{
background:gray;
position:relative;
}

/* Medal popup */
.medal{
position:absolute;
top:50%;
left:50%;
transform:translate(-50%,-50%);
font-size:30px;
color:yellow;
font-weight:bold;
}

/* Floating hearts */
.heart{
position:absolute;
font-size:20px;
animation:float 4s linear forwards;
}

@keyframes float{
0%{transform:translateY(0);opacity:1;}
100%{transform:translateY(-300px);opacity:0;}
}

.footer{
position:absolute;
bottom:10px;
width:100%;
font-size:14px;
opacity:0.7;
}
</style>
</head>

<body>

<div class="container">
<h1 id="text">Vivi… can I be your Gloo forever? 💜</h1>

<button id="yesBtn">YES 🏆</button>
<button id="noBtn">NO 😢</button>
</div>

<div class="footer">Made by your Gloo 💜</div>

<script>
var noBtn = document.getElementById("noBtn");
var yesBtn = document.getElementById("yesBtn");
var text = document.getElementById("text");

var messages = [
"Vivi don’t split from me 🥺",
"Gloo sticks forever 😭",
"You can’t escape the slime 💜",
"We are permanently attached 😏",
"Are we not Gloo? 🥹"
];

var index = 0;
var scale = 1;

noBtn.onclick = function(){
noBtn.style.position = "absolute";
noBtn.style.left = Math.random() * (window.innerWidth - 100) + "px";
noBtn.style.top = Math.random() * (window.innerHeight - 50) + "px";

if(index < messages.length){
text.innerHTML = messages[index];
index++;
}

scale += 0.2;
yesBtn.style.transform = "scale(" + scale + ")";
};

yesBtn.onclick = function(){

text.innerHTML = "Vivi 💜 You’re officially stuck with your Gloo forever!";

noBtn.style.display = "none";
yesBtn.style.display = "none";

showMedal("SAVAGE");
setTimeout(function(){ showMedal("LEGENDARY"); }, 1500);
setTimeout(function(){ showMedal("MVP"); }, 3000);

burstHearts();
};

function showMedal(word){
var medal = document.createElement("div");
medal.className = "medal";
medal.innerHTML = word;
document.body.appendChild(medal);

setTimeout(function(){
document.body.removeChild(medal);
},1000);
}

function burstHearts(){
for(var i=0;i<40;i++){
var heart = document.createElement("div");
heart.className = "heart";
heart.innerHTML = Math.random() > 0.5 ? "💜" : "🌸";
heart.style.left = Math.random() * window.innerWidth + "px";
heart.style.top = window.innerHeight + "px";
document.body.appendChild(heart);

setTimeout(function(h){
return function(){
document.body.removeChild(h);
}
}(heart),4000);
}
}
</script>

</body>
</html>
