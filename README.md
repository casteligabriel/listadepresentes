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
      display: flex;
      align-items: center;
      gap: 15px;
    }
    .item img {
      width: 100px;
      height: auto;
      border-radius: 8px;
      object-fit: cover;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    .item-info {
      flex-grow: 1;
    }
    button {
      padding: 8px 12px;
      border: none;
      background-color: #b85c5c;
      color: white;
      border-radius: 8px;
      cursor: pointer;
      flex-shrink: 0;
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
    <img src="https://images.unsplash.com/photo-1522337660859-02fbefca4702?auto=format&fit=crop&w=100&q=80" alt="Corte de cabelo"/>
    <div class="item-info">
      <strong>Corte de cabelo para o noivo – R$ 50,00</strong>
    </div>
    <button onclick="gerarPix(50, 'Corte de cabelo para o noivo')">Presentear</button>
  </div>

  <div class="item">
    <img src="https://images.unsplash.com/photo-1587300003388-59208cc962cb?auto=format&fit=crop&w=100&q=80" alt="Coberta"/>
    <div class="item-info">
      <strong>Coberta para a noiva sempre estar coberta de razão – R$ 150,00</strong>
    </div>
    <button onclick="gerarPix(150, 'Coberta da razão da noiva')">Presentear</button>
  </div>

  <div class="item">
    <img src="https://images.unsplash.com/photo-1509395062183-67c5ad6faff9?auto=format&fit=crop&w=100&q=80" alt="Churrasqueira"/>
    <div class="item-info">
      <strong>Churrasqueira para o japa pilotar – R$ 200,00</strong>
    </div>
    <button onclick="gerarPix(200, 'Churrasqueira para o japa')">Presentear</button>
  </div>

  <div class="qrcode" id="qrcode"></div>

  <script>
    const chavePix = "19994445973";
    const nomeRecebedor = "Gabriel Casteli Fontes";
    const cidade = "MogiGuacu";

    function gerarPix(valor, descricao) {
      const pixPayload = `00020126360014BR.GOV.BCB.PIX0114${chavePix}520400005303986540${(valor*100).toFixed(0)}5802BR5913${nomeRecebedor}6009${cidade}62100506${descricao}6304`;

      const qrcodeArea = document.getElementById("qrcode");
      qrcodeArea.innerHTML = `<h3>Escaneie o QR Code para pagar R$ ${valor.toFixed(2)}:</h3>`;

      QRCode.toCanvas(pixPayload, { width: 250 }, function (error, canvas) {
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
