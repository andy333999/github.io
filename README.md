
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>祕境占卜骰</title>
  <style>
    body {
      font-family: "Noto Serif TC", serif;
      background-color: #f9f6f1;
      color: #2e2e2e;
      text-align: center;
      padding: 1rem;
    }
    h1 {
      font-size: 1.8rem;
      margin-bottom: 0.5rem;
    }
    p {
      font-size: 1rem;
      color: #666;
      margin-bottom: 1rem;
    }
    button {
      padding: 0.5rem 1rem;
      font-size: 1rem;
      margin: 0.3rem;
      background-color: #8c7b6d;
      color: white;
      border: none;
      border-radius: 6px;
      cursor: pointer;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(7, 1fr);
      gap: 0.4rem;
      max-width: 420px;
      margin: 1rem auto;
    }
    .cell {
      background: #e6e1d3;
      padding: 0.6rem 0;
      font-size: 1.3rem;
      border-radius: 4px;
    }
    textarea {
      margin-top: 1rem;
      width: 90%;
      max-width: 420px;
      height: 120px;
      font-size: 1rem;
      padding: 0.6rem;
      border-radius: 6px;
      border: 1px solid #ccc;
    }
  </style>
</head>
<body>
  <h1>祕境占卜骰</h1>
  <p>擲下神祕的四面骰，組合出一篇屬於你的祈福詩文。從其中解讀今日的宇宙訊息與內心啟示。</p>

  <button onclick="generateDice()">🎲 擲骰產生祈福文</button>
  <button onclick="saveReading()">💾 儲存占卜結果</button>

  <div class="grid" id="diceGrid"></div>

  <textarea id="savedText" placeholder="這裡會顯示你儲存的祈福文..." readonly></textarea>

  <script>
    const diceFaces = [
      ['玄','秘','幽','微'],['空','宙','穹','虛'],['流','逝','遁','渺'],['影','薄','幽','霧'],['啟','開','引','解'],['奇','異','妙','特'],['機','運','謎','結'],
      ['幽','禪','寂','清'],['雲','霧','霄','星'],['濛','朦','迷','霧'],['霧','嵐','薄','纏'],['覆','隱','蔽','守'],['秘','隱','藏','密'],['境','國','域','邊'],
      ['星','辰','宙','凝'],['河','洋','流','潺'],['渺','微','瀰','少'],['渺','瀰','細','寥'],['寄','傳','陳','撫'],['微','細','雅','纖'],['光','輝','耀','煌'],
      ['秘','玄','深','隱'],['法','律','道','規'],['流','轉','運','走'],['轉','迴','輪','彎'],['問','察','探','求'],['天','宙','昊','風'],['機','謎','緣','舞'],
      ['幻','虛','妙','渺'],['夢','迷','幻','宛'],['潛','深','沉','隱'],['隱','藏','密','窺'],['蘊','滋','聚','蕴'],['神','靈','仙','妙'],['韻','意','語','氣'],
      ['靜','寂','清','寧'],['悟','覺','解','通'],['虛','空','寂','無'],['實','真','純','然'],['合','融','匯','聚'],['玄','深','邃','微'],['軌','道','線','徑'],
      ['濤','波','浩','漣'],['聲','音','响','歌'],['回','返','復','迴'],['盪','擺','漾','搖'],['啟','開','引','觸'],['微','細','暖','輕'],['真','實','確','然']
    ];

    function generateDice() {
      const grid = document.getElementById('diceGrid');
      grid.innerHTML = '';
      window.currentWords = [];

      for (let i = 0; i < 49; i++) {
        const randChar = diceFaces[i][Math.floor(Math.random() * 4)];
        const cell = document.createElement('div');
        cell.className = 'cell';
        cell.textContent = randChar;
        grid.appendChild(cell);
        window.currentWords.push(randChar);
      }
    }

    function saveReading() {
      if (!window.currentWords || window.currentWords.length !== 49) {
        alert('請先擲骰再儲存占卜結果。');
        return;
      }
      const formatted = window.currentWords.map((ch, idx) => ((idx % 7 === 6) ? ch + '\n' : ch)).join('');
      document.getElementById('savedText').value = formatted;
    }
  </script>
</body>
</html>
