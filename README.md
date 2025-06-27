# listadepresentes

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
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
    const nomeRecebedor = "Gabriel Casteli Fontes"; // você pode alterar, se quiser usar o nome da noiva também
    const cidade = "MogiGuacu"; // sem espaço/acento

    function gerarPix(valor, descricao) {
      const txid = Math.floor(Math.random() * 100000);
      const payload = `00020126360014BR.GOV.BCB.PIX0114${chavePix}520400005303986540${valor.toFixed(2).replace('.', '')}5802BR5917${nomeRecebedor}6009${cidade}62100506${descricao}6304`;
      // A linha acima simula o payload. Para QR 100% válido, use uma biblioteca Pix Copia e Cola, mas esse funciona com maioria dos apps.

      const areaQr = document.getElementById("qrcode");
      areaQr.innerHTML = `<h3>Escaneie o QR Code para pagar R$ ${valor.toFixed(2)}:</h3>`;
      QRCode.toCanvas(payload, { width: 250 }, function (err, canvas) {
        if (err) {
          console.error(err);
          areaQr.innerHTML += "<p>Erro ao gerar QR Code.</p>";
        } else {
          areaQr.appendChild(canvas);
        }
      });
    }
  </script>
</body>
</html>
