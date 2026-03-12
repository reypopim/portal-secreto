<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mi Página Web</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      margin: 0;
      padding: 0;
    }
    header {
      background: #4CAF50;
      color: white;
      padding: 20px 0;
      text-align: center;
    }
    main {
      padding: 20px;
      max-width: 800px;
      margin: auto;
      background: white;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.1);
    }
    button {
      background: #4CAF50;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover {
      background: #45a049;
    }
  </style>
</head>
<body>
  <header>
    <h1>Bienvenido a Mi Página Web</h1>
  </header>
  <main>
    <h2>¡Hola, mundo!</h2>
    <p>Esta es una página web de ejemplo creada con HTML, CSS y JavaScript.</p>
    <button onclick="mostrarMensaje()">Haz clic aquí</button>
    <p id="mensaje"></p>
  </main>
  <script>
    function mostrarMensaje() {
      document.getElementById('mensaje').textContent = '¡Gracias por hacer clic!';
    }
  </script>
</body>
</html>
