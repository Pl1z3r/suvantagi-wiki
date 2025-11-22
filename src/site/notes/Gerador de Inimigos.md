---
{"dg-publish":true,"permalink":"/gerador-de-inimigos/"}
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
    }

    h1 {
      margin-bottom: 20px;

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
    }

    input,
    select {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border-radius: 5px;
      color: var(--text-normal);
      border: 1px solid var(--background-modifier-border);
      background: var(--background-secondary);
;
    }

    input:hover,
    select:hover {
      outline: none;
      border-color: var(--text-normal);
      filter: brightness(0.85);
    }

    button {
      margin-top: 15px;
      padding: 10px 15px;
      border: none;
      border-radius: 6px;
      background: var(--background-secondary);
      cursor: pointer;
    }

    button:hover {
      filter: brightness(0.85);
    }
  </style>
</head>
<body>

<div class="section">
  <h2>Classe</h2>
  <select id="classe">
    <option value="aleatorio">aleatorio</option>
    <option value="brutamontes">Brutamontes</option>
    <option value="artistaMarcial">Artista Marcial</option>
    <option value="elemental">Elemental</option>
    <option value="espiritualista">Espiritualista</option>
    <option value="ilusionista">Ilusionista</option>
  </select>
  <h2>Rank</h2>
    <select id= "rank">
      <option value="20">Sobrehumano</option>
      <option value="50">Superhumano</option>
      <option value="70">Milagre</option>
      <option value="200">Deus</option>
    </select>
  <h2>SubRank</h2>
    <select id= "subrank">
      <option value="0.2">Baixo</option>
      <option value="0.4">Medio</option>
      <option value="0.6">Alto</option>
      <option value="1.0">Perfeito</option>
    </select>
    <button onclick="gerar()">Gerar aleatoriamente...</button>

</div>
<div class="section">
  <h2>Atributos</h2> 
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

  <h2>Competencias</h2>
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
  <h2>Naturezas</h2>
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
</div>

<script>
  let rank = Number(document.getElementById("rank")?.value || 20);
  let subrank = Number(document.getElementById("subrank")?.value || 0.2);
  let classe = String(document.getElementById("classe")?.value || "brutamontes");
  const minAtr = {
    "20": 5,   // Sobrehumano
    "50": 20,  // Superhumano
    "70": 50,  // Milagre
    "200": 70  // Deus
  };

  let atrFor = Number(document.getElementById("for")?.value || 1);
  let atrRes = Number(document.getElementById("res")?.value || 1);
  let atrVel = Number(document.getElementById("vel")?.value || 1);
  let atrInt = Number(document.getElementById("int")?.value || 1);
  let atrVon = Number(document.getElementById("von")?.value || 1);
  let atrMen = Number(document.getElementById("men")?.value || 1);
  let atrEsp = Number(document.getElementById("esp")?.value || 1);
  let atrSen = Number(document.getElementById("sen")?.value || 1);
  let atrCos = Number(document.getElementById("cos")?.value || 0);

  let valores = {
    get ["for"]() { return atrFor; },
    set ["for"](v) { atrFor = v; },

    get ["res"]() { return atrRes; },
    set ["res"](v) { atrRes = v; },

    get ["vel"]() { return atrVel; },
    set ["vel"](v) { atrVel = v; },

    get ["int"]() { return atrInt; },
    set ["int"](v) { atrInt = v; },

    get ["von"]() { return atrVon; },
    set ["von"](v) { atrVon = v; },

    get ["men"]() { return atrMen; },
    set ["men"](v) { atrMen = v; },

    get ["esp"]() { return atrEsp; },
    set ["esp"](v) { atrEsp = v; },

    get ["sen"]() { return atrSen; },
    set ["sen"](v) { atrSen = v; },

    get ["cos"]() { return atrCos; },
    set ["cos"](v) { atrCos = v; }
  };

  let socos = Number(document.getElementById("socos")?.value || 0);
  let chute = Number(document.getElementById("chute")?.value || 0);
  let armso = Number(document.getElementById("armso")?.value || 0);
  let armas = Number(document.getElementById("armas")?.value || 0);
  let psque = Number(document.getElementById("psque")?.value || 0);
  
  let atrTotal = atrFor + atrRes + atrVel + atrInt + atrVon + atrMen + atrEsp + atrSen +  atrCos;
  let ptsIntTotal = socos + chute + armso + armas + psque;

  let atrRestantes = Math.min(Math.max(((rank-minAtr[rank])*9*subrank)+minAtr[rank]*9, minAtr[rank]*9), rank*9)-atrTotal;
  let ptsIntRestantes = Math.floor(atrInt/2) - ptsIntTotal;

  const classes = {
    "brutamontes": {
      "ordemAtr": ["for", "res", "vel", "von", "men", "esp", "int", "cos"],
      "proporcaoCompNatArtes": [5,1,3],
      "proporcaoComp": [3,3,2,1,1]
    },
    "artistaMarcial": {
      "ordemAtr": ["vel", "for", "int", "res", "von", "men", "esp", "cos"],
      "proporcaoCompNatArtes": [3,1,5],
      "proporcaoComp": [2,2,1,2,1]
    },
    "elemental": {
      "ordemAtr": ["cos", "von", "int", "res", "vel", "men", "esp", "for"],
      "proporcaoCompNatArtes": [3,5,1],
      "proporcaoComp": [1,1,1,1,3]
    },
    "espiritualista": {
      "ordemAtr": ["cos", "esp", "von", "men", "int", "res", "vel", "for"],
      "proporcaoCompNatArtes": [5,3,1],
      "proporcaoComp": [1,1,1,1,3]
    },
    "ilusionista": {
      "ordemAtr": ["int", "men", "esp", "von", "res", "vel", "cos", "for"],
      "proporcaoCompNatArtes": [5,3,1],
      "proporcaoComp": [1,1,1,1,3]
    }
  };
  function gerar() {
    document.querySelectorAll("input").forEach(el => {
      el.value = 0;
    });
    update(document.body);

    const ordem = classes[classe].ordemAtr;

    function aplicarPonto(atr, qtd)
    {
      valores[atr] = Math.min(valores[atr]+qtd,rank);

      if (valores[atr] > valores["sen"]) {
        let excedente = valores[atr] - valores["sen"];
        valores["sen"] = Math.min(rank, Math.ceil(valores["sen"] + excedente));
      }
      return true;
    }
    while (atrRestantes > 0)
    {
      ordem.forEach(atr => {
        if (atrRestantes <= 0) return;

        // let r = (Math.random() + Math.random()) / 2; 
        // let gasto = Math.ceil(Math.pow(r, 0.8) * (atrRestantes / 2));
        let gasto = Math.ceil((1 - Math.pow(Math.random(), 2))*(atrRestantes / 2));
        aplicarPonto(atr, gasto);
        Object.keys(valores).forEach(a => {
          document.getElementById(a).value = valores[a];
        });

        update(document.body);
      });
    }
  }

  function update(alvo) {
    if (document.getElementById("classe").value == "aleatorio") {
      const total = document.getElementById("classe").length;
      const index = Math.floor(Math.random() * (total -1)) + 1; 
      document.getElementById("classe").selectedIndex = index;
    }
    // coleta de variaveis
    rank = Number(document.getElementById("rank")?.value || 20);
    subrank = Number(document.getElementById("subrank")?.value || 0.2);
    classe = String(document.getElementById("classe")?.value || "aleatorio");

    Object.keys(valores).forEach(a => {
      valores[a] = Number(document.getElementById(a)?.value || 1);
    });

    socos = Number(document.getElementById("socos")?.value || 0);
    chute = Number(document.getElementById("chute")?.value || 0);
    armso = Number(document.getElementById("armso")?.value || 0);
    armas = Number(document.getElementById("armas")?.value || 0);
    psque = Number(document.getElementById("psque")?.value || 0);

    // validando
    valores["sen"] = Math.min(Math.max(atrSen, minAtr[rank]), rank);
    Object.keys(valores).forEach(a => {
      valores[a] = Math.min(Math.max(valores[a], minAtr[rank]), atrSen);
    });
    Object.keys(valores).forEach(a => {
      document.getElementById(a).value = valores[a];
    });

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

    atrTotal = atrFor + atrRes + atrVel + atrInt + atrVon + atrMen + atrEsp + atrSen +  atrCos;
    ptsIntTotal = socos + chute + armso + armas + psque;

    atrRestantes = Math.min(Math.max(((rank-minAtr[rank])*9*subrank)+minAtr[rank]*9, minAtr[rank]*9), rank*9)-atrTotal;
    ptsIntRestantes = Math.floor(atrInt/2) - ptsIntTotal;

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
    if (event.target.id == "rank" | event.target.id == "subrank" | event.target.id == "classe"){
      document.querySelectorAll("input").forEach(el => {
        el.value = 0;
      });
    }
    update(event.target);
  });
  update(document.body);
</script>
</body>
</html>