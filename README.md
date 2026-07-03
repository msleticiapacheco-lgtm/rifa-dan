# rifa-dan
<!DOCTYPE html>
<html>
<head>
  <title>Raffle 1–100</title>
  <style>
    body { font-family: Arial; text-align: center; background: #f5f5f5; }
    h1 { margin-top: 20px; }

    #grid {
      display: grid;
      grid-template-columns: repeat(10, 1fr);
      gap: 5px;
      max-width: 500px;
      margin: 20px auto;
    }

    .num {
      padding: 10px;
      background: #4CAF50;
      color: white;
      cursor: pointer;
      border-radius: 5px;
    }

    .reserved { background: orange; }
    .paid { background: red; }

    #box {
      display: none;
      background: white;
      padding: 15px;
      border-radius: 10px;
      width: 300px;
      margin: auto;
      box-shadow: 0 0 10px rgba(0,0,0,0.2);
    }

    input { width: 90%; padding: 8px; margin: 5px 0; }

    button { padding: 10px; cursor: pointer; }
  </style>
</head>

<body>

<h1>🎟 Raffle Numbers (1–100)</h1>

<div id="grid"></div>

<div id="box">
  <h3 id="selected"></h3>
  <input id="name" placeholder="Your name">
  <button onclick="reserve()">Reserve</button>

  <div id="payment" style="display:none;">
    <p>Send payment to:</p>
    <p><b>Venmo:</b> @yourvenmo</p>
    <p><b>Cash App:</b> $yourcashapp</p>
    <p><b>Zelle:</b> your-email@email.com</p>
    <p>After paying, your number will be confirmed.</p>
  </div>
</div>

<script>
let selectedNum = null;
let data = {};

const grid = document.getElementById("grid");

for (let i = 1; i <= 100; i++) {
  let div = document.createElement("div");
  div.innerText = i;
  div.className = "num";
  div.onclick = () => openBox(i, div);
  grid.appendChild(div);
}

function openBox(num, el) {
  if (el.classList.contains("paid")) return;

  selectedNum = el;
  document.getElementById("selected").innerText = "Number " + num;
  document.getElementById("box").style.display = "block";
}

function reserve() {
  let name = document.getElementById("name").value;
  if (!name) return alert("Enter your name");

  selectedNum.classList.add("reserved");
  document.getElementById("payment").style.display = "block";
}
</script>

</body>
</html>