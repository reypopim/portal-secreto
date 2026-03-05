<!DOCTYPE html>
<html lang="es">

<head>
<meta charset="UTF-8">
<title>Nuestro lugar</title>

<style>

/* ===== FONDO GENERAL ===== */

body{
margin:0;
height:100vh;
background: linear-gradient(135deg,#2b0f1a,#3a1c2e,#1c0f18);
color:#f5f5f5;
font-family:Georgia,serif;
display:flex;
align-items:center;
justify-content:center;
text-align:center;
overflow:hidden;
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
radial-gradient(1px 1px at 40% 60%,#fff,transparent),
radial-gradient(2px 2px at 90% 20%,#fff,transparent),
radial-gradient(1px 1px at 10% 90%,#fff,transparent);
opacity:0.25;
pointer-events:none;
}

/* ===== CAJA CENTRAL ===== */

.box{
max-width:600px;
padding:40px;
border-radius:12px;
background:rgba(255,255,255,0.05);
border:1px solid rgba(255,255,255,0.1);
animation:aparecer 1.5s ease;
}

/* ===== ANIMACIÓN ===== */

@keyframes aparecer{
from{
opacity:0;
transform:translateY(20px);
}
to{
opacity:1;
transform:translateY(0);
}
}

/* ===== TITULO ===== */

.title{
font-size:34px;
letter-spacing:2px;
margin-bottom:5px;
}

.subtitle{
font-size:16px;
color:#d7c6c6;
margin-bottom:30px;
font-style:italic;
}

/* ===== INPUT ===== */

input{
padding:10px;
font-size:18px;
width:120px;
text-align:center;
background:#1c1c1c;
color:white;
border:1px solid #666;
border-radius:6px;
}

button{
margin-top:15px;
padding:10px 20px;
font-size:16px;
background:#2a2a2a;
color:white;
border:1px solid #777;
border-radius:6px;
cursor:pointer;
}

button:hover{
background:#444;
}

.hidden{
display:none;
}

/* ===== MENSAJE CIFRADO ===== */

.message{
white-space:pre-line;
font-size:18px;
line-height:1.7;
}

/* ===== POST IT LATERALES ===== */

.postits{
position:fixed;
left:0;
top:30%;
display:flex;
flex-direction:column;
gap:15px;
z-index:2;
}

.postit{
background:#ffe97a;
color:#333;
padding:12px 18px;
width:170px;
font-family:'Courier New',monospace;
cursor:pointer;
transform:translateX(-130px);
transition:transform 0.4s;
border-radius:0 8px 8px 0;
box-shadow:2px 4px 10px rgba(0,0,0,0.3);
}

.postit:hover{
transform:translateX(0);
}

/* ===== NOTA CENTRAL ===== */

.nota{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background:rgba(0,0,0,0.6);
display:flex;
justify-content:center;
align-items:center;
z-index:5;
}

.notaContenido{
background:#ffe97a;
padding:40px;
width:320px;
border-radius:10px;
font-family:'Courier New',monospace;
color:#333;
box-shadow:0 10px 30px rgba(0,0,0,0.5);
}

</style>
</head>


<body>

<!-- POST ITS -->

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


<!-- BLOQUEO -->

<div class="box" id="lock">

<h1 class="title">Nuestro lugar secreto</h1>
<p class="subtitle">Algunas fechas no se olvidan</p>

<p>Ingresa el número correcto</p>

<input type="number" id="code">

<br>

<button onclick="unlock()">Entrar</button>

</div>


<!-- CONTENIDO -->

<div class="box hidden" id="content">

<div class="message">

RECUERDA  
19 5 3 22 5 19 4 1  
9 4 5 5 14 5 19 16  

3 22 1 14 4 16  
21 16 4 16  
3 16 13 5 14 27 16  

5 20 21 5  
12 22 7 1 19  
7 22 1 19 4 1  

13 9 20  
3 1 19 21 1 20  
13 9 20  
17 19 16 13 5 20 1 20  

26  
13 9  
6 22 21 22 19 16  
3 16 14 21 9 7 16  

21 5  
1 13 16

</div>

</div>


<!-- NOTA CENTRAL -->

<div id="notaCentral" class="nota hidden" onclick="cerrarNota()">

<div class="notaContenido" onclick="event.stopPropagation()">

<p id="textoNota">amor</p>

<button onclick="cerrarNota()">cerrar</button>

</div>

</div>


<script>

/* DESBLOQUEO */

function unlock(){

const value=document.getElementById("code").value

if(value==="15"){

document.getElementById("lock").classList.add("hidden")
document.getElementById("content").classList.remove("hidden")

}else{

alert("No es ese número")

}

}


/* POST IT */

function abrirNota(tipo){

let texto="amor"

if(tipo==="triste"){
texto="amor"
}

if(tipo==="feliz"){
texto="amor"
}

if(tipo==="enojada"){
texto="amor"
}

document.getElementById("textoNota").innerText=texto
document.getElementById("notaCentral").classList.remove("hidden")

}

function cerrarNota(){
document.getElementById("notaCentral").classList.add("hidden")
}

</script>

</body>
</html>
