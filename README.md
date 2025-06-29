<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <title>BLACKNET // СИСТЕМА ВЗЛОМА</title>
  <style>
    html, body {
      margin: 0;
      padding: 0;
      background-color: #000;
      color: #fff;
      font-family: "Courier New", monospace;
      height: 100%;
    }

    .title {
      text-align: center;
      font-size: 22px;
      margin-top: 20px;
      text-shadow: 0 0 10px #ff0000;
    }

    .menu {
      border: 1px solid #fff;
      padding: 15px;
      max-width: 700px;
      margin: 20px auto;
      background-color: #111;
    }

    .option {
      margin: 10px 0;
      cursor: pointer;
      padding: 6px;
      transition: background 0.2s;
    }

    .option:hover {
      background-color: #222;
    }

    #console {
      margin: 20px auto;
      padding: 15px;
      background-color: #000;
      border: 1px solid #333;
      max-width: 700px;
      min-height: 250px;
      max-height: 300px;
      overflow-y: auto;
      white-space: pre-wrap;
      color: #ccc;
      transition: all 0.5s;
    }

    #console.fullscreen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      max-height: 100%;
      z-index: 9999;
      font-size: 14px;
      padding: 20px;
      box-sizing: border-box;
    }

    .footer {
      text-align: center;
      font-size: 12px;
      margin-top: 30px;
      color: #777;
    }
  </style>
</head>
<body>

<div class="title">⛧ BLACKNET // СИСТЕМА ВЗЛОМА ⛧</div>

<div class="menu">
  <div class="option" onclick="startInfiniteDDoS()">[01] DDoS-Атака</div>
  <div class="option" onclick="runFake('Сканер портов', 'target.net')">[02] Сканер портов</div>
  <div class="option" onclick="runFake('MAC-спуфинг', 'eth0')">[03] MAC-спуфинг</div>
  <div class="option" onclick="runFake('SQL-инъекция', 'admin.php')">[04] SQL-инъекция</div>
  <div class="option" onclick="runFake('OSINT сбор', 'vk.com/profile')">[05] OSINT-профиль</div>
  <div class="option" onclick="runFake('Удалённый эксплойт', '192.168.1.55')">[06] Эксплойт сервера</div>
</div>

<div id="console">
> BLACKNET загружен. Ожидание ввода команды...
</div>

<div class="footer">
root@blacknet | режим: обман | версия: 2.1
</div>

<script>
  let ddosInterval = null;

  function runFake(modul, target) {
    const c = document.getElementById("console");
    c.classList.remove("fullscreen");
    c.innerText = `> Модуль: ${modul}\n> Цель: ${target}\nИнициализация...\nПодключение...\nЗапуск...\n`;
    c.scrollTop = c.scrollHeight;

    setTimeout(() => {
      c.innerText += "\n[⛧ ОШИБКА] Эта функция — фальшивая.\n>> Ты был троллен.";
      c.scrollTop = c.scrollHeight;
    }, 3000);
  }

  function startInfiniteDDoS() {
    const target = prompt("Введите IP-адрес цели для DDoS:");
    const c = document.getElementById("console");

    if (!target || target.trim() === "") {
      c.classList.remove("fullscreen");
      c.innerText = "> [ОШИБКА] IP-адрес не указан.";
      return;
    }

    c.innerText = `> Модуль: DDoS-Атака\n> Цель: ${target}\n\n[ НАЧАЛО АТАКИ ]\n`;
    c.classList.add("fullscreen");

    if (ddosInterval) clearInterval(ddosInterval);
    let count = 1;

    ddosInterval = setInterval(() => {
      const order = Math.random() > 0.5;
      const packetLine = `➤ Пакет отправлен к ${target}... [${count}]`;
      const responseLine = `⇋ Ответ: 500 Internal Server Error`;

      const output = order
        ? `${packetLine}\n${responseLine}`
        : `${responseLine}\n${packetLine}`;

      c.innerText += output + "\n\n";
      c.scrollTop = c.scrollHeight;
      count++;
    }, 35);
  }
</script>

</body>
</html>
