# FERIDAS-TESTE
Este site tem como objetivo oferecer orientações confiáveis, atualizadas e de fácil compreensão sobre a prevenção, avaliação e cuidado com feridas. A plataforma é voltada tanto para profissionais da saúde quanto para estudantes, cuidadores e o público em geral, promovendo informação baseada em boas práticas e evidências científicas.

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Portal de Feridas</title>

  <!-- PWA -->
  <link rel="manifest" href="manifest.json">
  <meta name="theme-color" content="#0ea5e9">

  <!-- Ícone -->
  <link rel="icon" href="icon-192.png">

  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f1f5f9;
    }

    header {
      background: #0ea5e9;
      color: white;
      padding: 15px;
      text-align: center;
      font-size: 20px;
      font-weight: bold;
    }

    .container {
      padding: 15px;
    }

    .card {
      background: white;
      padding: 15px;
      border-radius: 12px;
      margin-bottom: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      cursor: pointer;
    }

    /* POPUP */
    .popup {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 60%;
      background: white;
      border-radius: 20px 20px 0 0;
      box-shadow: 0 -5px 15px rgba(0,0,0,0.2);
      display: none;
      padding: 20px;
    }

    .close {
      float: right;
      cursor: pointer;
      font-weight: bold;
      font-size: 18px;
    }
  </style>
</head>

<body>

<header>Portal de Feridas</header>

<div class="container">
  <div class="card" onclick="abrirPopup('Úlcera por pressão: aliviar pressão, manter pele limpa e seca.')">
    🛏️ Úlcera por pressão
  </div>

  <div class="card" onclick="abrirPopup('Ferida diabética: controle glicêmico e avaliação vascular.')">
    🩸 Ferida diabética
  </div>

  <div class="card" onclick="abrirPopup('Ferida infectada: observar pus, odor, calor local e encaminhar.')">
    ⚠️ Ferida infectada
  </div>
</div>

<!-- POPUP -->
<div class="popup" id="popup">
  <span class="close" onclick="fecharPopup()">X</span>
  <h3>Orientação</h3>
  <p id="conteudo"></p>
</div>

<script>
function abrirPopup(texto) {
  document.getElementById("popup").style.display = "block";
  document.getElementById("conteudo").innerText = texto;
}

function fecharPopup() {
  document.getElementById("popup").style.display = "none";
}

// Registrar Service Worker
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('service-worker.js');
}
</script>

</body>
</html>
