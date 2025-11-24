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
      font-family: "JetBrains Mono", monospace !important;
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

    .button-container {
      display: flex;
      justify-content: space-between;
      padding: 0px;
      width: 100%;
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
    <option value="aleatorio">Aleatório</option>
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
      <option value="0.4">Médio</option>
      <option value="0.6">Alto</option>
      <option value="1.0">Perfeito</option>
    </select>
    <div class="button-container">
      <button onclick="gerar()">Gerar aleatoriamente…</button>
      <button onclick="copiarFicha()">Copiar Ficha...</button>
    </div>


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

  <h2>Competências</h2>
    <label id="labelCompetencias">pontos restantes</label>
    <div class="campo">
      <label>Socos:</label>
      <input type="number" id="socos" min="0" max="5" value="0"/>
    </div>
    <div class="campo">
      <label>Chute:</label>
      <input type="number" id="chute" min="0" max="5" value="0"/>
    </div>
    <div class="campo">
      <label>Armso:</label>
      <input type="number" id="armso" min="0" max="5" value="0"/>
    </div>
    <div class="campo">
      <label>Armas:</label>
      <input type="number" id="armas" min="0" max="5" value="0"/>
    </div>
    <div class="campo">
      <label>Psque:</label>
      <input type="number" id="psque" min="0" max="5" value="0"/>
    </div>
  <h2>Naturezas</h2>
    <label id="labelNaturezas">...</label>
    <select id="selecNaturezas">
      <option value="">— Escolha —</option>
    </select>
    <div id="lista-naturezas"></div>
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
  const maxComp = {
    "20": 2,
    "50": 4,
    "70": 5,
    "200":5
  }

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

  let naturezas = {};
  // TODO: Separar os treinamentos e capacidades dessa lista de Naturezas, aproveitar para adcionar as capacidades genericas de sentido, cosmo e etc.
  // TODO: Adcionar as caracteristicas às naturezas, em preparação para a adição da geração de tecnicas
  const dictNaturezas = {
    "Calor": {
      "requesito": () => true,
      "rankPorNv": [20,20,20],
      "dependentes": ["Cosmo Ardente"]
    },
    "Frio": {
      "requesito": () => true,
      "rankPorNv": [20,20,20],
      "dependentes": ["Cosmo Glacial"]
    },
    "Raio": {
      "requesito": () => true,
      "rankPorNv": [20,20,20],
      "dependentes": ["Cosmo Trovejante"]
    },
    "Vento": {
      "requesito": () => true,
      "rankPorNv": [20,20,20],
      "dependentes": ["Cosmo Tempestuoso"]
    },
    "Água": {
      "requesito": () => true,
      "rankPorNv": [20,20,20],
      "dependentes": ["Cosmo Hídrico"]
    },
    "Terra": {
      "requesito": () => true,
      "rankPorNv": [20,20,20],
      "dependentes": ["Cosmo Térreo"]
    },
    "Luz": {
      "requesito": () => true,
      "rankPorNv": [20,20,20],
      "dependentes": ["Cosmo Luminoso"]
    },
    "Sombra": {
      "requesito": () => true,
      "rankPorNv": [20,20,20],
      "dependentes": ["Cosmo Obscuro"]
    },
    "Posição de Iai": {
      "requesito": () => true,
      "rankPorNv": [20,20,50],
      "dependentes": []
    },
    "Morte Negra": {
      "requesito": () => true,
      "rankPorNv": [20,20,50],
      "dependentes": []
    },
    "Ondas de Choque": {
      "requesito": () => true,
      "rankPorNv": [20,20,50],
      "dependentes": []
    },
    "Tatuagem Taonia": {
      "requesito": () => true,
      "rankPorNv": [20,20,50],
      "dependentes": []
    },
    "Pontos Cósmicos": {
      "requesito": () => true,
      "rankPorNv": [20,20,50],
      "dependentes": []
    },
    "Clarividência": {
      "requesito": () => true,
      "rankPorNv": [20,20,50],
      "dependentes": []
    },
    "Cosmo Ardente": {
      "requesito": () => naturezas["Calor"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": ["Poder Solar"]
    },
    "Cosmo Glacial": {
      "requesito": () => naturezas["Frio"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": ["Zero Absoluto"]
    },
    "Cosmo Trovejante": {
      "requesito": () => naturezas["Raio"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": ["Corrente Eterna"]
    },
    "Cosmo Tempestuoso": {
      "requesito": () => naturezas["Vento"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": ["Colapso Atmosférico"]
    },
    "Cosmo Hídrico": {
      "requesito": () => naturezas["Água"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": ["Fúria Diluviana"]
    },
    "Cosmo Térreo": {
      "requesito": () => naturezas["Terra"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": ["Cataclismo Titânico"]
    },
    "Cosmo Luminoso": {
      "requesito": () => naturezas["Luz"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": ["Brilho Estelar"]
    },
    "Cosmo Obscuro": {
      "requesito": () => naturezas["Sombra"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": ["Abismo Infinito"]
    },
    "Sekishiki": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": ["Fogo Fátuo", "Manipulação de Almas"]
    },
    "Ilusão": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Som": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Destruição Imperfeita": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": ["Destruição Perfeita"]
    },
    "Cura": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": ["Cura Mental", "Cura Espiritual"]
    },
    "Cura Mental": {
      "requesito": () => naturezas["cura"] > 0,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Cura Espiritual": {
      "requesito": () => naturezas["cura"] > 0,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Controlar Animais": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Controlar Plantas": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Força Cósmica": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Manipulação de Almas": {
      "requesito": () => naturezas["sekishiki"] === 3,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Leitura de Mentes": {
      "requesito": () => true,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Poder Solar": {
      "requesito": () => naturezas["Cosmo Ardente"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Zero Absoluto": {
      "requesito": () => naturezas["Cosmo Glacial"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Corrente Eterna": {
      "requesito": () => naturezas["Cosmo Trovejante"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Colapso Atmosférico": {
      "requesito": () => naturezas["Cosmo Tempestuoso"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Fúria Diluviana": {
      "requesito": () => naturezas["Cosmo Hídrico"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Cataclismo Titânico": {
      "requesito": () => naturezas["Cosmo Térreo"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Brilho Estelar": {
      "requesito": () => naturezas["Cosmo Luminoso"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Abismo Infinito": {
      "requesito": () => naturezas["Cosmo Obscuro"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Gravidade": {
      "requesito": () => valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Fogo Fátuo": {
      "requesito": () => naturezas["Sekishiki"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Destruição Perfeita": {
      "requesito": () => naturezas["Destruição Imperfeita"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    },
    "Cosmo Puro": {
      "requesito": () => naturezas["Destruição Perfeita"] === 3 && valores["sen"] >= 50,
      "rankPorNv": [20,50,70],
      "dependentes": []
    }
  };

  const multiplicadorRaridade = 10;
  const comum = 15;
  const incomum = 8;
  const raro = 3;
  const evoluçãoDireta = comum * multiplicadorRaridade;


  const classes = {
    "brutamontes": {
      "ordemAtr": ["for", "res", "vel", "von", "men", "esp", "int", "cos"],
      "proporcaoCompNatArtes": [5,1,3],
      "proporcaoComp": [3,3,2,1,1],
      "naturezas": { // TODO: pesos do elemental, colocado aq só para teste
        "Calor": comum,
        "Frio": comum,
        "Raio": comum,
        "Vento": comum,
        "Água": comum,
        "Terra": comum,
        "Luz": comum,
        "Sombra": comum,
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Ondas de Choque": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Cosmo Ardente": evoluçãoDireta,
        "Cosmo Glacial": evoluçãoDireta,
        "Cosmo Trovejante": evoluçãoDireta,
        "Cosmo Tempestuoso": evoluçãoDireta,
        "Cosmo Hídrico": evoluçãoDireta,
        "Cosmo Térreo": evoluçãoDireta,
        "Cosmo Luminoso": evoluçãoDireta,
        "Cosmo Obscuro": evoluçãoDireta,
        "Sekishiki": raro,
        "Ilusão": raro,
        "Som": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evoluçãoDireta,
        "Cura Espiritual": evoluçãoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evoluçãoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evoluçãoDireta,
        "Zero Absoluto": evoluçãoDireta,
        "Corrente Eterna": evoluçãoDireta,
        "Colapso Atmosférico": evoluçãoDireta,
        "Fúria Diluviana": evoluçãoDireta,
        "Cataclismo Titânico": evoluçãoDireta,
        "Brilho Estelar": evoluçãoDireta,
        "Abismo Infinito": evoluçãoDireta,
        "Gravidade": incomum,
        "Fogo Fátuo": evoluçãoDireta,
        "Destruição Perfeita": evoluçãoDireta,
        "Cosmo Puro": raro,
      }
    },
    "artistaMarcial": {
      "ordemAtr": ["vel", "for", "int", "res", "von", "men", "esp", "cos"],
      "proporcaoCompNatArtes": [3,1,5],
      "proporcaoComp": [2,2,1,2,1],
      "naturezas": { // TODO: pesos do elemental, colocado aq só para teste
        "Calor": comum,
        "Frio": comum,
        "Raio": comum,
        "Vento": comum,
        "Água": comum,
        "Terra": comum,
        "Luz": comum,
        "Sombra": comum,
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Ondas de Choque": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Cosmo Ardente": evoluçãoDireta,
        "Cosmo Glacial": evoluçãoDireta,
        "Cosmo Trovejante": evoluçãoDireta,
        "Cosmo Tempestuoso": evoluçãoDireta,
        "Cosmo Hídrico": evoluçãoDireta,
        "Cosmo Térreo": evoluçãoDireta,
        "Cosmo Luminoso": evoluçãoDireta,
        "Cosmo Obscuro": evoluçãoDireta,
        "Sekishiki": raro,
        "Ilusão": raro,
        "Som": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evoluçãoDireta,
        "Cura Espiritual": evoluçãoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evoluçãoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evoluçãoDireta,
        "Zero Absoluto": evoluçãoDireta,
        "Corrente Eterna": evoluçãoDireta,
        "Colapso Atmosférico": evoluçãoDireta,
        "Fúria Diluviana": evoluçãoDireta,
        "Cataclismo Titânico": evoluçãoDireta,
        "Brilho Estelar": evoluçãoDireta,
        "Abismo Infinito": evoluçãoDireta,
        "Gravidade": incomum,
        "Fogo Fátuo": evoluçãoDireta,
        "Destruição Perfeita": evoluçãoDireta,
        "Cosmo Puro": raro,
      }
    },
    "elemental": {
      "ordemAtr": ["cos", "von", "int", "res", "vel", "men", "esp", "for"],
      "proporcaoCompNatArtes": [3,5,1],
      "proporcaoComp": [1,1,1,1,3],
      "naturezas": {
        "Calor": comum,
        "Frio": comum,
        "Raio": comum,
        "Vento": comum,
        "Água": comum,
        "Terra": comum,
        "Luz": comum,
        "Sombra": comum,
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Ondas de Choque": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Cosmo Ardente": evoluçãoDireta,
        "Cosmo Glacial": evoluçãoDireta,
        "Cosmo Trovejante": evoluçãoDireta,
        "Cosmo Tempestuoso": evoluçãoDireta,
        "Cosmo Hídrico": evoluçãoDireta,
        "Cosmo Térreo": evoluçãoDireta,
        "Cosmo Luminoso": evoluçãoDireta,
        "Cosmo Obscuro": evoluçãoDireta,
        "Sekishiki": raro,
        "Ilusão": raro,
        "Som": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evoluçãoDireta,
        "Cura Espiritual": evoluçãoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evoluçãoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evoluçãoDireta,
        "Zero Absoluto": evoluçãoDireta,
        "Corrente Eterna": evoluçãoDireta,
        "Colapso Atmosférico": evoluçãoDireta,
        "Fúria Diluviana": evoluçãoDireta,
        "Cataclismo Titânico": evoluçãoDireta,
        "Brilho Estelar": evoluçãoDireta,
        "Abismo Infinito": evoluçãoDireta,
        "Gravidade": incomum,
        "Fogo Fátuo": evoluçãoDireta,
        "Destruição Perfeita": evoluçãoDireta,
        "Cosmo Puro": raro,
      }
    },
    "espiritualista": {
      "ordemAtr": ["cos", "esp", "von", "men", "int", "res", "vel", "for"],
      "proporcaoCompNatArtes": [5,3,1],
      "proporcaoComp": [1,1,1,1,3],
      "naturezas": { // TODO: pesos do elemental, colocado aq só para teste
        "Calor": comum,
        "Frio": comum,
        "Raio": comum,
        "Vento": comum,
        "Água": comum,
        "Terra": comum,
        "Luz": comum,
        "Sombra": comum,
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Ondas de Choque": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Cosmo Ardente": evoluçãoDireta,
        "Cosmo Glacial": evoluçãoDireta,
        "Cosmo Trovejante": evoluçãoDireta,
        "Cosmo Tempestuoso": evoluçãoDireta,
        "Cosmo Hídrico": evoluçãoDireta,
        "Cosmo Térreo": evoluçãoDireta,
        "Cosmo Luminoso": evoluçãoDireta,
        "Cosmo Obscuro": evoluçãoDireta,
        "Sekishiki": raro,
        "Ilusão": raro,
        "Som": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evoluçãoDireta,
        "Cura Espiritual": evoluçãoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evoluçãoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evoluçãoDireta,
        "Zero Absoluto": evoluçãoDireta,
        "Corrente Eterna": evoluçãoDireta,
        "Colapso Atmosférico": evoluçãoDireta,
        "Fúria Diluviana": evoluçãoDireta,
        "Cataclismo Titânico": evoluçãoDireta,
        "Brilho Estelar": evoluçãoDireta,
        "Abismo Infinito": evoluçãoDireta,
        "Gravidade": incomum,
        "Fogo Fátuo": evoluçãoDireta,
        "Destruição Perfeita": evoluçãoDireta,
        "Cosmo Puro": raro,
      }
    },
    "ilusionista": {
      "ordemAtr": ["int", "men", "esp", "von", "res", "vel", "cos", "for"],
      "proporcaoCompNatArtes": [5,3,1],
      "proporcaoComp": [1,1,1,1,3],
      "naturezas": { // TODO: pesos do elemental, colocado aq só para teste
        "Calor": comum,
        "Frio": comum,
        "Raio": comum,
        "Vento": comum,
        "Água": comum,
        "Terra": comum,
        "Luz": comum,
        "Sombra": comum,
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Ondas de Choque": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Cosmo Ardente": evoluçãoDireta,
        "Cosmo Glacial": evoluçãoDireta,
        "Cosmo Trovejante": evoluçãoDireta,
        "Cosmo Tempestuoso": evoluçãoDireta,
        "Cosmo Hídrico": evoluçãoDireta,
        "Cosmo Térreo": evoluçãoDireta,
        "Cosmo Luminoso": evoluçãoDireta,
        "Cosmo Obscuro": evoluçãoDireta,
        "Sekishiki": raro,
        "Ilusão": raro,
        "Som": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evoluçãoDireta,
        "Cura Espiritual": evoluçãoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evoluçãoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evoluçãoDireta,
        "Zero Absoluto": evoluçãoDireta,
        "Corrente Eterna": evoluçãoDireta,
        "Colapso Atmosférico": evoluçãoDireta,
        "Fúria Diluviana": evoluçãoDireta,
        "Cataclismo Titânico": evoluçãoDireta,
        "Brilho Estelar": evoluçãoDireta,
        "Abismo Infinito": evoluçãoDireta,
        "Gravidade": incomum,
        "Fogo Fátuo": evoluçãoDireta,
        "Destruição Perfeita": evoluçãoDireta,
        "Cosmo Puro": raro,
      }
    }
  };

  function clear() {
    document.querySelectorAll("input").forEach(el => {
      
      el.value = 0;
      if (el.id.startsWith("nivel-")) {
        const nomeNat = el.id.replace("nivel-", "");
        atualizarNatureza(nomeNat, 0);
      }
    });
    update(document.body);
  }

  function atualizarNatureza(nome, nivel = 1) {
    const container = document.getElementById("lista-naturezas");

    if (nivel <= 0) {
      delete naturezas[nome];
      const old = document.getElementById("nat-" + nome);
      if (old) old.remove();
      return;
    }

    naturezas[nome] = nivel;

    if (!document.getElementById("nat-" + nome)) {
      const div = document.createElement("div");
      div.className = "campo";
      div.id = "nat-" + nome;

      div.innerHTML = `
        <label>${nome}:</label>
        <input type="number" min="0" max="3" value="${nivel}" id="nivel-${nome}">
      `;

      container.appendChild(div);

      div.querySelector("input").addEventListener("change", (ev) => {
        let v = Number(ev.target.value);
        if (v <= 0) atualizarNatureza(nome, 0);
        else naturezas[nome] = Math.min(3, v);

        update(ev.target);
      });
    } 
    else {
      document.getElementById("nivel-" + nome).value = nivel;
    }
  }

  function atualizarSelectNaturezas() {
    const select = document.getElementById("selecNaturezas");
    const selecionadas = Object.keys(naturezas);

    select.innerHTML = `<option value="">— Escolha —</option>`;

    Object.keys(dictNaturezas).forEach(nome => {
      if (selecionadas.includes(nome)) return;
      const req = dictNaturezas[nome]["requesito"]();
      if (req) {
        const opt = document.createElement("option");
        opt.value = nome;
        opt.textContent = nome;
        select.appendChild(opt);
      }
    });
  }

  function gerar() {
    clear();

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
    let rand = 1 + (Math.random() * 9);
    console.log(rand);
    while (atrRestantes > 0)
    {
      ordem.forEach(atr => {
        if (atrRestantes <= 0) return;

        // let r = (Math.random() + Math.random()) / 2; 
        // let gasto = Math.ceil(Math.pow(r, 0.8) * (atrRestantes / 2));
        let gasto = Math.ceil((1 - Math.pow(Math.random(), 2))*(atrRestantes / rand));
        aplicarPonto(atr, gasto);
        Object.keys(valores).forEach(a => {
          document.getElementById(a).value = valores[a];
        });
        update(document.body);
      });
    }
    // gera fatores aleatórios mantendo a proporção
    const fatores = classes[classe]["proporcaoCompNatArtes"].map(p => p * Math.random());

    // soma total
    const total = fatores.reduce((a, b) => a + b, 0);

    // gera valores inteiros (floor)
    let comp  = Math.min(Math.floor((fatores[0] / total) * ptsIntRestantes), 25);
    let nat   = Math.floor((fatores[1] / total) * ptsIntRestantes);
    let artes = Math.floor((fatores[2] / total) * ptsIntRestantes);

    // ajustar diferença causada pelos floors
    let soma = comp + nat + artes;
    let diff = ptsIntRestantes - soma;
    const vars = ["comp", "nat", "artes"];

    while (diff > 0) {
        const v = vars[Math.floor(Math.random() * vars.length)];
        if (v === "comp" && comp < 25) comp++;
        if (v === "nat") nat++;
        if (v === "artes") artes++;
        diff--;
    }

    function aplicarComp(qtd) {
      const fatores = classes[classe]["proporcaoComp"].map(p => p * Math.random());
      const total = fatores.reduce((a, b) => a + b, 0);

      armso = Math.min(Math.floor((fatores[0] / total) * qtd), maxComp[rank]);
      socos = Math.min(Math.floor((fatores[1] / total) * qtd), maxComp[rank]);
      chute = Math.min(Math.floor((fatores[2] / total) * qtd), maxComp[rank]);
      armas = Math.min(Math.floor((fatores[3] / total) * qtd), maxComp[rank]);
      psque = Math.min(Math.floor((fatores[4] / total) * qtd), maxComp[rank]);

      let soma = armso + socos + chute + armas + psque;
      let diff = qtd - soma;
      const vars = ["armso", "socos", "chute", "armas", "psque"];

      while (diff > 0) {
        const v = vars[Math.floor(Math.random() * vars.length)];
        if (v === "armso") armso = Math.min(armso + 1, maxComp[rank]); 
        if (v === "socos") socos = Math.min(socos + 1, maxComp[rank]);
        if (v === "chute") chute = Math.min(chute + 1, maxComp[rank]); 
        if (v === "armas") armas = Math.min(armas + 1, maxComp[rank]);
        if (v === "psque") psque = Math.min(psque + 1, maxComp[rank]);
        soma = armso + socos + chute + armas + psque;
        diff = qtd - soma;
      }
      document.getElementById("socos").value = socos;
      document.getElementById("chute").value = chute;
      document.getElementById("armso").value = armso;
      document.getElementById("armas").value = armas;
      document.getElementById("psque").value = psque;
      update(document.body);
    }
    aplicarComp(comp);

    if (nat > 0) {
      let nRest = nat;

      while (nRest > 0) {
        atualizarSelectNaturezas();
        // recalcula todas as opções e seus pesos a cada iteração
        const todasOpcoes = [
          ...Array.from(document.querySelectorAll("#selecNaturezas option")).map(o => o.value),
          ...Object.keys(naturezas)
        ].filter(v => v && v !== ""); // remove valores vazios

        let listaPesada = [];
        todasOpcoes.forEach(nome => {
          let peso = classes[classe]["naturezas"][nome] || 0;

          // aumenta peso se já existe na variavel naturezas
          if (Object.keys(naturezas).includes(nome)) peso = peso * multiplicadorRaridade;

          for (let i = 0; i < peso; i++) listaPesada.push(nome);
        });

        if (listaPesada.length === 0) break; // evita loop infinito

        // escolhe uma natureza aleatoriamente da lista pesada
        const index = Math.floor(Math.random() * listaPesada.length);
        const natEscolhida = listaPesada[index];

        if (!naturezas[natEscolhida]) naturezas[natEscolhida] = 0;

        if (naturezas[natEscolhida] < 3) {
          naturezas[natEscolhida]++;
          atualizarNatureza(natEscolhida, naturezas[natEscolhida]);
          nRest--;
        }
      }
    }
    update(document.body);
  }

  function copiarFicha() {
    // Coleta as informações do formulário
    const classe = document.getElementById("classe").value;
    const rank = document.getElementById("rank").value;
    const subrank = document.getElementById("subrank").value;
    
    // Atributos
    const forca = document.getElementById("for").value;
    const resis = document.getElementById("res").value;
    const velocidade = document.getElementById("vel").value;
    const inteligencia = document.getElementById("int").value;
    const vontade = document.getElementById("von").value;
    const mente = document.getElementById("men").value;
    const espirito = document.getElementById("esp").value;
    const sentido = document.getElementById("sen").value;
    const cosmo = document.getElementById("cos").value;

    // Naturezas Cósmicas
    let naturezasTexto = '';
    Object.keys(naturezas).forEach(natureza => {
      naturezasTexto += `- ${natureza}: ${naturezas[natureza]}\n`;
    });

    // Formatar a ficha
    let ficha = `*[FICHA DE INIMIGO]*\n\n`;

    ficha += `*Classe:*\n- ${classe.charAt(0).toUpperCase() + classe.slice(1)}\n`;
    ficha += `*Rank:*\n- ${rank === "20" ? "Sobrehumano" : rank === "50" ? "Superhumano" : rank === "70" ? "Milagre" : "Deus"} ${subrank === "1.0" ? "Perfeito" : subrank === "0.6" ? "Alto" : subrank === "0.4" ? "Médio" : "Baixo"}\n\n`;

    ficha += `*Atributos:*\n\`\`\`\n`;
    ficha += `- Força: ${forca}\n`;
    ficha += `- Resis: ${resis}\n`;
    ficha += `- Veloc: ${velocidade}\n`;
    ficha += `- Intel: ${inteligencia}\n`;
    ficha += `- Vntad: ${vontade}\n`;
    ficha += `- Mente: ${mente}\n`;
    ficha += `- Spirt: ${espirito}\n`;
    ficha += `- Sentd: ${sentido}\n`;
    ficha += `- Cosmo: ${cosmo}\n`;
    ficha += `\`\`\`\n`;

    if (naturezasTexto) {
      ficha += `*Naturezas Cósmicas:*\n${naturezasTexto}`;
    }

    // Copiar para a área de transferência
    navigator.clipboard.writeText(ficha).then(() => {
      alert('Ficha copiada para a área de transferência!');
    }).catch((error) => {
      console.error('Erro ao copiar a ficha: ', error);
    });
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
    ptsIntTotal = socos + chute + armso + armas + psque + Object.values(naturezas).reduce((acc, val) => acc + val, 0);

    atrRestantes = Math.min(Math.max(((rank-minAtr[rank])*9*subrank)+minAtr[rank]*9, minAtr[rank]*9), rank*9)-atrTotal;
    ptsIntRestantes = Math.floor(atrInt/2) - ptsIntTotal;

    document.getElementById("selecNaturezas").disabled = ptsIntRestantes <= 0;
    if (atrRestantes < 0) {
      alvo.value = Number(alvo.value) + atrRestantes;
      atrRestantes = 0;
    }

    if (ptsIntRestantes < 0) {
      alvo.value = Number(alvo.value) + ptsIntRestantes;
      if (alvo.id.startsWith("nivel-")) {
        const nomeNat = alvo.id.replace("nivel-", "");
        naturezas[nomeNat] = Number(naturezas[nomeNat]) + ptsIntRestantes;
      }
      ptsIntRestantes = 0;
    }
    document.getElementById("labelAtributos").textContent =  atrRestantes+" pontos de atributos restantes";
    document.getElementById("labelCompetencias").textContent = ptsIntRestantes+" pontos de aprendizagem restantes";
    document.getElementById("labelNaturezas").textContent = ptsIntRestantes+" pontos de aprendizagem restantes";
    
    atualizarSelectNaturezas();
  }
  document.addEventListener("change", function(event) {
    if (event.target.id == "rank" | event.target.id == "subrank" | event.target.id == "classe") clear();
    if (event.target.id === "selecNaturezas") {
      const val = event.target.value;
      if (val === "") return;

      if (!naturezas[val]) {
        atualizarNatureza(val, 1); // nível inicial
        event.target.value = "";
      }
    }
    update(event.target);
  });
  update(document.body);
</script>
</body>
</html>