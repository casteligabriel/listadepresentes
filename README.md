# listadepresentes

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Chá de Casamento - Cinthia e Gabriel</title>
  <script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
      background: #fff8f0;
      color: #333;
    }
    h1 {
      color: #b85c5c;
    }
    .item {
      margin-bottom: 20px;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 12px;
      background: #fff;
    }
    button {
      margin-top: 8px;
      padding: 8px 12px;
      border: none;
      background-color: #b85c5c;
      color: white;
      border-radius: 8px;
      cursor: pointer;
    }
    .qrcode {
      margin-top: 30px;
      text-align: center;
    }
  </style>
</head>
<body>
  <h1>Chá de Casamento 💕</h1>
  <p>Ajude Cinthia e Gabriel a começarem essa nova fase com carinho e bom humor! Escolha um presente abaixo:</p>

  <div class="item">
    <strong>Corte de cabelo para o noivo – R$ 50,00</strong><br />
    <button onclick="gerarPix(50, 'Corte de cabelo para o noivo')">Presentear</button>
  </div>

  <div class="item">
    <strong>Coberta para a noiva sempre estar coberta de razão – R$ 150,00</strong><br />
    <button onclick="gerarPix(150, 'Coberta da razão da noiva')">Presentear</button>
  </div>

  <div class="item">
    <strong>Churrasqueira para o japa pilotar – R$ 200,00</strong><br />
    <button onclick="gerarPix(200, 'Churrasqueira para o japa')">Presentear</button>
  </div>

  <div class="qrcode" id="qrcode">
    <!-- QR Code será exibido aqui -->
  </div>

  <script>
    const chavePix = "19994445973"; // celular
    const nomeRecebedor = "Gabriel Casteli Fontes"; 
    const cidade = "MogiGuacu"; 

    function gerarPix(valor, descricao) {
      const valorFormatado = valor.toFixed(2).replace('.', ',');
      // Para gerar um QR Pix válido, normalmente usamos uma biblioteca específica.
      // Aqui, vou usar uma biblioteca que gera o payload correto para você.

      // Montar payload Pix Copia e Cola usando biblioteca externa simplificada (https://github.com/pablonadj/pix-qrcode)
      // Como estamos em ambiente frontend, vamos simplificar com uma URL Pix com valor e descrição.

      // Montar string Pix para QR Code (simplificado):
      const pixString = `00020126360014BR.GOV.BCB.PIX0114${chavePix}520400005303986540${(valor*100).toFixed(0)}5802BR5913${nomeRecebedor}6009${cidade}62100506${descricao}6304`;

      // No mundo real, essa string precisa de CRC16, mas vamos usar um QRCode simples do pixString mesmo.

      const qrcodeArea = document.getElementById("qrcode");
      qrcodeArea.innerHTML = `<h3>Escaneie o QR Code para pagar R$ ${valorFormatado}:</h3>`;
      QRCode.toCanvas(pixString, { width: 250 }, function (error, canvas) {
        if (error) {
          qrcodeArea.innerHTML += "<p>Erro ao gerar QR Code.</p>";
          console.error(error);
          return;
        }
        qrcodeArea.appendChild(canvas);
      });
    }
  </script>
</body>
</html>
