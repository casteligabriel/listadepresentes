# listadepresentes

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Chá de Casamento - Presentes</title>
  <script src="https://cdn.jsdelivr.net/npm/qrcode/build/qrcode.min.js"></script>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    .item { margin-bottom: 20px; }
    .qrcode { margin-top: 20px; }
  </style>
</head>
<body>
  <h1>Chá de Casamento 💍</h1>
  <p>Escolha um presente para contribuir com nosso novo lar!</p>

  <div class="item">
    <strong>Conjunto de Panelas - R$ 150,00</strong><br />
    <button onclick="gerarPix(150, 'Conjunto de Panelas')">Presentear</button>
  </div>

  <div class="item">
    <strong>Jogo de Cama - R$ 120,00</strong><br />
    <button onclick="gerarPix(120, 'Jogo de Cama')">Presentear</button>
  </div>

  <div class="item">
    <strong>Liquidificador - R$ 90,00</strong><br />
    <button onclick="gerarPix(90, 'Liquidificador')">Presentear</button>
  </div>

  <div class="qrcode" id="qrcode"></div>

  <script>
    const chavePix = "seu-email@exemplo.com"; // coloque sua chave PIX aqui
    const nomeRecebedor = "Nome Completo";
    const cidade = "SaoPaulo"; // sem acentos ou espaços

    function gerarPix(valor, descricao) {
      const payload = `00020126360014BR.GOV.BCB.PIX0114${chavePix}520400005303986540${valor.toFixed(2).replace('.', '')}5802BR5913${nomeRecebedor}6009${cidade}62100506${descricao}6304`;
      // A linha acima gera uma base para o QR, mas para QR Pix válido, recomendo usar uma API Pix Copia e Cola

      const urlPix = `pix:/${payload}`;
      document.getElementById("qrcode").innerHTML = "";
      QRCode.toCanvas(document.getElementById("qrcode"), payload, { width: 300 }, function (error) {
        if (error) console.error(error);
        console.log("QR Code gerado!");
      });
    }
  </script>
</body>
</html>
