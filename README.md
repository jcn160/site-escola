<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Escola Paranaense de Refrigeração</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-image: url('https://blog.zanottirefrigeracao.com.br/wp-content/uploads/2017/09/camara-fria-frigorifica-scaled.jpg');
      background-size: cover;
      background-position: center;
      margin: 0;
      padding: 0;
      color: white;
    }

    .container {
      background-color: rgba(0, 0, 128, 0.8);
      max-width: 400px;
      margin: 80px auto;
      padding: 20px;
      border-radius: 12px;
    }

    h1 {
      text-align: center;
      margin-bottom: 20px;
    }

    label {
      display: block;
      margin-top: 10px;
    }

    input, select {
      width: 100%;
      padding: 8px;
      border-radius: 5px;
      border: none;
      margin-top: 5px;
    }

    button {
      width: 100%;
      padding: 10px;
      margin-top: 15px;
      background-color: white;
      color: navy;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }

    .success {
      text-align: center;
      margin-top: 15px;
      color: lightgreen;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Escola Paranaense de Refrigeração</h1>
    <form id="form">
      <label for="nome">Nome completo:</label>
      <input type="text" id="nome" name="nome" required />

      <label for="cpf">CPF:</label>
      <input type="text" id="cpf" name="cpf" required />

      <label for="telefone">Telefone:</label>
      <input type="tel" id="telefone" name="telefone" required />

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required />

      <label for="endereco">Endereço:</label>
      <input type="text" id="endereco" name="endereco" required />

      <label for="curso">Curso:</label>
      <input type="text" id="curso" name="curso" required />

      <label for="acordo">Acordo:</label>
      <input type="text" id="acordo" name="acordo" required />

      <label for="turma">Turma:</label>
      <input type="text" id="turma" name="turma" required />

      <button type="submit">Enviar</button>
      <p class="success" id="mensagem"></p>
    </form>
  </div>

  <script>
    document.getElementById("form").addEventListener("submit", function(e) {
      e.preventDefault();

      const data = {
        nome: document.getElementById("nome").value,
        cpf: document.getElementById("cpf").value,
        telefone: document.getElementById("telefone").value,
        email: document.getElementById("email").value,
        endereco: document.getElementById("endereco").value,
        curso: document.getElementById("curso").value,
        acordo: document.getElementById("acordo").value,
        turma: document.getElementById("turma").value
      };

      fetch("https://api.sheetbest.com/sheets/7293bda3-ca6c-494d-8930-ea32243061d3", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify(data)
      })
      .then((res) => {
        if (res.ok) {
          document.getElementById("mensagem").textContent = "Dados enviados com sucesso!";
          document.getElementById("form").reset();
        } else {
          document.getElementById("mensagem").textContent = "Erro ao enviar dados.";
        }
      })
      .catch(() => {
        document.getElementById("mensagem").textContent = "Erro ao enviar dados.";
      });
    });
  </script>
</body>
</html>
