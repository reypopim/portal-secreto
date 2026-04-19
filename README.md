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

/* FOTO 1 */

.polaroid.foto1::before{
content:"";
position:absolute;
top:10px;
left:10px;
right:10px;
bottom:40px;
background-image:url("ola.jpg");
background-size:cover;
background-position:center;
opacity:0;
animation:revelado 4s ease forwards;
}

/* FOTO 2 */

.polaroid.foto2::before{
content:"";
position:absolute;
top:10px;
left:10px;
right:10px;
bottom:40px;
background-image:url("ola2.jpg");
background-size:cover;
background-position:center;
opacity:0;
animation:revelado 4s ease forwards;
animation-delay:1.5s;
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

.timeline-container{
margin-top:40px;
display:flex;
flex-direction:column;
align-items:center;
gap:20px;
}

#contador{
font-size:20px;
text-align:center;
color:#f5e6d3;
}

.letter{
width:140px;
height:90px;
background:#f0dfc5;
cursor:pointer;
}

.timeline{
position:relative;
width:80%;
max-width:650px;
height:60px;
margin-top:20px;
}

/* línea principal */
.line{
position:absolute;
top:50%;
left:0;
right:0;
height:3px;
background:linear-gradient(to right, #f0dfc5, #ffffff, #f0dfc5);
transform:translateY(-50%);
border-radius:5px;
}

/* punta de flecha elegante */
.line::after{
content:"";
position:absolute;
right:-2px;
top:50%;
transform:translateY(-50%) rotate(45deg);
width:14px;
height:14px;
border-top:3px solid #f0dfc5;
border-right:3px solid #f0dfc5;
}

/* punto */
.dot{
position:absolute;
top:50%;
width:14px;
height:14px;
background:#ffffff;
border-radius:50%;
transform:translate(-50%,-50%);
box-shadow:0 0 10px rgba(255,255,255,0.8);
animation:pulse 2s infinite;
}

/* efecto de vida */
@keyframes pulse{
0%{ transform:translate(-50%,-50%) scale(1); }
50%{ transform:translate(-50%,-50%) scale(1.3); }
100%{ transform:translate(-50%,-50%) scale(1); }
}

/* carta grande */
.letter.big{
width:260px;
height:170px;
background:linear-gradient(145deg, #f0dfc5, #e6d2b5);
border-radius:6px;
position:relative;
cursor:pointer;
box-shadow:0 10px 20px rgba(0,0,0,0.3);
transition:0.3s;
}

/* efecto hover */
.letter.big:hover{
transform:scale(1.05);
}

/* borde tipo papel */
.letter.big::before{
content:"";
position:absolute;
top:10px;
left:10px;
right:10px;
bottom:10px;
border:1px solid rgba(0,0,0,0.2);
border-radius:4px;
}

/* línea superior tipo carta */
.letter.big::after{
content:"";
position:absolute;
top:0;
left:0;
right:0;
height:40%;
background:linear-gradient(to bottom, rgba(0,0,0,0.05), transparent);
border-radius:6px 6px 0 0;
}

.seal{
position:absolute;
bottom:12px;
right:12px;
width:22px;
height:22px;
background:#8b1e3f;
border-radius:50%;
box-shadow:0 0 6px rgba(0,0,0,0.4);
}

</style>
</head>

<body>

<div id="hearts"></div>

<!-- PAGINA 1 -->

<div id="page1">

<h1>Nuestro portal secreto</h1>
<h2>La elección</h2>

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
FELICES 8 MESES!!!
</p>

<div class="section">
  
<div>
<p>
Te amo.
Estos dias han sido movidos para nosotros.
pero jamás me olvidé de ti amor.
esta actualización se llama "la elección"
</p>
</div>

<div class="photos">
<div class="polaroid activa foto1"></div>
<div class="polaroid activa foto2"></div>  
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

Diré incansablemente lo mucho que te amo.
pero este Dia, o el de ayer no sé, es epsecial.
si estas leyendo esto es porque encontré la oportunidad de decirtelo.

tu madre siempre me dijo que eras complicada.
siempre me advirtio de ti.
pero no me importaba, porque no puedo estar mas seguro de lo que quiero en mi vida. que eres tu.

</div>

<div class="section">
  
<div class="binary">
hoy no hay puzzles, hay verdad.
los post-it con dias contienen las razones de por qué te selecioné a ti.

hoy queria recordarte que te escogí a ti.
en los buenos, y malos momentos.
te escogí aun en medio del dolor.
te escogí en medio del resentimiento.
y esta semana, te seguí escogiendo.

eres mi amada, la mujer que quiero en mi vida.
y no me cansaré de decirtelo, de lucharlo, de amarte.

porque a fin de cuentas, eso es el amor:

seleccionar, en medio de la adversidad.
</div>

</div>

<div class="timeline-container">

<div id="contador"></div>

<!-- LINEA DE TIEMPO -->
<div class="timeline">
<div class="line"></div>
<div class="dot" id="dot"></div>
</div>

<div class="letter big" onclick="openLetter()">
  <div class="seal"></div>
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
"Llevamos: "+days+" días, "+
hours+" horas, "+
minutes+" minutos y "+
seconds+" segundos ❤️"
}

setInterval(updateCounter,1000)

function updateTimeline(){
const now = new Date()

// inicio: 18 del mes actual o anterior
let start = new Date(now.getFullYear(), now.getMonth(), 18)

if(now.getDate() < 18){
start = new Date(now.getFullYear(), now.getMonth()-1, 18)
}

// fin: 18 del siguiente mes
let end = new Date(start.getFullYear(), start.getMonth()+1, 18)

const total = end - start
const progress = now - start

let percent = (progress / total) * 100
if(percent < 0) percent = 0
if(percent > 100) percent = 100

document.getElementById("dot").style.left = percent + "%"
}

setInterval(updateTimeline,1000)
updateTimeline()


/* post it */

const textos=[
"Me fijé en ti por tu corazón, por tu alma, porque eres una perla preciosa entre piedras",
"Te hablé porque vi en ti cosas que tú aún no ves, porque vi una amiga, una compañera, porque vi inocencia en un mundo destruido",
"Me confesé porque sabía que el señor me estaba permitiendo sentir por ti, porque no era normal lo que sentía cuando le hablaba a Dios de ti.",
"Te pedí formalizar, porque estoy seguro de que eras tú, quien queria en mi vida, porque Dios me habló, me estremeció, me hizo llorar, y me respondió.",
"Te besé porque las palabras no daban a basto, porque quería demostrate que SOLO ERES TÚ, y que te escogí",
"Te escogí, por tu corazón, por que veo cosas en ti, porque veo futuro en ti, porque Dios lo confirmó, porque estoy dispuesto a vivir una vida contigo.",
"Y a pesar de que me digan: Te equivocaste, Elegiste mal, te advertí, El señor reprenda el enemigo, porque la duda no es bienvenida en un corazón que elgió también, creer en lo que Dios dijo: Ahí es.",

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
Preciosa, yo te amo.
y cada post-it tambien representa que no solo te elegí en el pololeo, o en la adversidad, te elegí, en ese encuentro de Dorcas, pero mas importante aún:
Dios te seleccionó para mi
Dios me seleccionó para ti
asi que no dudemos
ni en la adversidad
ni en la incredulidad 
ni en la prueba 
El amor es mas fuerte.
¿O no?
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
