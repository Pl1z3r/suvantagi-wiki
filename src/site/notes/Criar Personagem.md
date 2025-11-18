---
{"dg-publish":true,"permalink":"/criar-personagem/"}
---

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Character Manager</title>
  <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@300;400;500;700&display=swap" rel="stylesheet">

  <style>
    body {
      font-family: "JetBrains Mono", monospace;
      background: #201f1f;
      padding: 20px;
      line-height: 1.6;
    }

    h1 {
      margin-bottom: 20px;
    }

    .container {
      max-width: 900px;
      margin: auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    .campo {
      display: flex;
      align-items: center;
      margin-bottom: 10px;
      gap: 8px;
    }

    .section {
      margin-bottom: 25px;
      padding-bottom: 20px;
      border-bottom: 2px solid #ccc;
    }

    label {
      display: block;
      margin-top: 10px;
      font-weight: bold;
    }

    input, select {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border-radius: 5px;
      border: 1px solid #999;
    }

    button {
      margin-top: 15px;
      padding: 10px 15px;
      border: none;
      border-radius: 6px;
      background: #333;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background: #555;
    }

    .character-card {
      background: #fafafa;
      border: 1px solid #ddd;
      padding: 15px;
      margin-bottom: 15px;
      border-radius: 8px;
      white-space: pre-wrap;
    }

  </style>
</head>
<body>

<div class="container">
  <h1>Criador de Personagens</h1>
      <div class="section">
        <label>Nome</label>
          <div class="campo">
            <input id="name"/>
          </div>

        <label>Rank</label>
          <select id= "rank">
            <option value="20">Sobrehumano</option>
            <option value="50">Superhumano</option>
            <option value="70">Milagre</option>
            <option value="200">Deus</option>
          </select>
    
        <label>SubRank</label>
          <select id= "subrank">
            <option value="0.2">Baixo</option>
            <option value="0.4">Medio</option>
            <option value="0.6">Alto</option>
            <option value="1.0">Perfeito</option>
          </select>
      </div>
      <div class="section">
        <label>Atributos</label> 
        <button onclick="spreadAtr()">Aleatorizar</button>
        <p></p>
        <label id="labelAtributos">20 pontos restantes</label>
          <div class="campo">
            <label>For:</label>
            <input id="for" value="1"/>
          </div>
          <div class="campo">
            <label>Res:</label>
            <input id="res" value="1"/>
          </div>
          <div class="campo">
            <label>Vel:</label>
            <input id="vel" value="1"/>
          </div>
          <div class="campo">
            <label>Int:</label>
            <input id="int" value="1"/>
          </div>
          <div class="campo">
            <label>Von:</label>
            <input id="von" value="1"/>
          </div>
          <div class="campo">
            <label>Men:</label>
            <input id="men" value="1"/>
          </div>
          <div class="campo">
            <label>Esp:</label>
            <input id="esp" value="1"/>
          </div>
          <div class="campo">
            <label>Sen:</label>
            <input id="sen" value="1"/>
          </div>
          <div class="campo">
            <label>Cos:</label>
            <input id="cos" value="0"/>
          </div>

      </div>
      <div class="section">
        <label>Competencias</label>
          <button onclick="spreadCom()">Aleatorizar</button>
        <p></p>
        <label id="pontosRestantes">20 pontos restantes</label>
        <div class="campo">
            <label>Socos:</label>
            <input id="socos" value="0"/>
          </div>
          <div class="campo">
            <label>Chute:</label>
            <input id="chute" value="0"/>
          </div>
          <div class="campo">
            <label>Armso:</label>
            <input id="armso" value="0"/>
          </div>
          <div class="campo">
            <label>Armas:</label>
            <input id="armas" value="0"/>
          </div>
          <div class="campo">
            <label>Psque:</label>
            <input id="psque" value="0"/>
          </div>

      </div>
      <div class="section">
        <label>Naturezas</label>
          <button onclick="spreadCom()">Aleatorizar</button>
        <p></p>
        <label id="labelNaturezas"></label>
        <select id="selecNaturezas">
          <option value="">-- escolha --</option>
          <option value="calor">Calor</option>
          <option value="frio">Frio</option>
          <option value="relampago">Relampago</option>
          <option value="agua">Água</option>
          <option value="terra">Terra</option>
          <option value="ar">Ar</option>
          <option value="luz">Luz</option>
          <option value="sombras">Sombras</option>
          <option value="destruicaoImperfeita">Destruição Imperfeita</option>
          <option value="destuicaoPerfeita">Destruição Perfeita</option>
          <option value="cosmoPuro">Cosmo Puro</option>
        </select>
        <button onclick="adcionarNatureza()">Adcionar</button>
        <p></p>
      </div>


  
</div>

<script>
  let rank = "20";
  let subrank = "0.2";
  function update() {
    rank = document.getElementById("rank").value;
    subrank = document.getElementById("subrank").value;
    document.getElementById("labelAtributos").textContent = rank*subrank*9+" pontos restantes";
    }

  document.getElementById("rank").addEventListener("change", function() {
    update();
  }); 
   document.getElementById("subrank").addEventListener("change", function() {
    update();
  });
   document.getElementById("int").addEventListener("change", function() {
    update();
  });
  document.getElementById("sen").addEventListener("change", function() {
    update();
  });
</script>

</body>
</html>
