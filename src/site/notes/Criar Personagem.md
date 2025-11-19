---
{"dg-publish":true,"permalink":"/criar-personagem/","updated":"2025-11-19T01:58:25.380-03:00"}
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
      background: var(--background-primary);
      color: var(--text-normal);
      line-height: 1.6;
      display: flex;
      align-items: center;
      max-width: 700px;
    }

    h1 {
      margin-bottom: 20px;
      color: var(--text-accent);
    }

    .container {
      max-width: 900px;
      margin: auto;
      background: var(--background-primary);
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
      border-bottom: 2px solid var(--background-modifier-border);
    }

    label {
      display: block;
      margin-top: 10px;
      font-weight: bold;
      color: var(--text-normal);
    }

    input,
    select {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border-radius: 5px;
      background: var(--background-secondary);
      color: var(--text-normal);
      border: 1px solid var(--background-modifier-border);
    }

    input:focus,
    select:focus {
      outline: none;
      border-color: var(--text-normal);
    }

    button {
      margin-top: 15px;
      padding: 10px 15px;
      border: none;
      border-radius: 6px;
      background: var(--interactive-normal);
      color: var(--text-normal);
      cursor: pointer;
    }

    button:hover {
      background: #121212;
    }
  </style>
</head>
<body>

<div class="container">
      <div class="section">
        <label>Classe</label>
        <select id="classe">
          <option value="aleatorio">aleatorio</option>
          <option value="brutamontes">Brutamontes</option>
          <option value="artista marcial">Artista Marcial</option>
          <option value="elemental">Elemental</option>
          <option value="espiritualista">Espiritualista</option>
          <option value="ilusionista">Ilusionista</option>
        </select>

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
            <input type="number" id="for" value="1"/>
          </div>
          <div class="campo">
            <label>Res:</label>
            <input type="number" id="res" value="1"/>
          </div>
          <div class="campo">
            <label>Vel:</label>
            <input type="number" id="vel" value="1"/>
          </div>
          <div class="campo">
            <label>Int:</label>
            <input type="number" id="int" value="1"/>
          </div>
          <div class="campo">
            <label>Von:</label>
            <input type="number" id="von" value="1"/>
          </div>
          <div class="campo">
            <label>Men:</label>
            <input type="number" id="men" value="1"/>
          </div>
          <div class="campo">
            <label>Esp:</label>
            <input type="number" id="esp" value="1"/>
          </div>
          <div class="campo">
            <label>Sen:</label>
            <input type="number" id="sen" value="1"/>
          </div>
          <div class="campo">
            <label>Cos:</label>
            <input type="number" id="cos" value="0"/>
          </div>

      </div>
      <div class="section">
        <label>Competencias</label>
          <button onclick="spreadCom()">Aleatorizar</button>
        <p></p>
        <label id="labelCompetencias">pontos restantes</label>
        <div class="campo">
            <label>Socos:</label>
            <input type="number" id="socos" value="0"/>
          </div>
          <div class="campo">
            <label>Chute:</label>
            <input type="number" id="chute" value="0"/>
          </div>
          <div class="campo">
            <label>Armso:</label>
            <input type="number" id="armso" value="0"/>
          </div>
          <div class="campo">
            <label>Armas:</label>
            <input type="number" id="armas" value="0"/>
          </div>
          <div class="campo">
            <label>Psque:</label>
            <input type="number" id="psque" value="0"/>
          </div>

      </div>
      <div class="section">
        <label>Naturezas</label>
          <button onclick="spreadCom()">Aleatorizar</button>
        <p></p>
        <label id="labelNaturezas">...</label>
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
  let nome, rank, subrank = "";
  let atrFor, atrRes, atrVel,
      atrInt, atrVon, atrMen,
      atrEsp, atrSen, atrCos = 0;;
  const minAtr = {
    "20": 5,   // Sobrehumano
    "50": 20,  // Superhumano
    "70": 50,  // Milagre
    "200": 70  // Deus
  };
  function update(alvo) {
    if (document.getElementById("classe").value == "aleatorio") {
      const total = document.getElementById("classe").length;
      const index = Math.floor(Math.random() * (total -1)) + 1; 
      document.getElementById("classe").selectedIndex = index;
    }
    // coleta de variaveis
    let rank = Number(document.getElementById("rank")?.value || 0);
    let subrank = Number(document.getElementById("subrank")?.value || 0);

    let atrFor = Number(document.getElementById("for")?.value || 1);
    let atrRes = Number(document.getElementById("res")?.value || 1);
    let atrVel = Number(document.getElementById("vel")?.value || 1);
    let atrInt = Number(document.getElementById("int")?.value || 1);
    let atrVon = Number(document.getElementById("von")?.value || 1);
    let atrMen = Number(document.getElementById("men")?.value || 1);
    let atrEsp = Number(document.getElementById("esp")?.value || 1);
    let atrSen = Number(document.getElementById("sen")?.value || 1);
    let atrCos = Number(document.getElementById("cos")?.value || 0);

    let socos = Number(document.getElementById("socos")?.value || 0);
    let chute = Number(document.getElementById("chute")?.value || 0);
    let armso = Number(document.getElementById("armso")?.value || 0);
    let armas = Number(document.getElementById("armas")?.value || 0);
    let psque = Number(document.getElementById("psque")?.value || 0);

    // validando
    atrSen = Math.min(Math.max(atrSen, minAtr[rank]), rank);
    atrFor = Math.min(Math.max(atrFor, minAtr[rank]), atrSen);
    atrRes = Math.min(Math.max(atrRes, minAtr[rank]), atrSen);
    atrVel = Math.min(Math.max(atrVel, minAtr[rank]), atrSen);
    atrInt = Math.min(Math.max(atrInt, minAtr[rank]), atrSen);
    atrVon = Math.min(Math.max(atrVon, minAtr[rank]), atrSen);
    atrMen = Math.min(Math.max(atrMen, minAtr[rank]), atrSen);
    atrEsp = Math.min(Math.max(atrEsp, minAtr[rank]), atrSen);
    atrCos = Math.min(Math.max(atrCos, minAtr[rank]), atrSen);

    document.getElementById("for").value = atrFor;
    document.getElementById("res").value = atrRes;
    document.getElementById("vel").value = atrVel;
    document.getElementById("int").value = atrInt;
    document.getElementById("von").value = atrVon;
    document.getElementById("men").value = atrMen;
    document.getElementById("esp").value = atrEsp;
    document.getElementById("sen").value = atrSen;
    document.getElementById("cos").value = atrCos;

    socos = Math.min(Math.max(socos, 0), 5);
    chute = Math.min(Math.max(chute, 0), 5);
    armso = Math.min(Math.max(armso, 0), 5);
    armas = Math.min(Math.max(armas, 0), 5);
    psque = Math.min(Math.max(psque, 0), 5);

    document.getElementById("socos").value = socos;
    document.getElementById("chute").value = chute;
    document.getElementById("armso").value = armso;
    document.getElementById("armas").value = armas;
    document.getElementById("psque").value = psque;

    let atrTotal = atrFor + atrRes + atrVel + atrInt + atrVon + atrMen + atrEsp + atrSen +  atrCos;
    let ptsIntTotal = socos + chute + armso + armas + psque;

    let atrRestantes = (minAtr[rank]*9)+(rank*subrank*9) - atrTotal;
    let ptsIntRestantes = Math.floor(atrInt/2) - ptsIntTotal;

    if (atrRestantes < 0) {
      alvo.value = Number(alvo.value) + atrRestantes;
      atrRestantes = 0;
    }

    if (ptsIntRestantes < 0) {
      alvo.value = Number(alvo.value) + ptsIntRestantes;
      ptsIntRestantes = 0;
    }

    document.getElementById("labelAtributos").textContent =  atrRestantes+" pontos de atributos restantes";
    document.getElementById("labelCompetencias").textContent = ptsIntRestantes+" pontos de aprendizagem restantes";
    document.getElementById("labelNaturezas").textContent = ptsIntRestantes+" pontos de aprendizagem restantes";



  }
  document.addEventListener("change", function(event) {
    if (event.target.id == "rank"){
      document.querySelectorAll("input").forEach(el => {
        el.value = 0;
      });
    }
    update(event.target);
  });
  update();
</script>

</body>
</html>
