<!DOCTYPE html>  
<html lang="pt-BR">  
<head>  
<meta charset="UTF-8" />  
<meta name="viewport" content="width=device-width, initial-scale=1" />  
<title>Mestre Agro - Chatbot</title>  
<style>  
  body { font-family: Arial, sans-serif; margin: 20px; background: #f4f4f4; }  
  #chatbox { width: 100%; max-width: 600px; margin: auto; background: white; padding: 20px; border-radius: 8px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }  
  #messages { height: 300px; overflow-y: auto; border: 1px solid #ddd; padding: 10px; margin-bottom: 10px; }  
  .message { margin-bottom: 10px; }  
  .user { color: blue; }  
  .bot { color: green; }  
  #inputForm { display: flex; }  
  #input { flex: 1; padding: 10px; font-size: 16px; }  
  #sendBtn { padding: 10px 20px; font-size: 16px; }  
</style>  
</head>  
<body>  
  <div id="chatbox">  
    <h2>Mestre Agro - Chatbot</h2>  
    <div id="messages"></div>  
    <form id="inputForm">  
      <input type="text" id="input" placeholder="Digite sua pergunta..." autocomplete="off" />  
      <button type="submit" id="sendBtn">Enviar</button>  
    </form>  
  </div>  
  
<script>  
  const baseConhecimento = {  
    "manutenção bomba hidráulica": "Para a manutenção da bomba hidráulica, verifique o nível de óleo regularmente, substitua os filtros conforme o manual do fabricante e inspecione as mangueiras para evitar vazamentos.",  
    "painel de instrumentos trator": "O painel de instrumentos do trator mostra informações essenciais como velocidade, temperatura do motor, nível de combustível e pressão do óleo.",  
    "funcionamento colhedora": "A colhedora funciona cortando, recolhendo e separando os grãos da planta, utilizando sistemas hidráulicos e mecânicos específicos.",  
    "problema ps sem sinal": "Se o PS está sem sinal, verifique as conexões elétricas, fusíveis e sensores relacionados. Consulte o manual para procedimentos detalhados.",  
    "quem é o dono": "A Mestre Agro foi criada e é de propriedade de Gustavo da Silva Melo.",  
    "proprietário": "A Mestre Agro foi criada e é de propriedade de Gustavo da Silva Melo.",  
    "capacidade óleo ch 570": "A capacidade de óleo do sistema hidráulico da colhedora CH 570 é de 120 litros."  
  };  
  
  const messagesDiv = document.getElementById('messages');  
  const inputForm = document.getElementById('inputForm');  
  const inputField = document.getElementById('input');  
  
  function appendMessage(text, sender) {  
    const msgDiv = document.createElement('div');  
    msgDiv.classList.add('message');  
    msgDiv.classList.add(sender);  
    msgDiv.textContent = text;  
    messagesDiv.appendChild(msgDiv);  
    messagesDiv.scrollTop = messagesDiv.scrollHeight;  
  }  
  
  function responderPergunta(pergunta) {  
    pergunta = pergunta.toLowerCase();  
    for (const chave in baseConhecimento) {  
      if (pergunta.includes(chave)) {  
        return baseConhecimento[chave];  
      }  
    }  
    return "Desculpe, não tenho essa informação no momento.";  
  }  
  
  inputForm.addEventListener('submit', function(e) {  
    e.preventDefault();  
    const pergunta = inputField.value.trim();  
    if (!pergunta) return;  
    appendMessage("Você: " + pergunta, 'user');  
    const resposta = responderPergunta(pergunta);  
    setTimeout(() => {  
      appendMessage("Mestre Agro: " + resposta, 'bot');  
    }, 500);  
    inputField.value = '';  
  });  
</script>  
</body>  
</html>  
