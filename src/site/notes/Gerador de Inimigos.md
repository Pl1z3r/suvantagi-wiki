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
    <label id="label-competencias">pontos restantes</label>
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
  <h2>Naturezas Cósmicas</h2>
    <label id="label-naturezas">...</label>
    <select id="select-naturezas">
      <option value="">— Escolha —</option>
    </select>
    <div id="lista-naturezas"></div>
  <h2>Artes Marciais</h2>
    <label id="label-artes">...</label>
    <select id="select-artes">
      <option value="">— Escolha —</option>
    </select>
    <div id="lista-artes"></div>
  <h2>Treinamentos</h2>
    <label id="label-treinamentos">...</label>
    <select id="select-treinamentos">
      <option value="">— Escolha —</option>
    </select>
    <div id="lista-treinamentos"></div>
  <h2>Técnicas</h2>
    <label id="label-tecnicas">...</label>
    <select id="select-tecnicas">
      <option value="">— Escolha —</option>
    </select>
    <div id="lista-tecnicas"></div>
  <h2>Combos</h2>
    <label id="label-combos">...</label>
    <select id="select-combos">
      <option value="">— Escolha —</option>
    </select>
    <div id="lista-combos"></div>
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
  let ptsIntTotal = 0;

  let atrRestantes = Math.min(Math.max(((rank-minAtr[rank])*9*subrank)+minAtr[rank]*9, minAtr[rank]*9), rank*9)-atrTotal;
  let ptsIntRestantes = 1;
  let ptsTecTotal = 0;
  let ptsTecRestantes = 1;

  let posses = {
    "naturezas": {},
    "treinamentos": {},
    "artes": {},
    "tecnicas": [],
    "combos": []
  };

  const caracteristicasGenericas = ["Restrição", "Efeito Contínuo", "Poder Passivo", "Destruição de Durabilidade", "Ataque Múltiplo", "Ataque em Área", "Energizar", "Dano Aumentado"]
  const caracteristicasEspeciais = ["Atravessar Armadura", "Dano Contínuo", "Congelamento", "Ricochete", "Paralisia", "Barreira", "Fortalecer", "Camuflagem", "Melhoria Contínua", "Ataque Espiritual", "Ataque Mental", "Enfraquecer"]

  const treinamentosGenericos = {
    "Explosão Cósmica": {
      "requesito": () => valores["sen"] >= 5,
      "rankPorNv": [20]
    },
    "Implacabilidade": {
      "requesito": () => valores["sen"] >= 10,
      "rankPorNv": [20]
    },
    "Premonição": {
      "requesito": () => valores["sen"] >= 20,
      "rankPorNv": [20]
    },
    "Lampejo (velicidade da Luz)": {
      "requesito": () => valores["sen"] >= 40,
      "rankPorNv": [20]
    },
    "Superioridade": {
      "requesito": () => valores["sen"] >= 50,
      "rankPorNv": [20]
    },
    "Milagre": {
      "requesito": () => valores["sen"] >= 60,
      "rankPorNv": [20]
    },
    "Quebra de Lei Divina": {
      "requesito": () => valores["sen"] >= 70,
      "rankPorNv": [20]
    },
    "Percepção Divina": {
      "requesito": () => valores["sen"] >= 80,
      "rankPorNv": [20]
    },
    "Criação de Lei Divina": {
      "requesito": () => valores["sen"] >= 90,
      "rankPorNv": [20]
    },
    "Grande Vontade": {
      "requesito": () => valores["sen"] >= 100,
      "rankPorNv": [20]
    }
  };
  // TODO: Adcionar as capacidades genericas de sentido, cosmo e etc.
  const dict = {
    "naturezas": {
      "Calor": {
        "requesito": () => true,
        "rankPorNv": [20,20,20],
        "caracteristicas": ["Atravessar Armadura", "Dano Contínuo"]
      },
      "Frio": {
        "requesito": () => true,
        "rankPorNv": [20,20,20],
        "caracteristicas": ["Atravessar Armadura", "Congelamento"]
      },
      "Raio": {
        "requesito": () => true,
        "rankPorNv": [20,20,20],
        "caracteristicas": ["Atravessar Armadura", "Ricochete", "Paralisia"]
      },
      "Vento": {
        "requesito": () => true,
        "rankPorNv": [20,20,20],
        "caracteristicas": ["Barreira"]
      },
      "Água": {
        "requesito": () => true,
        "rankPorNv": [20,20,20],
        "caracteristicas": ["Barreira"]
      },
      "Terra": {
        "requesito": () => true,
        "rankPorNv": [20,20,20],
        "caracteristicas": ["Barreira"]
      },
      "Luz": {
        "requesito": () => true,
        "rankPorNv": [20,20,20],
        "caracteristicas": ["Atravessar Armadura", "Camuflagem"]
      },
      "Sombra": {
        "requesito": () => true,
        "rankPorNv": [20,20,20],
        "caracteristicas": ["Atravessar Armadura", "Camuflagem", "Paralisia"]
      },
      "Ondas de Choque": {
        "requesito": () => true,
        "rankPorNv": [20,20,50],
        "caracteristicas": ["Melhoria Contínua"]
      },
      "Cosmo Ardente": {
        "requesito": () => posses["naturezas"]["Calor"] === 3,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Atravessar Armadura", "Dano Contínuo"]
      },
      "Cosmo Glacial": {
        "requesito": () => posses["naturezas"]["Frio"] === 3,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Atravessar Armadura", "Congelamento"]
      },
      "Cosmo Trovejante": {
        "requesito": () => posses["naturezas"]["Raio"] === 3,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Atravessar Armadura", "Ricochete", "Paralisia"]
      },
      "Cosmo Tempestuoso": {
        "requesito": () => posses["naturezas"]["Vento"] === 3,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Barreira"]
      },
      "Cosmo Hídrico": {
        "requesito": () => posses["naturezas"]["Água"] === 3,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Barreira"]
      },
      "Cosmo Térreo": {
        "requesito": () => posses["naturezas"]["Terra"] === 3,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Barreira"]
      },
      "Cosmo Luminoso": {
        "requesito": () => posses["naturezas"]["Luz"] === 3,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Atravessar Armadura", "Camuflagem"]
      },
      "Cosmo Obscuro": {
        "requesito": () => posses["naturezas"]["Sombra"] === 3,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Atravessar Armadura", "Ricochete", "Paralisia"]
      },
      "Sekishiki": {
        "requesito": () => true,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Ataque Espiritual"]
      },
      "Ilusão": {
        "requesito": () => true,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Ataque Mental", "Congelamento"]
      },
      "Som": {
        "requesito": () => true,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Atravessar Armadura", "Congelamento", "Enfraquecer"]
      },
      "Gravidade": {
        "requesito": () => valores["sen"] >= 50,
        "rankPorNv": [20,50,70],
        "caracteristicas": ["Potencializar", "Enfraquecer", "Paralisia"]
      },
      "Cosmo Puro": {
        "requesito": () => posses["treinamentos"]["Destruição Perfeita"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20,50,70],
        "caracteristicas": [...caracteristicasEspeciais]
      }
    },
    "treinamentos": {
      "Posição de Iai": {
        "requesito": () => true,
        "rankPorNv": [20,20,50]
      },
      "Morte Negra": {
        "requesito": () => true,
        "rankPorNv": [20,20,50]
      },
      "Tatuagem Taonia": {
        "requesito": () => true,
        "rankPorNv": [20,20,50]
      },
      "Pontos Cósmicos": {
        "requesito": () => true,
        "rankPorNv": [20,20,50]
      },
      "Clarividência": {
        "requesito": () => true,
        "rankPorNv": [20,20,50]
      },
      "Destruição Imperfeita": {
        "requesito": () => true,
        "rankPorNv": [20,50,70]
      },
      "Cura": {
        "requesito": () => true,
        "rankPorNv": [20,50,70]
      },
      "Cura Mental": {
        "requesito": () => posses["treinamentos"]["cura"] > 0,
        "rankPorNv": [20,50,70]
      },
      "Cura Espiritual": {
        "requesito": () => posses["treinamentos"]["cura"] > 0,
        "rankPorNv": [20,50,70]
      },
      "Controlar Animais": {
        "requesito": () => true,
        "rankPorNv": [20,50,70]
      },
      "Controlar Plantas": {
        "requesito": () => true,
        "rankPorNv": [20,50,70]
      },
      "Força Cósmica": {
        "requesito": () => true,
        "rankPorNv": [20,50,70]
      },
      "Manipulação de Almas": {
        "requesito": () => posses["naturezas"]["sekishiki"] === 3,
        "rankPorNv": [20,50,70]
      },
      "Leitura de Mentes": {
        "requesito": () => true,
        "rankPorNv": [20,50,70]
      },
      "Poder Solar": {
        "requesito": () => posses["naturezas"]["Cosmo Ardente"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20]
      },
      "Zero Absoluto": {
        "requesito": () => posses["naturezas"]["Cosmo Glacial"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20]
      },
      "Corrente Eterna": {
        "requesito": () => posses["naturezas"]["Cosmo Trovejante"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20]
      },
      "Colapso Atmosférico": {
        "requesito": () => posses["naturezas"]["Cosmo Tempestuoso"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20]
      },
      "Fúria Diluviana": {
        "requesito": () => posses["naturezas"]["Cosmo Hídrico"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20]
      },
      "Cataclismo Titânico": {
        "requesito": () => posses["naturezas"]["Cosmo Térreo"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20]
      },
      "Brilho Estelar": {
        "requesito": () => posses["naturezas"]["Cosmo Luminoso"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20]
      },
      "Abismo Infinito": {
        "requesito": () => posses["naturezas"]["Cosmo Obscuro"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20]
      },
      "Fogo Fátuo": {
        "requesito": () => posses["naturezas"]["Sekishiki"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20,50,70]
      },
      "Destruição Perfeita": {
        "requesito": () => posses["treinamentos"]["Destruição Imperfeita"] === 3 && valores["sen"] >= 50,
        "rankPorNv": [20,50,70]
      }
    },
    "artes": {
      "Aikidô": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Baraqah": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Bojutsu": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Boxe": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Capoeira": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
     "Forças Especiais": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Glimae": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Hsing Yi Chuan": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Jeet Kune Do": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Jiu-Jitsu": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Kabaddi": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Kalaripayt": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Karatê Rindoukan": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Karatê Shotokan": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Kempo": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Kenjutsu": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Kickboxe": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Krav Maga": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Kung Fu": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Ler Drit": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Lua": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Lucha Libre": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Luta-Livre": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Luta-Livre Nativo Americana": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Ninjitsu": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Ninjitsu Espanhol": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Pankration": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Sanbo": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Savate": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Silat": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Soul Power": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Sumô": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Tae Kwon Dô": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Tai Chi Chuan": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Pegazzani": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Thai Kickboxe": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Wu Shu": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Vale-Tudo": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      },
      "Yagli Gures": {
        "requesito": () => true,
        "rankPorNv": [20, 20, 50, 50, 70]
      }
    }
  };

  const multiplicadorRaridade = 10;
  const comum = 15;
  const incomum = 8;
  const raro = 3;
  const evolucaoDireta = comum * multiplicadorRaridade;


  const classes = {
    "brutamontes": {
      "ordemAtr": ["for", "res", "vel", "von", "men", "esp", "int", "cos"],
      "proporcaoCompNatTreArtes": [5,1,2,3],
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
        "Ondas de Choque": incomum,
        "Cosmo Ardente": evolucaoDireta,
        "Cosmo Glacial": evolucaoDireta,
        "Cosmo Trovejante": evolucaoDireta,
        "Cosmo Tempestuoso": evolucaoDireta,
        "Cosmo Hídrico": evolucaoDireta,
        "Cosmo Térreo": evolucaoDireta,
        "Cosmo Luminoso": evolucaoDireta,
        "Cosmo Obscuro": evolucaoDireta,
        "Sekishiki": raro,
        "Ilusão": raro,
        "Som": incomum,
        "Gravidade": incomum,
        "Cosmo Puro": raro,
      },
      "treinamentos": {
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evolucaoDireta,
        "Cura Espiritual": evolucaoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evolucaoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evolucaoDireta,
        "Zero Absoluto": evolucaoDireta,
        "Corrente Eterna": evolucaoDireta,
        "Colapso Atmosférico": evolucaoDireta,
        "Fúria Diluviana": evolucaoDireta,
        "Cataclismo Titânico": evolucaoDireta,
        "Brilho Estelar": evolucaoDireta,
        "Abismo Infinito": evolucaoDireta,
        "Fogo Fátuo": evolucaoDireta,
        "Destruição Perfeita": evolucaoDireta,
      },
      "artes": {
        "Aikidô": comum,
        "Baraqah": comum,
        "Bojutsu": comum,
        "Boxe": comum,
        "Capoeira": comum,
        "Forças Especiais": comum,
        "Glimae": comum,
        "Hsing Yi Chuan": comum,
        "Jeet Kune Do": comum,
        "Jiu-Jitsu": comum,
        "Kabaddi": comum,
        "Kalaripayt": comum,
        "Karatê Rindoukan": comum,
        "Karatê Shotokan": comum,
        "Kempo": comum,
        "Kenjutsu": comum,
        "Kickboxe": comum,
        "Krav Maga": comum,
        "Kung Fu": comum,
        "Ler Drit": comum,
        "Lua": comum,
        "Lucha Libre": comum,
        "Luta-Livre": comum,
        "Luta-Livre Nativo Americana": comum,
        "Ninjitsu": comum,
        "Ninjitsu Espanhol": comum,
        "Pankration": comum,
        "Sanbo": comum,
        "Savate": comum,
        "Silat": comum,
        "Soul Power": comum,
        "Sumô": comum,
        "Tae Kwon Dô": comum,
        "Tai Chi Chuan": comum,
        "Pegazzani": comum,
        "Thai Kickboxe": comum,
        "Wu Shu": comum,
        "Vale-Tudo": comum,
        "Yagli Gures": comum
      }
    },
    "artistaMarcial": {
      "ordemAtr": ["vel", "for", "int", "res", "von", "men", "esp", "cos"],
      "proporcaoCompNatTreArtes": [3,1,3,5],
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
        "Ondas de Choque": incomum,
        "Cosmo Ardente": evolucaoDireta,
        "Cosmo Glacial": evolucaoDireta,
        "Cosmo Trovejante": evolucaoDireta,
        "Cosmo Tempestuoso": evolucaoDireta,
        "Cosmo Hídrico": evolucaoDireta,
        "Cosmo Térreo": evolucaoDireta,
        "Cosmo Luminoso": evolucaoDireta,
        "Cosmo Obscuro": evolucaoDireta,
        "Sekishiki": raro,
        "Ilusão": raro,
        "Som": incomum,
        "Gravidade": incomum,
        "Cosmo Puro": raro,
      },
      "treinamentos": {
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evolucaoDireta,
        "Cura Espiritual": evolucaoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evolucaoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evolucaoDireta,
        "Zero Absoluto": evolucaoDireta,
        "Corrente Eterna": evolucaoDireta,
        "Colapso Atmosférico": evolucaoDireta,
        "Fúria Diluviana": evolucaoDireta,
        "Cataclismo Titânico": evolucaoDireta,
        "Brilho Estelar": evolucaoDireta,
        "Abismo Infinito": evolucaoDireta,
        "Fogo Fátuo": evolucaoDireta,
        "Destruição Perfeita": evolucaoDireta,
      },
      "artes": {
        "Aikidô": comum,
        "Baraqah": comum,
        "Bojutsu": comum,
        "Boxe": comum,
        "Capoeira": comum,
        "Forças Especiais": comum,
        "Glimae": comum,
        "Hsing Yi Chuan": comum,
        "Jeet Kune Do": comum,
        "Jiu-Jitsu": comum,
        "Kabaddi": comum,
        "Kalaripayt": comum,
        "Karatê Rindoukan": comum,
        "Karatê Shotokan": comum,
        "Kempo": comum,
        "Kenjutsu": comum,
        "Kickboxe": comum,
        "Krav Maga": comum,
        "Kung Fu": comum,
        "Ler Drit": comum,
        "Lua": comum,
        "Lucha Libre": comum,
        "Luta-Livre": comum,
        "Luta-Livre Nativo Americana": comum,
        "Ninjitsu": comum,
        "Ninjitsu Espanhol": comum,
        "Pankration": comum,
        "Sanbo": comum,
        "Savate": comum,
        "Silat": comum,
        "Soul Power": comum,
        "Sumô": comum,
        "Tae Kwon Dô": comum,
        "Tai Chi Chuan": comum,
        "Pegazzani": comum,
        "Thai Kickboxe": comum,
        "Wu Shu": comum,
        "Vale-Tudo": comum,
        "Yagli Gures": comum
      }
    },
    "elemental": {
      "ordemAtr": ["cos", "von", "int", "res", "vel", "men", "esp", "for"],
      "proporcaoCompNatTreArtes": [3,5,3,1],
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
        "Ondas de Choque": incomum,
        "Cosmo Ardente": evolucaoDireta,
        "Cosmo Glacial": evolucaoDireta,
        "Cosmo Trovejante": evolucaoDireta,
        "Cosmo Tempestuoso": evolucaoDireta,
        "Cosmo Hídrico": evolucaoDireta,
        "Cosmo Térreo": evolucaoDireta,
        "Cosmo Luminoso": evolucaoDireta,
        "Cosmo Obscuro": evolucaoDireta,
        "Sekishiki": raro,
        "Ilusão": raro,
        "Som": incomum,
        "Gravidade": incomum,
        "Cosmo Puro": raro,
      },
      "treinamentos": {
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evolucaoDireta,
        "Cura Espiritual": evolucaoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evolucaoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evolucaoDireta,
        "Zero Absoluto": evolucaoDireta,
        "Corrente Eterna": evolucaoDireta,
        "Colapso Atmosférico": evolucaoDireta,
        "Fúria Diluviana": evolucaoDireta,
        "Cataclismo Titânico": evolucaoDireta,
        "Brilho Estelar": evolucaoDireta,
        "Abismo Infinito": evolucaoDireta,
        "Fogo Fátuo": evolucaoDireta,
        "Destruição Perfeita": evolucaoDireta,
      },
      "artes": {
        "Aikidô": comum,
        "Baraqah": comum,
        "Bojutsu": comum,
        "Boxe": comum,
        "Capoeira": comum,
        "Forças Especiais": comum,
        "Glimae": comum,
        "Hsing Yi Chuan": comum,
        "Jeet Kune Do": comum,
        "Jiu-Jitsu": comum,
        "Kabaddi": comum,
        "Kalaripayt": comum,
        "Karatê Rindoukan": comum,
        "Karatê Shotokan": comum,
        "Kempo": comum,
        "Kenjutsu": comum,
        "Kickboxe": comum,
        "Krav Maga": comum,
        "Kung Fu": comum,
        "Ler Drit": comum,
        "Lua": comum,
        "Lucha Libre": comum,
        "Luta-Livre": comum,
        "Luta-Livre Nativo Americana": comum,
        "Ninjitsu": comum,
        "Ninjitsu Espanhol": comum,
        "Pankration": comum,
        "Sanbo": comum,
        "Savate": comum,
        "Silat": comum,
        "Soul Power": comum,
        "Sumô": comum,
        "Tae Kwon Dô": comum,
        "Tai Chi Chuan": comum,
        "Pegazzani": comum,
        "Thai Kickboxe": comum,
        "Wu Shu": comum,
        "Vale-Tudo": comum,
        "Yagli Gures": comum
      }
    },
    "espiritualista": {
      "ordemAtr": ["cos", "esp", "von", "men", "int", "res", "vel", "for"],
      "proporcaoCompNatTreArtes": [5,3,2,1],
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
        "Ondas de Choque": incomum,
        "Cosmo Ardente": evolucaoDireta,
        "Cosmo Glacial": evolucaoDireta,
        "Cosmo Trovejante": evolucaoDireta,
        "Cosmo Tempestuoso": evolucaoDireta,
        "Cosmo Hídrico": evolucaoDireta,
        "Cosmo Térreo": evolucaoDireta,
        "Cosmo Luminoso": evolucaoDireta,
        "Cosmo Obscuro": evolucaoDireta,
        "Sekishiki": evolucaoDireta,
        "Ilusão": raro,
        "Som": incomum,
        "Gravidade": incomum,
        "Cosmo Puro": raro,
      },
      "treinamentos": {
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evolucaoDireta,
        "Cura Espiritual": evolucaoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evolucaoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evolucaoDireta,
        "Zero Absoluto": evolucaoDireta,
        "Corrente Eterna": evolucaoDireta,
        "Colapso Atmosférico": evolucaoDireta,
        "Fúria Diluviana": evolucaoDireta,
        "Cataclismo Titânico": evolucaoDireta,
        "Brilho Estelar": evolucaoDireta,
        "Abismo Infinito": evolucaoDireta,
        "Fogo Fátuo": evolucaoDireta,
        "Destruição Perfeita": evolucaoDireta,
      },
      "artes": {
        "Aikidô": comum,
        "Baraqah": comum,
        "Bojutsu": comum,
        "Boxe": comum,
        "Capoeira": comum,
        "Forças Especiais": comum,
        "Glimae": comum,
        "Hsing Yi Chuan": comum,
        "Jeet Kune Do": comum,
        "Jiu-Jitsu": comum,
        "Kabaddi": comum,
        "Kalaripayt": comum,
        "Karatê Rindoukan": comum,
        "Karatê Shotokan": comum,
        "Kempo": comum,
        "Kenjutsu": comum,
        "Kickboxe": comum,
        "Krav Maga": comum,
        "Kung Fu": comum,
        "Ler Drit": comum,
        "Lua": comum,
        "Lucha Libre": comum,
        "Luta-Livre": comum,
        "Luta-Livre Nativo Americana": comum,
        "Ninjitsu": comum,
        "Ninjitsu Espanhol": comum,
        "Pankration": comum,
        "Sanbo": comum,
        "Savate": comum,
        "Silat": comum,
        "Soul Power": comum,
        "Sumô": comum,
        "Tae Kwon Dô": comum,
        "Tai Chi Chuan": comum,
        "Pegazzani": comum,
        "Thai Kickboxe": comum,
        "Wu Shu": comum,
        "Vale-Tudo": comum,
        "Yagli Gures": comum
      }
    },
    "ilusionista": {
      "ordemAtr": ["int", "men", "esp", "von", "res", "vel", "cos", "for"],
      "proporcaoCompNatTreArtes": [5,3,2,1],
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
        "Ondas de Choque": incomum,
        "Cosmo Ardente": evolucaoDireta,
        "Cosmo Glacial": evolucaoDireta,
        "Cosmo Trovejante": evolucaoDireta,
        "Cosmo Tempestuoso": evolucaoDireta,
        "Cosmo Hídrico": evolucaoDireta,
        "Cosmo Térreo": evolucaoDireta,
        "Cosmo Luminoso": evolucaoDireta,
        "Cosmo Obscuro": evolucaoDireta,
        "Sekishiki": raro,
        "Ilusão": evolucaoDireta,
        "Som": incomum,
        "Gravidade": incomum,
        "Cosmo Puro": raro,
      },
      "treinamentos": {
        "Posição de Iai": incomum,
        "Morte Negra": incomum,
        "Tatuagem Taonia": incomum,
        "Pontos Cósmicos": incomum,
        "Clarividência": incomum,
        "Destruição Imperfeita": comum,
        "Cura": incomum,
        "Cura Mental": evolucaoDireta,
        "Cura Espiritual": evolucaoDireta,
        "Controlar Animais": incomum,
        "Controlar Plantas": incomum,
        "Força Cósmica": incomum,
        "Manipulação de Almas": evolucaoDireta,
        "Leitura de Mentes": incomum,
        "Poder Solar": evolucaoDireta,
        "Zero Absoluto": evolucaoDireta,
        "Corrente Eterna": evolucaoDireta,
        "Colapso Atmosférico": evolucaoDireta,
        "Fúria Diluviana": evolucaoDireta,
        "Cataclismo Titânico": evolucaoDireta,
        "Brilho Estelar": evolucaoDireta,
        "Abismo Infinito": evolucaoDireta,
        "Fogo Fátuo": evolucaoDireta,
        "Destruição Perfeita": evolucaoDireta,
      },
      "artes": {
        "Aikidô": comum,
        "Baraqah": comum,
        "Bojutsu": comum,
        "Boxe": comum,
        "Capoeira": comum,
        "Forças Especiais": comum,
        "Glimae": comum,
        "Hsing Yi Chuan": comum,
        "Jeet Kune Do": comum,
        "Jiu-Jitsu": comum,
        "Kabaddi": comum,
        "Kalaripayt": comum,
        "Karatê Rindoukan": comum,
        "Karatê Shotokan": comum,
        "Kempo": comum,
        "Kenjutsu": comum,
        "Kickboxe": comum,
        "Krav Maga": comum,
        "Kung Fu": comum,
        "Ler Drit": comum,
        "Lua": comum,
        "Lucha Libre": comum,
        "Luta-Livre": comum,
        "Luta-Livre Nativo Americana": comum,
        "Ninjitsu": comum,
        "Ninjitsu Espanhol": comum,
        "Pankration": comum,
        "Sanbo": comum,
        "Savate": comum,
        "Silat": comum,
        "Soul Power": comum,
        "Sumô": comum,
        "Tae Kwon Dô": comum,
        "Tai Chi Chuan": comum,
        "Pegazzani": comum,
        "Thai Kickboxe": comum,
        "Wu Shu": comum,
        "Vale-Tudo": comum,
        "Yagli Gures": comum
      }
    }
  };

  function clear() {
    posses = {
      "naturezas": {},
      "treinamentos": {},
      "artes": {},
      "tecnicas": [],
      "combos": []
    };
    document.querySelectorAll("input").forEach(el => {
      el.value = 0;
      if (el.id.startsWith("nivel-")) {
        const nome = el.id.replace("nivel-", "");
        atualizarNTA(el.parentElement.id.split("-")[0], nome, 0);
      }
    });
    posses = {
      "naturezas": {},
      "treinamentos": {},
      "artes": {},
      "tecnicas": [],
      "combos": []
    };
    document.getElementById("lista-tecnicas").innerHTML = "";
    document.getElementById("lista-combos").innerHTML = "";
    update(document.body);
  }

  function atualizarNTA(dictName, nome, nivel = 1) {
    const container = document.getElementById(`lista-${dictName}`);

    if (nivel <= 0) {
      delete posses[dictName][nome];
      const old = document.getElementById(`${dictName}-` + nome);
      if (old) old.remove();
      return;
    }

    posses[dictName][nome] = nivel;

    if (!document.getElementById(`${dictName}-` + nome)) {
      const div = document.createElement("div");
      div.className = "campo";
      div.id = `${dictName}-` + nome;

      const fonte = dict[dictName][nome] ?? treinamentosGenericos[nome]; // TODO: "...??..." armengue temporario, melhor refatorar?
      div.innerHTML = `
        <label>${nome}:</label>
        <input type="number" min="0" max="${fonte["rankPorNv"]}" value="${nivel}" id="nivel-${nome}">
      `;

      container.appendChild(div);

      div.querySelector("input").addEventListener("change", (ev) => {
        let v = Number(ev.target.value);
        if (v <= 0) atualizarNTA(dictName, nome, 0);
        else posses[dictName][nome] = Math.min(3, v);

        update(ev.target);
      });
    } 
    else {
      document.getElementById("nivel-" + nome).value = nivel;
    }
  }

  function atualizarSelectTecnicas() {
    const select = document.getElementById("select-tecnicas");
    select.innerHTML = `<option value="">— Escolha —</option>`;

    Object.keys(posses.naturezas).forEach(natureza => {
      const nivel = posses.naturezas[natureza];
      if (nivel > 0) {
        const opt = document.createElement("option");
        opt.value = natureza;
        opt.textContent = `${natureza} (nível ${nivel})`;
        select.appendChild(opt);
      }
    });

    select.onchange = () => {
      const natureza = select.value;
      if (!natureza) return;

      posses.tecnicas.push({
        natureza,
        grau: 1,
        caracteristicas: []
      });
      renderTecnicas();
      
      select.value = "";
    };
  }

  function atualizarSelectNTA() {
    ["naturezas", "treinamentos", "artes"].forEach(dictName => {
      const select = document.getElementById(`select-${dictName}`);
      const selecionadas = Object.keys(posses[dictName]);

      select.innerHTML = `<option value="">— Escolha —</option>`;

      Object.keys(dict[dictName]).forEach(nome => {
        if (selecionadas.includes(nome)) return;
        const req = dict[dictName][nome]["requesito"]();
        if (req) {
          const opt = document.createElement("option");
          opt.value = nome;
          opt.textContent = nome;
          select.appendChild(opt);
        }
      });
    });
  }

  function renderTecnicas() {
    const box = document.getElementById("lista-tecnicas");
    box.innerHTML = "";

    posses.tecnicas.forEach((tec, i) => {
      const div = document.createElement("div");
      div.className = "tecnica";

      div.innerHTML = `
        <div class="campo">
          <label>${tec.natureza}</label>
          <input type="number" min="0" max="${posses.naturezas[tec.natureza]}" value="${tec.grau}" id="tec-grau-${i}">
        </div>
        <div id="tec-caracts-${i}"></div>
        <hr>
      `;

      box.appendChild(div);

      // altera grau
      document.getElementById(`tec-grau-${i}`).addEventListener("change", e => {
        let nv = Number(e.target.value);
        const max = posses.naturezas[tec.natureza];

        nv = Math.max(0, Math.min(max, nv));
        if (nv === 0) {
          posses.tecnicas.pop(i);
          renderTecnicas();
          return;
        }
        posses.tecnicas[i].grau = nv;
        // resize buffer de características
        posses.tecnicas[i].caracteristicas = (posses.tecnicas[i].caracteristicas || []).slice(0, nv + 2);

        renderTecnicas(); // rerender
      });

      renderSlotsTecnica(i);
    });
  }


  function renderSlotsTecnica(i) {
    const tec = posses.tecnicas[i];
    const qtd = 2 + tec.grau;
    const box = document.getElementById(`tec-caracts-${i}`);

    box.innerHTML = "";

    const genericas = caracteristicasGenericas || [];
    const especificas = dict.naturezas[tec.natureza]?.caracteristicas || [];
    const escolhasAtuais = tec.caracteristicas || [];

    for (let s = 0; s < qtd; s++) {
      const select = document.createElement("select");
      const valorSalvo = escolhasAtuais[s] || "";

      // placeholder
      select.insertAdjacentHTML(
        "beforeend",
        `<option value="" ${valorSalvo === "" ? "selected" : ""}>— Escolha —</option>`
      );

      [...genericas, ...especificas].forEach(opcao => {
        const podeRepetir = opcao === "Dano Aumentado";
        const jaEscolhida = escolhasAtuais.includes(opcao);

        // filtro simples e direto
        if (!podeRepetir && jaEscolhida && opcao !== valorSalvo) {
          return; // não cria option
        }

        select.insertAdjacentHTML(
          "beforeend",
          `<option value="${opcao}" ${valorSalvo === opcao ? "selected" : ""}>${opcao}</option>`
        );
      });

      select.onchange = e => {
        tec.caracteristicas[s] = e.target.value;
        renderSlotsTecnica(i);
      };
      box.appendChild(select);
    }
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
    const fatores = classes[classe]["proporcaoCompNatTreArtes"].map(p => p * Math.random());

    // soma total
    const total = fatores.reduce((a, b) => a + b, 0);

    // gera valores inteiros (floor)
    let comp  = Math.min(Math.floor((fatores[0] / total) * ptsIntRestantes), 25);
    let nat   = Math.floor((fatores[1] / total) * ptsIntRestantes);
    let tre   = Math.floor((fatores[2] / total) * ptsIntRestantes);
    let artes = Math.floor((fatores[3] / total) * ptsIntRestantes);

    // ajustar diferença causada pelos floors
    let soma = comp + nat + tre + artes;
    let diff = ptsIntRestantes - soma;
    const vars = ["comp", "nat", "tre", "artes"];

    while (diff > 0) {
        const v = vars[Math.floor(Math.random() * vars.length)];
        if (v === "comp" && comp < maxComp[rank] * 5) comp++;
        if (v === "nat") nat++;
        if (v === "tre") tre++;
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

    function aplicarNTA(dictName, qtd) {
      if (qtd > 0) {
        let nRest = qtd;

        while (nRest > 0) {
          atualizarSelectNTA();
          // recalcula todas as opções e seus pesos a cada iteração
          const todasOpcoes = [
            ...Array.from(document.querySelectorAll(`#select-${dictName} option`)).map(o => o.value),
            ...Object.keys(posses[dictName])
          ].filter(v => v && v !== ""); // remove valores vazios

          let listaPesada = [];
          todasOpcoes.forEach(nome => {
            let peso = classes[classe][dictName][nome] || 0;

            // aumenta peso se já existe na variavel naturezas
            if (Object.keys(posses[dictName]).includes(nome)) peso = peso * multiplicadorRaridade;

            for (let i = 0; i < peso; i++) listaPesada.push(nome);
          });

          if (listaPesada.length === 0) break; // evita loop infinito

          // escolhe uma natureza aleatoriamente da lista pesada
          const index = Math.floor(Math.random() * listaPesada.length);
          const NTAEscolhida = listaPesada[index];

          if (!posses[dictName][NTAEscolhida]) posses[dictName][NTAEscolhida] = 0;
          if (posses[dictName][NTAEscolhida] < dict[dictName][NTAEscolhida]["rankPorNv"].length) {
            posses[dictName][NTAEscolhida]++;
            atualizarNTA(dictName, NTAEscolhida, posses[dictName][NTAEscolhida]);
            nRest--;
          }
        }
      }
    }
    aplicarNTA("naturezas", nat);
    aplicarNTA("treinamentos", tre);
    aplicarNTA("artes", artes);
    update(document.body);

    function obterOpcoesValidasTecnica(natureza, escolhidas = []) {
      const genericas = caracteristicasGenericas || [];
      const exclusivas = dict.naturezas[natureza]?.caracteristicas || [];

      return [...genericas, ...exclusivas].filter(opcao => {
        if (opcao === "Dano Aumentado") return true;
        return !escolhidas.includes(opcao);
      });
    }

    function gerarCaracteristicasAleatorias(natureza, qtd) {
      const resultado = [];

      while (resultado.length < qtd) {
        const opcoes = obterOpcoesValidasTecnica(natureza, resultado);

        if (opcoes.length === 0) break;

        // peso maior para exclusivas
        const pesos = {};
        opcoes.forEach(op => {
          if (dict.naturezas[natureza]?.caracteristicas?.includes(op)) {
            pesos[op] = 3; // prioridade
          } else {
            pesos[op] = 1;
          }
        });

        const escolhida = escolherPonderado(pesos);
        resultado.push(escolhida);
      }

      return resultado;
    }

    function escolherPonderado(pesos) {
      const lista = [];
      Object.entries(pesos).forEach(([k, v]) => {
        for (let i = 0; i < v; i++) lista.push(k);
      });
      return lista[Math.floor(Math.random() * lista.length)];
    }


    function escolherNaturezaParaTecnica() {
      const pesos = {};

      Object.keys(posses.naturezas).forEach(n => {
        // natureza base
        pesos[n] = comum * posses.naturezas[n];

        // se for evolução direta, ganha peso enorme
        if (n.startsWith("Cosmo")) {
          pesos[n] = comum * 2 * posses.naturezas[n];
        }
      });

      return escolherPonderado(pesos);
    }


    function gerarTecnicasAleatorias() {
      let slots = ptsTecRestantes;
      if (Object.keys(posses.naturezas).length === 0) return;

      while (slots > 0) {
        const natureza = escolherNaturezaParaTecnica();
        const maxGrau = posses.naturezas[natureza] || 1;

        let grau;

        if (subrank >= 1.0) {
          // Perfeito: sempre no máximo
          grau = maxGrau;
        } else {
          const expoente = 1 / subrank;

          grau = Math.min(
            Math.ceil(Math.pow(Math.random(), expoente) * maxGrau),
            maxGrau
          );
        }

        const qtdCaracts = 2 + grau;

        const caracteristicas = gerarCaracteristicasAleatorias(
          natureza,
          qtdCaracts
        );

        posses.tecnicas.push({
          natureza,
          grau,
          caracteristicas
        });

        slots--;
      }

      renderTecnicas();
    }

    gerarTecnicasAleatorias();
    update(document.body)
  }

  function copiarFicha() {
    // Classe, Rank e Subrank já estão nas variáveis globais
    const classeNome =
      classe.charAt(0).toUpperCase() + classe.slice(1);

    const rankNome =
      rank === 20 ? "Sobrehumano" :
      rank === 50 ? "Superhumano" :
      rank === 70 ? "Milagre" : "Deus";

    const subrankNome =
      subrank === 1.0 ? "Perfeito" :
      subrank === 0.6 ? "Alto" :
      subrank === 0.4 ? "Médio" : "Baixo";

    // Naturezas
    let naturezasTexto = "";
    for (const n in posses.naturezas) {
      naturezasTexto += `- ${n}: ${posses.naturezas[n]}\n`;
    }

    // Artes Marciais
    let artesTexto = "";
    for (const t in posses.artes) {
      artesTexto += `- ${t}: ${posses.artes[t]}\n`;
    }

    // Treinamentos
    let treinamentosTexto = "";
    for (const t in posses.treinamentos) {
      treinamentosTexto += `- ${t}: ${posses.treinamentos[t]}\n`;
    }
    
    // Técnicas
    let tecnicasTexto = "";
    posses.tecnicas.forEach(tec => {
      const listaCaracts = tec.caracteristicas
        .filter(c => c && c !== "") // remove vazios
        .map(c => `  - ${c}`)
        .join("\n");

      tecnicasTexto += `- ${tec.natureza} (Grau ${tec.grau})\n`;
      tecnicasTexto += listaCaracts ? listaCaracts + "\n" : "  -\n";
    });

    // Combos
    let combosTexto = "";

    // Ficha formatada
    let ficha = `*[FICHA DE INIMIGO]*\n\n`;

    ficha += `*Classe:*\n- ${classeNome}\n`;
    ficha += `*Rank:*\n- ${rankNome} ${subrankNome}\n\n`;

    ficha += `*Atributos:*\n\`\`\`\n`;
    ficha += `- Força: ${atrFor}\n`;
    ficha += `- Resis: ${atrRes}\n`;
    ficha += `- Veloc: ${atrVel}\n`;
    ficha += `- Intel: ${atrInt}\n`;
    ficha += `- Vntad: ${atrVon}\n`;
    ficha += `- Mente: ${atrMen}\n`;
    ficha += `- Spirt: ${atrEsp}\n`;
    ficha += `- Sentd: ${atrSen}\n`;
    ficha += `- Cosmo: ${atrCos}\n`;
    ficha += `\`\`\`\n`;

    ficha += `*Competências:*\n\`\`\`\n`;
    ficha += `- Socos: ${socos}\n`;
    ficha += `- Chute: ${chute}\n`;
    ficha += `- Armas: ${armas}\n`;
    ficha += `- Armso: ${armso}\n`;
    ficha += `- Psque: ${psque}\n`;
    ficha += `\`\`\`\n`;

    if (naturezasTexto) ficha += `*Naturezas Cósmicas:*\n\`\`\`\n${naturezasTexto}\`\`\`\n`;
  
    if (artesTexto) ficha += `*Artes Marciais:*\n\`\`\`\n${artesTexto}\`\`\`\n`;

    if (treinamentosTexto) ficha += `*Treinamentos:*\n\`\`\`\n${treinamentosTexto}\`\`\`\n`;

    if (tecnicasTexto) ficha += `*Técnicas:*\n\`\`\`\n${tecnicasTexto}\`\`\`\n`;

    if (combosTexto) ficha += `*Combos:*\n\`\`\`\n${combosTexto}\`\`\`\n`;

    navigator.clipboard.writeText(ficha)
      .then(() => alert('Ficha copiada para a área de transferência!'))
      .catch(err => console.error("Erro ao copiar ficha: ", err));
  }

  function sincronizarTreinamentosGenericos() {
    Object.entries(treinamentosGenericos).forEach(([nome, dados]) => {
      const ativo = dados.requesito();

      if (ativo) {
        // adiciona se ainda não existir
        if (!(nome in posses.treinamentos)) {
          atualizarNTA("treinamentos", nome, 1); // temporario, mudar caso treinamentos genericos com niveis
        }
      } else {
        // remove se existir
        if (nome in posses.treinamentos) {
          atualizarNTA("treinamentos", nome, 0);
        }
      }
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

    let somaNTA = 0;
    ["naturezas", "treinamentos", "artes"].forEach(dictName => {
      somaNTA += Object.entries(posses[dictName]).reduce((acc, [nome, val]) => {

        // ignora treinamentos genéricos
        if (
          dictName === "treinamentos" &&
          nome in treinamentosGenericos
        ) {
          return acc;
        }

        return acc + val;
      }, 0);
    });
    ptsIntTotal = socos + chute + armso + armas + psque + somaNTA;

    atrRestantes = Math.min(Math.max(((rank-minAtr[rank])*9*subrank)+minAtr[rank]*9, minAtr[rank]*9), rank*9)-atrTotal;
    ptsIntRestantes = Math.floor(atrInt/2) - ptsIntTotal + 1;

    ptsTecTotal = posses.tecnicas.length;
    ptsTecRestantes = Math.floor(atrInt/10) - ptsTecTotal + 1;

    ["naturezas", "treinamentos", "artes"].forEach(dictName => {
      document.getElementById(`select-${dictName}`).disabled = ptsIntRestantes <= 0;
    });

    ["tecnicas", "combos"].forEach(dictName => {
      document.getElementById(`select-${dictName}`).disabled = ptsTecRestantes <= 0;
    });
    
    if (atrRestantes < 0) {
      alvo.value = Number(alvo.value) + atrRestantes;
      atrRestantes = 0;
    }

    if (ptsIntRestantes < 0) {
      alvo.value = Number(alvo.value) + ptsIntRestantes;
      if (alvo.id.startsWith("nivel-")) {
        const nome = alvo.id.replace("nivel-", "");
        posses[alvo.parentElement.id.split("-")[0]][nome] = Number(posses[alvo.parentElement.id.split("-")[0]][nome]) + ptsIntRestantes;
      }
      ptsIntRestantes = 0;
    }
    document.getElementById("labelAtributos").textContent =  atrRestantes+" pontos de atributos restantes";
    const ids = [
      "label-competencias",
      "label-treinamentos",
      "label-naturezas",
      "label-artes"
    ];

    ids.forEach(id => {
      document.getElementById(id).textContent =
        `${ptsIntRestantes} pontos de aprendizagem restantes`;
    });
    document.getElementById("label-tecnicas").textContent = `${ptsTecRestantes} slots restantes`;

    atualizarSelectTecnicas();
    atualizarSelectNTA();
    sincronizarTreinamentosGenericos();
    renderTecnicas()
  }
  document.addEventListener("change", function(event) {
    if (event.target.id == "rank" | event.target.id == "subrank" | event.target.id == "classe") clear();
    if (event.target.id.startsWith("select-")) {
      const val = event.target.value;
      if (val === "") return;
      if ("tecnicas" === event.target.id.split("-")[1]) {
        const natureza = event.target.value;
        if (!natureza) return;
        posses.tecnicas.push({
            "natureza": natureza,
            "grau": 1,
            "caracteristicas": []
        });

        event.target.value = "";

        renderTecnicas();
      }
      if (["naturezas", "artes", "treinamentos"].includes(event.target.id.split("-")[1]) && !posses[event.target.id.split("-")[1]][val]) {
        atualizarNTA(event.target.id.split("-")[1], val, 1); // nível inicial
        event.target.value = "";
      }
    }
    update(event.target);
  });
  update(document.body);
</script>
</body>
</html>