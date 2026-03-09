<!DOCTYPE html>
<html lang="es">

<head>
<meta charset="UTF-8">
<title>Nuestro lugar</title>

<style>

/* ===== FONDO ===== */

body{
margin:0;
height:100vh;
background:linear-gradient(135deg,#2b0f1a,#3a1c2e,#1c0f18);
color:#f5f5f5;
font-family:Georgia,serif;
display:flex;
align-items:center;
justify-content:center;
text-align:center;
overflow:hidden;
}

/* ESTRELLAS */

body::before{
content:"";
position:fixed;
width:100%;
height:100%;
background-image:
radial-gradient(2px 2px at 20% 30%,#fff,transparent),
radial-gradient(2px 2px at 70% 80%,#fff,transparent),
radial-gradient(1px 1px at 40% 60%,#fff,transparent),
radial-gradient(2px 2px at 90% 20%,#fff,transparent);
opacity:0.25;
pointer-events:none;
}

/* ===== CAJAS ===== */

.box{
max-width:600px;
padding:40px;
border-radius:12px;
background:rgba(255,255,255,0.05);
border:1px solid rgba(255,255,255,0.1);
}

.hidden{
display:none;
}

/* TITULO */

.title{
font-size:34px;
}

.subtitle{
color:#d7c6c6;
margin-bottom:30px;
}

/* INPUTS */

.codeInputs{
display:flex;
gap:10px;
justify-content:center;
}

.codeInputs input{
width:50px;
height:50px;
font-size:24px;
text-align:center;
border-radius:6px;
border:none;
}

/* MENSAJE */

.message{
white-space:pre-line;
line-height:1.7;
}

/* POST ITS LATERALES */

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
cursor:pointer;
transform:translateX(-130px);
transition:0.4s;
border-radius:0 8px 8px 0;
}

.postit:hover{
transform:translateX(0);
}

/* NOTA CENTRAL */

.nota{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background:rgba(0,0,0,0.6);
display:none;
justify-content:center;
align-items:center;
backdrop-filter:blur(6px);
}

.notaContenido{
background:#ffe97a;
padding:40px;
width:300px;
border-radius:10px;
color:#333;
}

</style>
</head>


<body>

<!-- POSTITS -->

<div class="postits">

<div class="postit" onclick="abrirNota('triste')">léeme cuando estés triste</div>
<div class="postit" onclick="abrirNota('feliz')">léeme cuando estés feliz</div>
<div class="postit" onclick="abrirNota('enojada')">léeme cuando estés enojada</div>

</div>


<!-- PANTALLA BLOQUEO -->

<div class="box" id="lock">

<h1 class="title">Nuestro lugar secreto</h1>
<p class="subtitle">Algunas fechas no se olvidan</p>

<p>Ingresa el código</p>

<div class="codeInputs">
<input id="c1" maxlength="1">
<input id="c2" maxlength="1">
<input id="c3" maxlength="1">
<input id="c4" maxlength="1">
</div>

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


<!-- POSTIT CENTRAL -->

<div id="notaCentral" class="nota" onclick="cerrarNota()">

<div class="notaContenido" onclick="event.stopPropagation()">

<p id="textoNota">
Aquí puedes escribir tu mensaje inicial.
</p>

</div>

</div>


<script>

/* DESBLOQUEO */

function unlock(){

let code =
document.getElementById("c1").value +
document.getElementById("c2").value +
document.getElementById("c3").value +
document.getElementById("c4").value

if(code === "0615"){

document.getElementById("lock").classList.add("hidden")
document.getElementById("content").classList.remove("hidden")

abrirNota("inicio")

}else{

alert("No es ese el codigo amor.")

}

}

/* POSTITS */

function abrirNota(tipo){

let texto="amor"

if(tipo==="inicio"){
texto="Aquí puedes poner la primera carta o mensaje que quieras que lea."
}

if(tipo==="triste"){
texto="amor"
}

if(tipo==="feliz"){
texto="amor"
}

if(tipo==="enojada"){
texto="amor"
}

document.getElementById("textoNota").innerText = texto
document.getElementById("notaCentral").style.display="flex"

}

function cerrarNota(){
document.getElementById("notaCentral").style.display="none"
}

</script>

</body>
</html>
