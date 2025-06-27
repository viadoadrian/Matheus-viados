<!DOCTYPE html>
<html>
<head>
  <title>Gerador de Key | Guilherme 👑</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #111;
      color: white;
      text-align: center;
      margin-top: 100px;
    }
    .key-box {
      background-color: #222;
      padding: 20px 40px;
      border-radius: 10px;
      display: inline-block;
      font-size: 28px;
      letter-spacing: 3px;
      font-weight: bold;
      user-select: all; /* Permite copiar facilmente */
      cursor: pointer;
      transition: background-color 0.3s;
    }
    .key-box:hover {
      background-color: #444;
    }
  </style>
</head>
<body>
  <h1>🔐 Key Atual (válida por 12 horas)</h1>
  <div class="key-box" id="keyAtual" title="Clique para copiar">Carregando...</div>
  
  <script>
    function gerarKey() {
      const now = Math.floor(Date.now() / 1000);
      const base = Math.floor(now / (60 * 60 * 12));
      const hash = String(base).split('').reverse().join('').substring(0, 6);
      return "gui" + hash;
    }

    const keyElement = document.getElementById("keyAtual");
    const key = gerarKey();
    keyElement.textContent = key;

    // Copiar key ao clicar na caixa
    keyElement.addEventListener("click", () => {
      navigator.clipboard.writeText(key).then(() => {
        keyElement.textContent = "Copiado! ✔️";
        setTimeout(() => { keyElement.textContent = key; }, 2000);
      }).catch(() => {
        alert("Falha ao copiar a key");
      });
    });
  </script>
</body>
</html>
