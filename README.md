<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Item Aleatório da Arrecadação</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      background: #f7f7f7;
    }
    #item {
      font-size: 3rem;
      margin-top: 20px;
      padding: 20px 40px;
      background: white;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }
    button {
      margin-top: 30px;
      padding: 10px 20px;
      font-size: 1.2rem;
      cursor: pointer;
      border: none;
      border-radius: 10px;
      background: #007bff;
      color: white;
    }
  </style>
</head>
<body>
  <h1>Seu item para doação:</h1>
  <div id="item">Clique no botão</div>
  <button onclick="gerar()">Gerar Item Aleatório</button>

  <script>
    // Lista de itens e limite por item
    const limites = {
      "A": 100,
      "B": 100,
      "C": 100,
      "D": 100,
      "E": 100,
      "F": 100,
      "G": 100,
      "H": 100,
      "O": 100,
      "J": 100
    };

    function gerar() {
      // Filtra apenas itens que ainda têm unidades sobrando
      const disponiveis = Object.keys(limites).filter(item => limites[item] > 0);

      if (disponiveis.length === 0) {
        document.getElementById("item").innerText = "Todos os itens já atingiram o limite!";
        return;
      }

      const escolhido = disponiveis[Math.floor(Math.random() * disponiveis.length)];

      // Reduz 1 unidade do item sorteado
      limites[escolhido]--;

      document.getElementById("item").innerText = `${escolhido} (restam ${limites[escolhido]} unidades)`;
    }
  </script>
</body>
</html>
