```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Nazarick#4:20</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: Arial, Helvetica, sans-serif;
    }

    body {
      background: #000;
      color: #fff;
      height: 100vh;
      overflow: hidden;
    }

    /* =========================
       SERVIDORES
    ========================= */

    .servers {
      position: fixed;
      left: 0;
      top: 0;

      width: 72px;
      height: 100vh;

      background: #050505;
      border-right: 1px solid #1d1d1d;

      display: flex;
      flex-direction: column;
      align-items: center;

      padding-top: 12px;
      gap: 12px;
    }

    .server {
      width: 50px;
      height: 50px;

      border-radius: 15px;

      background: #151515;
      color: #fff;

      display: flex;
      align-items: center;
      justify-content: center;

      font-weight: bold;
      font-size: 18px;

      cursor: pointer;

      transition: .2s;
    }

    .server:hover {
      background: #fff;
      color: #000;
      border-radius: 10px;
    }

    .server.active {
      background: #fff;
      color: #000;
      border-radius: 10px;
    }

    .add {
      font-size: 26px;
      color: #aaa;
    }


    /* =========================
       SIDEBAR
    ========================= */

    .sidebar {
      position: fixed;

      left: 72px;
      top: 0;

      width: 245px;
      height: 100vh;

      background: #0c0c0c;

      border-right: 1px solid #1d1d1d;
    }

    .server-name {
      height: 58px;

      display: flex;
      align-items: center

      padding: 0 18px;

      font-size: 15px;
      font-weight: bold;

      border-bottom: 1px solid #1d1d1d;

      letter-spacing: .3px;
    }

    .category {
      color: #777;

      font-size: 11px;
      font-weight: bold;

      padding: 20px 15px 8px;

      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .channel {
      margin: 3px 8px;

      padding: 10px 14px;

      border-radius: 5px;

      color: #929292;

      cursor: pointer;

      transition: .2s;
    }

    .channel:hover {
      background: #1c1c1c;
      color: #fff;
    }

    .channel.active {
      background: #fff;
      color: #000;
    }


    /* =========================
       USUÁRIO
    ========================= */

    .user-box {
      position: absolute;

      bottom: 0;
      left: 0;

      width: 100%;
      height: 64px;

      background: #070707;

      border-top: 1px solid #1d1d1d;

      display: flex;
      align-items: center;

      padding: 8px 10px;
    }

    .avatar {
      width: 40px;
      height: 40px;

      background: #fff;
      color: #000;

      border-radius: 50%;

      display: flex;
      align-items: center;
      justify-content: center;

      font-weight: bold;

      margin-right: 10px;
    }

    .user-info {
      font-size: 13px;
    }

    .online {
      color: #aaa;
      font-size: 11px;
      margin-top: 2px;
    }


    /* =========================
       CHAT
    ========================= */

    .chat {
      margin-left: 317px;
      margin-right: 220px;

      height: 100vh;

      display: flex;
      flex-direction: column;

      background: #090909;
    }

    .chat-header {
      height: 58px;

      display: flex;
      align-items: center;

      padding: 0 20px;

      border-bottom: 1px solid #1d1d1d;

      font-weight: bold;
    }

    .chat-header span {
      color: #777;
      font-size: 20px;
      margin-right: 8px;
    }


    /* =========================
       MENSAGENS
    ========================= */

    .messages {
      flex: 1;

      padding: 22px;

      overflow-y: auto;
    }

    .message {
      display: flex;

      gap: 12px;

      margin-bottom: 22px;
    }

    .message-avatar {
      width: 42px;
      height: 42px;

      min-width: 42px;

      border-radius: 50%;

      background: #fff;
      color: #000;

      display: flex;
      align-items: center;
      justify-content: center;

      font-weight: bold;
    }

    .message-content {
      max-width: 80%;
    }

    .message-name {
      font-weight: bold;
      margin-bottom: 4px;
    }

    .message-time {
      color: #666;
      font-size: 10px;
      font-weight: normal;
      margin-left: 5px;
    }

    .message-text {
      color: #cfcfcf;
      line-height: 1.5;
      word-break: break-word;
    }


    /* =========================
       INPUT
    ========================= */

    .message-input {
      margin: 10px 20px 20px;

      background: #171717;

      border: 1px solid #242424;

      border-radius: 8px;

      display: flex;
      align-items: center;

      padding: 5px 8px;
    }

    .message-input input {
      flex: 1;

      background: transparent;

      border: none;
      outline: none;

      color: #fff;

      padding: 12px;

      font-size: 14px;
    }

    .message-input input::placeholder {
      color: #666;
    }

    .message-input button {
      background: #fff;
      color: #000;

      border: none;

      border-radius: 5px;

      padding: 9px 15px;

      font-weight: bold;

      cursor: pointer;

      transition: .2s;
    }

    .message-input button:hover {
      background: #ccc;
    }


    /* =========================
       MEMBROS
    ========================= */

    .members {
      position: fixed;

      right: 0;
      top: 0;

      width: 220px;
      height: 100vh;

      background: #0c0c0c;

      border-left: 1px solid #1d1d1d;

      padding: 20px 12px;
    }

    .members-title {
      color: #777;

      font-size: 11px;

      font-weight: bold;

      margin-bottom: 15px;

      letter-spacing: 1px;
    }

    .member {
      display: flex;
      align-items: center;

      padding: 8px;

      color: #bbb;

      border-radius: 5px;
    }

    .member:hover {
      background: #1b1b1b;
      color: #fff;
    }

    .member-avatar {
      width: 34px;
      height: 34px;

      border-radius: 50%;

      background: #fff;
      color: #000;

      display: flex;
      align-items: center;
      justify-content: center;

      margin-right: 10px;

      font-size: 13px;
      font-weight: bold;
    }


    /* =========================
       SCROLLBAR
    ========================= */

    ::-webkit-scrollbar {
      width: 6px;
    }

    ::-webkit-scrollbar-track {
      background: #080808;
    }

    ::-webkit-scrollbar-thumb {
      background: #333;
      border-radius: 10px;
    }

    ::-webkit-scrollbar-thumb:hover {
      background: #555;
    }


    /* =========================
       MOBILE
    ========================= */

    @media (max-width: 900px) {

      .members {
        display: none;
      }

      .chat {
        margin-right: 0;
      }
    }


    @media (max-width: 650px) {

      .servers {
        display: none;
      }

      .sidebar {
        display: none;
      }

      .chat {
        margin-left: 0;
      }

      .chat-header {
        height: 55px;
      }

      .messages {
        padding: 14px;
      }

      .message-input {
        margin: 8px;
      }
    }
  </style>
</head>

<body>


  <!-- =========================
       SERVIDORES
  ========================= -->

  <aside class="servers">

    <div class="server active">N</div>

    <div class="server">🎮</div>

    <div class="server">🎵</div>

    <div class="server">⚽</div>

    <div class="server">🔥</div>

    <div class="server add">+</div>

  </aside>


  <!-- =========================
       MENU
  ========================= -->

  <aside class="sidebar">

    <div class="server-name">
      ◈ Nazarick#4:20
    </div>


    <div class="category">
      Canais de texto
    </div>

    <div class="channel active">
      # geral
    </div>

    <div class="channel">
      # conversa
    </div>

    <div class="channel">
      # amizades
    </div>

    <div class="channel">
      # games
    </div>

    <div class="channel">
      # música
    </div>


    <div class="category">
      Comunidades
    </div>

    <div class="channel">
      # brasil
    </div>

    <div class="channel">
      # são-paulo
    </div>

    <div class="channel">
      # rio-de-janeiro
    </div>

    <div class="channel">
      # minas-gerais
    </div>


    <!-- USUÁRIO -->

    <div class="user-box">

      <div class="avatar">
        N
      </div>

      <div class="user-info">

        <strong>Nazarick</strong>

        <div class="online">
          ● Online
        </div>

      </div>

    </div>

  </aside>


  <!-- =========================
       CHAT
  ========================= -->

  <main class="chat">

    <header class="chat-header">

      <span>#</span>

      <div id="channelTitle">
        geral
      </div>

    </header>


    <section class="messages" id="messages">


      <div class="message">

        <div class="message-avatar">
          N
        </div>

        <div class="message-content">

          <div class="message-name">

            Nazarick

            <span class="message-time">
              Hoje às 04:20
            </span>

          </div>

          <div class="message-text">
            Bem-vindo ao Nazarick#4:20 🖤
          </div>

        </div>

      </div>


      <div class="message">

        <div class="message-avatar">
          B
        </div>

        <div class="message-content">

          <div class="message-name">

            Bot

            <span class="message-time">
              Hoje às 04:20
            </span>

          </div>

          <div class="message-text">
            Este é o começo da sua comunidade.
          </div>

        </div>

      </div>


    </section>


    <!-- INPUT -->

    <div class="message-input">

      <input
        type="text"
        id="messageInput"
        placeholder="Conversar em #geral"
        autocomplete="off"
      >

      <button onclick="sendMessage()">
        Enviar
      </button>

    </div>

  </main>


  <!-- =========================
       MEMBROS
  ========================= -->

  <aside class="members">

    <div class="members-title">
      ONLINE — 4
    </div>


    <div class="member">

      <div class="member-avatar">
        N
      </div>

      Nazarick

    </div>


    <div class="member">

      <div class="member-avatar">
        J
      </div>

      João

    </div>


    <div class="member">

      <div class="member-avatar">
        M
      </div>

      Maria

    </div>


    <div class="member">

      <div class="member-avatar">
        R
      </div>

      Rafael

    </div>

  </aside>


  <script>

    const input =
      document.getElementById("messageInput");

    const messages =
      document.getElementById("messages");


    /* =========================
       ENVIAR MENSAGEM
    ========================= */

    function sendMessage() {

      const text = input.value.trim();

      if (!text) return;


      const message =
        document.createElement("div");

      message.className = "message";


      message.innerHTML = `

        <div class="message-avatar">
          N
        </div>

        <div class="message-content">

          <div class="message-name">

            Nazarick

            <span class="message-time">
              Agora
            </span>

          </div>

          <div class="message-text">
            ${escapeHTML(text)}
          </div>

        </div>

      `;


      messages.appendChild(message);

      input.value = "";

      messages.scrollTop =
        messages.scrollHeight;
    }


    /* ENTER ENVIA */

    input.addEventListener(
      "keydown",
      function(event) {

        if (event.key === "Enter") {
          sendMessage();
        }

      }
    );


    /* SEGURANÇA CONTRA HTML */

    function escapeHTML(text) {

      const div =
        document.createElement("div");

      div.textContent = text;

      return div.innerHTML;
    }


    /* =========================
       TROCAR CANAL
    ========================= */

    document
      .querySelectorAll(".channel")
      .forEach(channel => {

        channel.addEventListener(
          "click",
          function() {

            document
              .querySelectorAll(".channel")
              .forEach(c =>
                c.classList.remove("active")
              );


            this.classList.add("active");


            const name =
              this.textContent
                .trim()
                .replace("#", "");


            document
              .getElementById("channelTitle")
              .textContent = name;


            input.placeholder =
              "Conversar em #" + name;

          }
        );

      });


    /* =========================
       TROCAR SERVIDOR
    ========================= */

    document
      .querySelectorAll(".server")
      .forEach(server => {

        server.addEventListener(
          "click",
          function() {

            document
              .querySelectorAll(".server")
              .forEach(s =>
                s.classList.remove("active")
              );


            this.classList.add("active");

          }
        );

      });

  </script>

</body>
</html>
```
