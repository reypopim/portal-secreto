<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Solo para ti</title>
  <style>
    body
    {
      .title {
  font-size: 32px;
  margin-bottom: 5px;
  letter-spacing: 2px;
}
.subtitle {
  font-size: 16px;
  color: #bbbbbb;
  margin-bottom: 30px;
  font-style: italic;
}
      margin: 0;
      height: 100vh;
      background: #3a1c2e;
      color: #eaeaea;
      font-family: 'Georgia', serif;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: center;
    }

    .box {
  animation: aparecer 1.5s ease;
}

@keyframes aparecer {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

    input {
      padding: 10px;
      font-size: 18px;
      width: 120px;
      text-align: center;
      background: #111;
      color: #fff;
      border: 1px solid #555;
      border-radius: 6px;
    }

    button {
      margin-top: 15px;
      padding: 10px 20px;
      font-size: 16px;
      background: #222;
      color: #fff;
      border: 1px solid #666;
      border-radius: 6px;
      cursor: pointer;
    }

    button:hover {
      background: #333;
    }

    .hidden {
      display: none;
    }

    .message {
      white-space: pre-line;
      margin-top: 20px;
      font-size: 18px;
      line-height: 1.6;
    }

    
  </style>
</head>

<body>
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



<div class="box" id="lock">
  <h1 class="title">Nuestro Lugar Secreto</h1>
  <p class="subtitle">Algunas fechas no se olvidan</p>
  
  <p>Ingresa el número correcto</p>
  <input type="number" id="code" />
  <br>
  <button onclick="unlock()">Entrar</button>
</div>
.postits{
  position: fixed;
  left: 0;
  top: 30%;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.postit{
  background: #ffd86b;
  color: #333;
  padding: 12px 18px;
  width: 160px;
  font-family: 'Courier New', monospace;
  cursor: pointer;
  transform: translateX(-120px);
  transition: transform 0.4s;
  border-radius: 0 8px 8px 0;
  box-shadow: 2px 4px 8px rgba(0,0,0,0.3);
}

.postit:hover{
  transform: translateX(0);
}


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

<script>
  function unlock() {
    const value = document.getElementById("code").value;
    if (value === "15") {
      document.getElementById("lock").classList.add("hidden");
      document.getElementById("content").classList.remove("hidden");
    } else {
      alert("Amor, intentalo otra vez");
    }
  }
</script>

</body>
</html>
