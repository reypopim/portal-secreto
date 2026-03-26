<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Nuestro Portal Secreto</title>

<style>

body{
margin:0;
font-family:Georgia, serif;
background:#5b0f2f;
color:#f5e6d3;
overflow-x:hidden;
}

/* ---------- corazones cayendo ---------- */

.heart{
position:fixed;
top:-10px;
font-size:14px;
color:#f5e6d3;
animation:fall linear infinite;
opacity:0.5;
}

@keyframes fall{
to{
transform:translateY(110vh);
}
}

/* ---------- pagina 1 ---------- */

#page1{
display:flex;
flex-direction:column;
align-items:center;
justify-content:center;
height:100vh;
text-align:center;
}

h1{
font-size:40px;
animation:fade 2s;
}

h2{
font-size:18px;
margin-bottom:40px;
animation:fade 3s;
}

@keyframes fade{
from{opacity:0; transform:translateY(-10px);}
to{opacity:1;}
}

.code-box{
display:flex;
gap:15px;
}

.code-box input{
width:60px;
height:60px;
font-size:28px;
text-align:center;
background:#f0dfc5;
border:none;
border-radius:8px;
}

#error{
margin-top:20px;
color:#ffcccc;
}

/* ---------- pagina 2 ---------- */

#page2{
display:none;
padding:40px;
min-height:200vh;
}

.topbar{
display:flex;
justify-content:space-between;
align-items:center;
}

.exit{
cursor:pointer;
font-size:18px;
}

.section{
display:flex;
justify-content:space-between;
margin-top:60px;
}

/* contador */

#contador{
font-size:18px;
line-height:30px;
}

/* polaroids */

.photos{
display:flex;
gap:20px;
}

.polaroid{
width:160px;
height:180px;
background:white;
padding:10px 10px 40px 10px; /* borde inferior más grande */
box-shadow:0 8px 15px rgba(0,0,0,0.3);
transform:rotate(-6deg);
position:relative;
transition:0.4s;
display:flex;
align-items:center;
justify-content:center;
overflow:hidden;
}

.polaroid:hover{
transform:scale(1.08) rotate(-2deg);
}

.polaroid:not(.activa):hover::after{
content:"Aún en programación";
position:absolute;
top:0;
left:0;
right:0;
bottom:0;
background:rgba(0,0,0,0.6);
display:flex;
align-items:center;
justify-content:center;
color:white;
}

/* post it */

.postits{
display:flex;
gap:15px;
margin-top:40px;
}

.postit{
width:110px;
height:110px;
background:#f0dfc5;
box-shadow:3px 5px 10px rgba(0,0,0,0.3);
cursor:pointer;
transition:0.3s;
display:flex;
flex-direction:column;
align-items:center;
justify-content:center;
text-align:center;
font-family:"Courier New", monospace;
color:black;
}

.postit-number{
font-size:28px;
font-weight:bold;
}

.postit-day{
font-size:14px;
margin-top:4px;
letter-spacing:1px;
}

/* modal */

.modal{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background:rgba(0,0,0,0.6);
display:none;
align-items:center;
justify-content:center;
}

.modal-content{
background:#f5e6d3;
color:#5b0f2f;
padding:30px;
border-radius:10px;
max-width:400px;
}

/* carta */

.letter{
width:120px;
height:80px;
background:#f0dfc5;
cursor:pointer;
}

.binary{
font-family:monospace;
font-size:18px;
}

.cipher{
font-family:monospace;
margin-top:40px;
}

.polaroid.activa{
position:relative;
}

.polaroid.activa::before{
content:"";
position:absolute;
top:10px;
left:10px;
right:10px;
bottom:40px; /* respeta el borde blanco inferior */
background-image:url("ola.jpg");
background-size:cover;
background-position:center;

opacity:0;
animation:revelado 4s ease forwards;
}

.polaroid.activa::after{
content:"";
display:block;
width:100%;
height:100%;
box-shadow:inset 0 0 80px rgba(0,0,0,0.6);
}

@keyframes revelado{
0%{
opacity:0;
filter:blur(10px) brightness(0.5);
}
50%{
opacity:0.6;
filter:blur(4px) brightness(0.8);
}
100%{
opacity:1;
filter:blur(0px) brightness(1);
}
}

</style>
</head>

<body>

<div id="hearts"></div>

<!-- PAGINA 1 -->

<div id="page1">

<h1>Nuestro portal secreto</h1>
<h2>Un vistazo a lo que siento</h2>

<div class="code-box">
<input maxlength="1">
<input maxlength="1">
<input maxlength="1">
<input maxlength="1">
</div>

<div id="error"></div>

</div>


<!-- PAGINA 2 -->

<div id="page2">

<div class="topbar">
<div class="exit" onclick="salir()">← Salida</div>
<h1>Nuestro portal secreto</h1>
<div></div>
</div>

<p>
Este lugar existe porque nuestras historias se cruzaron,
porque el tiempo decidió detenerse en ciertos momentos,
y porque cada recuerdo contigo merece ser guardado.
BEBEEEE!!!
Queria decirte, que a veces no paro de pensar en lo feliz 
que soy a tu lado, que cada momento contigo lo atesoro
y cada risa la guardo en mi corazón.
</p>

<div class="section">

<div id="contador"></div>

<div>
<p>
Te amo
hoy es un tanto diferente, pues un secreto:
hoy siento que no es mi dia
pero no importa, pues creo que es bueno que atesoremos
los buenos recuerdos, y lo malo dejarlo pasar.
a veces me cuesta dejar pasar lo malo.
pero como un día te dije:
¡El amor contgo siempre va a predominar!
</p>
</div>

<div class="photos">

<div class="polaroid activa"></div>

<div class="polaroid"></div>
<div class="polaroid"></div>

</div>

</div>

<!-- post it -->

<div class="postits">

<div class="postit" onclick="openPost(1)">
<div class="postit-number">1</div>
<div class="postit-day">Día</div>
</div>

<div class="postit" onclick="openPost(2)">
<div class="postit-number">2</div>
<div class="postit-day">Día</div>
</div>

<div class="postit" onclick="openPost(3)">
<div class="postit-number">3</div>
<div class="postit-day">Día</div>
</div>

<div class="postit" onclick="openPost(4)">
<div class="postit-number">4</div>
<div class="postit-day">Día</div>
</div>

<div class="postit" onclick="openPost(5)">
<div class="postit-number">5</div>
<div class="postit-day">Día</div>
</div>

<div class="postit" onclick="openPost(6)">
<div class="postit-number">6</div>
<div class="postit-day">Día</div>
</div>

<div class="postit" onclick="openPost(7)">
<div class="postit-number">7</div>
<div class="postit-day">Día</div>
</div>

</div>

<h2>Un pequeño mensaje</h2>

<div class="cipher">

Quizás hoy esperes un puzzle, o algo que tenga que ver con 00110000 00111000.
bueno dejame decirte que lo de hoy es más sentimental, mas descriptivo.
queda poco para una actualizacion novedosa de esta pagina.
que deseo incluir de hace un tiempo,
pero no deseo hablarte de esas cosas. quiero que una vez más, veas todo el amor
que tengo en ti, que no quiero que haya dia que te sientas desplazada.

No quiero que te sientas de esa manera, asi que hoy quiero recordarte
que eres mi reina hermosa, sin ti, mi reino se desploma
tienes un lugar en micorazon, unico, irremplazable.
nadie en esta tierra nunca va a poder llegar a ese lugar.
Te amo
</div>

<div class="section">

<div class="letter" onclick="openLetter()"></div>

<div></div>

<div class="binary">
- .   .- -- ---   .- -- --- .-. --..--   . ... .--. . .-. ---   --.- ..- .   -. ---   - .   ..-. .- ... - .. -.. .. .   -.. . -.. .. -.-. .- .-.   - .- -. - ---   - .. . -- .--. ---   . -.   .-. . ... --- .-.. ...- . .-.   .--. ..- --.. --.. .-.. . ... .-.-.- 
</div>

</div>

</div>

<!-- MODAL -->

<div class="modal" id="modal" onclick="closeModal(event)">
<div class="modal-content" id="modalContent"></div>
</div>

<script>

/* corazones */

function crearCorazones(){
for(let i=0;i<30;i++){
let heart=document.createElement("div")
heart.className="heart"
heart.innerHTML="❤"
heart.style.left=Math.random()*100+"vw"
heart.style.animationDuration=(5+Math.random()*5)+"s"
document.body.appendChild(heart)
}
}
crearCorazones()


/* codigo */

const inputs=document.querySelectorAll(".code-box input")

inputs.forEach((input,i)=>{
input.addEventListener("input",()=>{
if(i<3) inputs[i+1].focus()

let code=""
inputs.forEach(x=>code+=x.value)

if(code.length==4){
if(code==="0715"){
document.getElementById("page1").style.display="none"
document.getElementById("page2").style.display="block"
}
else{
document.getElementById("error").innerText="Inténtalo otra vez, princesa."
inputs.forEach(x=>x.value="")
inputs[0].focus()
}
}
})
})


function salir(){
document.getElementById("page2").style.display="none"
document.getElementById("page1").style.display="flex"
}


/* contador */

const startDate=new Date("2025-08-18")

function updateCounter(){
const now=new Date()
const diff=now-startDate

const days=Math.floor(diff/86400000)
const hours=Math.floor(diff%86400000/3600000)
const minutes=Math.floor(diff%3600000/60000)
const seconds=Math.floor(diff%60000/1000)

document.getElementById("contador").innerHTML=
days+" días<br>"+
hours+" horas<br>"+
minutes+" minutos<br>"+
seconds+" segundos"
}

setInterval(updateCounter,1000)


/* post it */

const textos=[
"???",
"bebe?",
"este dia ya te hice sentir amada bebe, pasa al siguiente",
"MI AMOOOOOOOOOOOOOORRRRRR TE AMO TE AMO TE AMOOOOOOOOO, y si, creo que te debo 2 castigos y muchos ataques de besos, vas a tener que pedirmelos, TE AMO BEBE!!",
"...",
"como le gusta indagar, por hoy no te voy a castigar, la proxima actualizacion será mas.... "
]

function openPost(i){
document.getElementById("modal").style.display="flex"
document.getElementById("modalContent").innerText=textos[i-1]
}

/* carta */

function openLetter(){
document.getElementById("modal").style.display="flex"
document.getElementById("modalContent").innerHTML=
`Querida mía,<br><br>
el post-it del dia 7 te dejo a mitad?, un secretito por aqui, no voy a dejar el trabajo incompleto.
seguramente la proxima actualizacion sea un tanto mas personal.
más de nosotros.
<br><br>
— El Rey`
}

/* cerrar modal */

function closeModal(e){
if(e.target.id==="modal"){
document.getElementById("modal").style.display="none"
}

}

</script>

</body>
</html>
