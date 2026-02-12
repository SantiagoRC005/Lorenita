<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Para Lorenita 💖</title>

<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">

<style>

body{
    margin:0;
    height:100vh;
    background:#f5efe6;
    display:flex;
    justify-content:center;
    align-items:center;
    font-family:'Press Start 2P', cursive;
    overflow:hidden;
}

/* Corazones cayendo tipo nieve */
.falling-heart{
    position:absolute;
    top:-40px;
    width:24px;
    opacity:0.8;
    animation:fall linear infinite;
}

@keyframes fall{
    0%{ transform:translateY(0); }
    100%{ transform:translateY(110vh); }
}

/* Carta inicial */
.start-letter{
    width:280px;
    cursor:pointer;
    transition:0.5s;
    z-index:5;
}

.start-letter.hide{
    transform:scale(0);
    opacity:0;
}

/* Ventana pixel */
.pixel-window{
    position:absolute;
    width:340px;
    background:#ffd6dc;
    border:8px solid #ff9aa8;
    box-shadow:0 0 0 4px #ffb7c5 inset;
    padding:20px;
    text-align:center;
    transform:scale(0);
    opacity:0;
    transition:0.4s;
}

.pixel-window.show{
    transform:scale(1);
    opacity:1;
}

/* Barra superior LOVE */
.window-top{
    background:#ff9aa8;
    color:white;
    padding:6px;
    margin:-20px -20px 15px -20px;
    font-size:10px;
}

/* Gatito */
.cat{
    width:120px;
    margin:15px 0;
}

/* Botones */
.buttons{
    display:flex;
    justify-content:center;
    gap:20px;
    margin-top:10px;
}

button{
    font-family:'Press Start 2P';
    font-size:10px;
    border:none;
    padding:10px 14px;
    cursor:pointer;
}

.yes{
    background:#ff8fa3;
    color:white;
}

.no{
    background:#eee;
    position:relative;
}

</style>
</head>

<body>

<!-- Carta inicial -->
<img src="carta.png" id="startLetter" class="start-letter">

<!-- Ventana mensaje -->
<div class="pixel-window" id="window">

    <div class="window-top">LOVE.exe</div>

    <p>Lorenita 💖</p>
    <p>¿Quieres ser mi San Valentín?</p>

    <img src="gatito.png" class="cat">

    <div class="buttons">
        <button class="yes" onclick="sayYes()">YES</button>
        <button class="no" id="noBtn">NO</button>
    </div>

</div>

<script>

/* Corazones nieve */
function createHeart(){
    const heart=document.createElement("img");
    heart.src="corazones.png";
    heart.classList.add("falling-heart");

    heart.style.left=Math.random()*100+"vw";
    heart.style.animationDuration=(Math.random()*6+6)+"s";

    document.body.appendChild(heart);

    setTimeout(()=>heart.remove(),12000);
}
setInterval(createHeart,900);

/* Carta -> ventana */
const startLetter=document.getElementById("startLetter");
const windowBox=document.getElementById("window");

startLetter.onclick=()=>{
    startLetter.classList.add("hide");
    setTimeout(()=>{
        windowBox.classList.add("show");
    },400);
}

/* Botón NO huye */
const noBtn=document.getElementById("noBtn");

noBtn.addEventListener("mouseover",()=>{
    const x=Math.random()*200-100;
    const y=Math.random()*150-75;
    noBtn.style.transform=`translate(${x}px, ${y}px)`;
});

/* Botón YES */
function sayYes(){
    alert("Nos vemos el sábado :3 💖");
}

</script>

</body>
</html>
