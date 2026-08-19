# Asistente-virtual-danchy-pc-solution
asistente virtual danchy pc solution
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Danchy PC Solution - Asistente Virtual</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f4f8;
      margin: 0;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      height: 100vh;
      padding: 20px;
    }
    #app {
      background: white;
      width: 400px;
      border-radius: 8px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.15);
      display: flex;
      flex-direction: column;
      height: 600px;
    }
    header {
      background: #004aad;
      color: white;
      padding: 20px;
      font-size: 1.5em;
      font-weight: bold;
      text-align: center;
      border-radius: 8px 8px 0 0;
    }
    #chat {
      flex: 1;
      padding: 15px;
      overflow-y: auto;
      border-bottom: 1px solid #ddd;
    }
    .message {
      margin: 10px 0;
      padding: 10px;
      border-radius: 12px;
      max-width: 75%;
      clear: both;
    }
    .client {
      background: #dff3ff;
      float: right;
      text-align: right;
    }
    .bot {
      background: #e2e2e2;
      float: left;
      text-align: left;
    }
    #inputArea {
      display: flex;
      padding: 10px;
      background: #eee;
      border-radius: 0 0 8px 8px;
    }
    #inputMessage {
      flex: 1;
      padding: 10px;
      border-radius: 20px;
      border: 1px solid #ccc;
      font-size: 1em;
    }
    #sendButton {
      background: #004aad;
      border: none;
      color: white;
      margin-left: 10px;
      border-radius: 20px;
      padding: 0 20px;
      font-size: 1em;
      cursor: pointer;
    }
    #sendButton:hover {
      background: #003589;
    }
    #whatsappBtn {
      display: block;
      margin: 15px auto;
      padding: 12px 20px;
      background: #25D366;
      color: white;
      font-weight: bold;
      border-radius: 25px;
      text-align: center;
      text-decoration: none;
      width: 90%;
      font-size: 1.1em;
      box-shadow: 0 3px 8px rgba(0, 0, 0, 0.15);
    }
    #whatsappBtn:hover {
      background: #1ebe5d;
    }
  </style>
</head>
<body>
  <div id="app">
    <header>Danchy PC Solution - Asistente Virtual</header>
    <div id="chat">
      <div class="message bot">Hola 👋, soy el asistente virtual de Danchy PC Solution. ¿En qué puedo ayudarte?</div>
    </div>
    <div id="inputArea">
      <input type="text" id="inputMessage" placeholder="Escribe tu pregunta..." autocomplete="off" />
      <button id="sendButton">Enviar</button>
    </div>
    <a id="whatsappBtn" href="https://wa.me/8494580065" target="_blank" rel="noopener">Contactar por WhatsApp</a>
  </div>

  <script>
    const chat = document.getElementById('chat');
    const inputMessage = document.getElementById('inputMessage');
    const sendButton = document.getElementById('sendButton');

    function addMessage(text, sender) {
      const message = document.createElement('div');
      message.className = 'message ' + sender;
      message.textContent = text;
      chat.appendChild(message);
      chat.scrollTop = chat.scrollHeight;
    }

    function getBotResponse(text) {
      const msg = text.toLowerCase();

      if (msg.includes('hola') || msg.includes('buenas')) {
        return '¡Hola! ¿Qué tipo de producto o servicio necesitas?';
      }
      if (msg.includes('laptop')) {
        return 'Para laptops tenemos modelos desde RD$20,000 hasta RD$70,000. ¿Quieres ver nuestro catálogo?';
      }
      if (msg.includes('catálogo')) {
        return 'Claro, puedes ver nuestro catálogo completo en nuestra página oficial o te puedo ayudar con detalles.';
      }
      if (msg.includes('precio')) {
        return 'Los precios varían según el modelo. ¿Qué características buscas?';
      }
      if (msg.includes('cotización')) {
        return 'Para solicitar una cotización, por favor indícame el producto y tus datos de contacto.';
      }
      if (msg.includes('gracias') || msg.includes('ok')) {
        return 'Con gusto. Si necesitas más ayuda, aquí estaré.';
      }
      return 'Disculpa, no entendí tu pregunta. ¿Puedes intentarlo con otras palabras o contactarme por WhatsApp?';
    }

    function sendMessage() {
      const text = inputMessage.value.trim();
      if (!text) return;
      addMessage(text, 'client');
      inputMessage.value = '';
      setTimeout(() => {
        const response = getBotResponse(text);
        addMessage(response, 'bot');
      }, 700);
    }

    sendButton.addEventListener('click', sendMessage);
    inputMessage.addEventListener('keypress', (e) => {
      if (e.key === 'Enter') {
        sendMessage();
      }
    });
  </script>
</body>
</html>
