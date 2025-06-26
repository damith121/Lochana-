from zipfile import ZipFile
import os

# HTML, CSS & JS code based on user's logic
html_code = """
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Lochana's 15th Birthday</title>
  <style>
    body {
      background: linear-gradient(to top right, #ffe0ec, #ffe6ff);
      font-family: 'Segoe UI', sans-serif;
      text-align: center;
      padding: 40px;
      color: #333;
    }
    .box {
      max-width: 500px;
      background: white;
      margin: auto;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 20px rgba(0,0,0,0.1);
      display: none;
    }
    .active {
      display: block;
    }
    h1 {
      font-size: 2em;
      color: #ff3399;
    }
    button {
      margin: 10px;
      padding: 12px 20px;
      font-size: 16px;
      border: none;
      border-radius: 8px;
      background-color: #ff66a3;
      color: white;
      cursor: pointer;
    }
    .cake {
      font-size: 4em;
      margin-top: 20px;
      animation: float 1s infinite alternate;
    }
    @keyframes float {
      from { transform: translateY(0); }
      to { transform: translateY(-10px); }
    }
    .balloons {
      font-size: 2em;
      animation: float 1.5s infinite alternate;
    }
    .hardbox {
      display: none;
      background-color: #ffd6e7;
      padding: 15px;
      margin-top: 20px;
      border-radius: 10px;
      font-size: 1.2em;
    }
  </style>
</head>
<body>

  <div id="q1" class="box active">
    <h1>ඔයාගෙ නම ලෝචනා නේද?</h1>
    <button onclick="yesName()">Yes</button>
    <button onclick="noName()">No</button>
  </div>

  <div id="q2" class="box">
    <h1>ඔයාගෙ 🍑 සුදුද?</h1>
    <button onclick="q3()">නැ කලුයි</button>
    <button onclick="q3()">ඇයි අහන්නෙ</button>
  </div>

  <div id="q1b" class="box">
    <h1>ඒනම් ඔයා චමෝදි නේද?</h1>
    <button onclick="q2()">Yes</button>
  </div>

  <div id="q3" class="box">
    <h1>ඔයා boyfriend කොච්චරක් ආදරෙයිද?</h1>
    <button onclick="birthday()">ඔව්ව්ව්</button>
    <button onclick="birthday()">ගොඩක් ආදරෙයි</button>
    <button onclick="birthday()">පනටත් වැඩිය ආදරෙයි</button>
  </div>

  <div id="final" class="box">
    <div class="balloons">🎈🎉🎈</div>
    <div class="cake">🎂</div>
    <h1>Happy Birthday Mage Manikah! 💖</h1>
    <p>ඔයාට සුන්දරම 15වෙනි උපන්දිනයක් වේවා!</p>
    <button onclick="showHard()">touch</button>
  </div>

  <div id="hard" class="hardbox">
    ummmmah 😍
  </div>

<script>
  function showBox(id) {
    document.querySelectorAll('.box').forEach(el => el.classList.remove('active'));
    document.getElementById(id).classList.add('active');
  }
  function yesName() {
    showBox('q2');
  }
  function noName() {
    showBox('q1b');
  }
  function q2() {
    showBox('q2');
  }
  function q3() {
    showBox('q3');
  }
  function birthday() {
    showBox('final');
  }
  function showHard() {
    document.getElementById('hard').style.display = 'block';
  }
</script>

</body>
</html>
"""

# Save the HTML to a file
os.makedirs("/mnt/data/lochana_birthday_page", exist_ok=True)
file_path = "/mnt/data/lochana_birthday_page/index.html"
with open(file_path, "w", encoding="utf-8") as f:
    f.write(html_code)

# Zip the folder
zip_path = "/mnt/data/Lochana_Interactive_Birthday_Page.zip"
with ZipFile(zip_path, 'w') as zipf:
    zipf.write(file_path, arcname="index.html")

zip_path  # Return path to zip file for download

