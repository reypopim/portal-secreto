<!DOCTYPE html>
<html lang="es">

<head>
<meta charset="UTF-8">
<title>Nuestro lugar</title>

<style>

/* ===== FONDO ===== */

body{
margin:0;
background: linear-gradient(135deg,#2b0f1a,#3a1c2e,#1c0f18);
color:#f5f5f5;
font-family:Georgia,serif;
overflow-x:hidden;
}

/* ===== ESTRELLAS ===== */

body::before{
content:"";
position:fixed;
width:100%;
height:100%;
background-image:
radial-gradient(2px 2px at 20% 30%,#fff,transparent),
radial-gradient(2px 2px at 70% 80%,#fff,transparent),
radial-gradient(1px 1px at 40% 60%,#fff,transparent);
opacity:0.25;
pointer-events:none;
}

/* ===== PORTADA ===== */

.portada{
height:100vh;
display:flex;
align-items:center;
justify-content:center;
text-align:center;
}

.box{
max-width:600px;
padding:40px;
border-radius:12px;
background:rgba(255,255,255,0.05);
border:1px solid rgba(255,255,255,0.1);
}

.title{
font-size:34px;
margin-bottom:5px;
}

.subtitle{
font-style:italic;
margin-bottom:30px;
color:#d7c6c6;
}

/* ===== INPUT ===== */

input{
padding:10px;
font-size:18px;
width:120px;
text-align:center;
background:#f3e6d0;
color:#333;
border:1px solid #aaa;
border-radius:6px;
}

button{
margin-top:15px;
padding:10px 20px;
font-size:16px;
background:#f3e6d0;
color:#333;
border:1px solid #aaa;
border-radius:6px;
cursor:pointer;
}

/* ===== PAGINA 2 ===== */

.pagina2{
display:none;
padding-top:80px;
min-height:200vh;
text-align:center;
}

/* ===== CONTADOR ===== */

.contador{
font-size:20px;
margin-bottom:40px;
}

/* ===== MENSAJE ===== */

.message{
white-space:pre-line;
line-height:1.7;
margin:50px auto;
max-width:600px;
}

/* ===== GALERIA ===== */

.galeria{
display:flex;
justify-content:center;
gap:20px;
flex-wrap:wrap;
margin:80px 0;
}

.galeria img{
width:200px;
border-radius:10px;
}

/* ===== CARTAS ===== */

.cartas{
max-width:700px;
margin:auto;
}

.carta{
background:#fff3;
padding:25px;
margin:20px;
border-radius:10px;
}

/* ===== POSTITS ===== */

.postits{
position:fixed;
left:0;
top:30%;
display:flex;
flex-direction:column;
gap:15px;
}

.postit{
background:#ffe97a;
color:#333;
padding:12px 18px;
width:170px;
font-family:'Courier New';
cursor:pointer;
transform:translateX(-130px);
transition:transform 0.4s;
border-radius:0 8px 8px 0;
}

.postit:hover{
transform:translateX(0);
}

/* ===== NOTA ===== */

.nota{
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

.notaContenido{
background:#ffe97a;
padding:40px;
border-radius:10px;
color:#333;
max-width:320px;
}

</style>
</head>

<body>


<!-- PORTADA -->

<div class="portada" id="pagina1">

<div class="box">

<h1 class="title">Nuestro lugar secreto</h1>

<p class="subtitle">Algunas fechas no se olvidan</p>

<p>Ingresa el número correcto</p>

<input type="number" id="code">

<br>

<button onclick="unlock()">Entrar</button>

</div>

</div>


<!-- PAGINA 2 -->

<div class="pagina2" id="pagina2">


<div class="contador" id="contador"></div>


<!-- MENSAJE CIFRADO -->

<div class="message">

RECUERDA  
19 5 3 22 5 19 4 1  

</div>


<!-- GALERIA -->

<div class="galeria">

<img src="https://picsum.photos/300/200">
<img src="https://picsum.photos/301/200">
<img src="https://picsum.photos/302/200">

</div>


<!-- CARTAS -->

<div class="cartas">

<div class="carta">
Aquí podrás escribir una carta.
</div>

<div class="carta">
Otra carta editable.
</div>

</div>


<!-- POSTITS LATERALES -->

<div class="postits">

<div class="postit" onclick="abrirNota('triste')">
léeme cuando estés triste
</div>

<div class="postit" onclick="abrirNota('feliz')">
léeme cuando estés feliz
</div>

<div class="postit" onclick="abrirNota('enojada')">
léeme cuando estés enojada
</div>

</div>

</div>


<!-- NOTA -->

<div class="nota" id="notaCentral" onclick="cerrarNota()">

<div class="notaContenido" onclick="event.stopPropagation()">

<p id="textoNota">amor</p>

</div>

</div>


<script>

/* DESBLOQUEO */

function unlock(){

let value=document.getElementById("code").value

if(value==="15"){

document.getElementById("pagina1").style.display="none"
document.getElementById("pagina2").style.display="block"

}

}


/* CONTADOR DIAS */

let inicio=new Date("2025-08-18")
let hoy=new Date()

let dias=Math.floor((hoy-inicio)/(1000*60*60*24))

document.getElementById("contador").innerText=
"Días juntos: "+dias


/* POSTITS */

function abrirNota(tipo){

let texto=""

if(tipo==="triste"){
texto="Todo estará bien."
}

if(tipo==="feliz"){
texto="Me encanta verte feliz."
}

if(tipo==="enojada"){
texto="Respira. Estoy contigo."
}

document.getElementById("textoNota").innerText=texto
document.getElementById("notaCentral").style.display="flex"

}

function cerrarNota(){
document.getElementById("notaCentral").style.display="none"
}

</script>

</body>
</html>
