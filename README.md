# Convidados-do-Casamento.
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Confirmação de Presença - Joarison & Renata</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background-color: #f5f5f5;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #0b1f3a;
      color: white;
      padding: 30px 20px;
      text-align: center;
    }

    header h1 {
      margin: 0;
      font-size: 36px;
    }

    header p {
      font-size: 18px;
      margin-top: 10px;
    }

    main {
      max-width: 600px;
      margin: 40px auto;
      background: white;
      padding: 30px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
    }

    h2 {
      color: #0b1f3a;
      margin-bottom: 20px;
    }

    label {
      display: block;
      margin-top: 15px;
      color: #333;
      font-weight: bold;
    }

    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }

    button {
      background-color: #0b1f3a;
      color: white;
      padding: 12px 20px;
      border: none;
      border-radius: 4px;
      margin-top: 20px;
      cursor: pointer;
      font-size: 16px;
    }

    button:hover {
      background-color: #132f55;
    }

    .mensagem {
      margin-top: 20px;
      font-weight: bold;
    }

    footer {
      text-align: center;
      color: #888;
      font-size: 14px;
      margin: 40px 0 20px;
    }
  </style>
</head>
<body>

  <header>
    <h1>Joarison & Renata</h1>
    <p>Nosso grande dia: 22 de Novembro de 2025 às 14h30</p>
  </header>

  <main>
    <h2>Confirmação de Presença</h2>
    <form onsubmit="validarPresenca(event)">
      <label for="nome">Nome completo:</label>
      <input type="text" id="nome" name="nome" required>

      <label for="criancas">Nome das crianças (se houver):</label>
      <input type="text" id="criancas" name="criancas">

      <label for="presenca">Você vai comparecer?</label>
      <select id="presenca" name="presenca" required>
        <option value="">Selecione</option>
        <option value="sim">Sim, com certeza!</option>
        <option value="nao">Infelizmente não poderei ir</option>
      </select>

      <button type="submit">Confirmar</button>
      <p id="mensagem" class="mensagem"></p>
    </form>
  </main>

  <main>
    <h2>Manual dos Convidados</h2>
    <ul>
      <li><strong>Horário:</strong> Chegue com 15 minutos de antecedência.</li>
      <li><strong>Traje:</strong> Esporte fino. Azul marinho é nossa cor principal!</li>
      <li><strong>Local:</strong> (em breve)</li>
      <li><strong>Crianças:</strong> São bem-vindas!</li>
      <li><strong>Lista de presentes:</strong> QR Code disponível no convite e aqui no site.</li>
    </ul>
  </main>

  <footer>
    Com carinho, Joarison & Renata
  </footer>

  <script>
    const listaConvidados = ["Juliana", "Raimundo", "Joyce", "Ítalo", "Aninha", "Allan"];

    function normalizarTexto(texto) {
      return texto.normalize("NFD").replace(/[\u0300-\u036f]/g, "").toLowerCase();
    }

    function validarPresenca(event) {
      event.preventDefault();
      const nomeDigitado = document.getElementById("nome").value.trim();
      const nomeNormalizado = normalizarTexto(nomeDigitado);
      const permitido = listaConvidados.some(nome =>
        nomeNormalizado.includes(normalizarTexto(nome))
      );

      const mensagem = document.getElementById("mensagem");

      if (permitido) {
        mensagem.style.color = "green";
        mensagem.textContent = "Presença confirmada com sucesso! Obrigado por fazer parte desse momento.";
        // Aqui você pode adicionar lógica para enviar os dados para o servidor
      } else {
        mensagem.style.color = "red";
        mensagem.textContent = "Seu nome não está na lista de convidados. Caso ache que é um erro, fale com os noivos.";
      }
    }
  </script>

</body>
</html>
