<!DOCTYPE html>
<html lang="ne">
<head>
  <meta charset="UTF-8">
  <title>Security Check</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: black;
      color: white;
      text-align: center;
      padding: 30px;
    }
    .hidden { display: none; }
    .box {
      border: 2px solid #333;
      border-radius: 10px;
      padding: 20px;
      margin: 20px auto;
      width: 90%;
      max-width: 400px;
      background-color: #111;
      animation: fadeIn 1s ease-in-out;
    }
    input {
      padding: 10px;
      border: none;
      width: 80%;
      margin: 10px 0;
      border-radius: 5px;
      text-align: center;
    }
    button {
      padding: 10px 20px;
      background-color: #444;
      color: white;
      border: none;
      border-radius: 5px;
      margin-top: 10px;
      cursor: pointer;
    }
    .notification {
      background-color: #222;
      border-left: 5px solid #ff0000;
      padding: 10px;
      margin-top: 20px;
      font-size: 0.9rem;
      color: #ff8080;
    }
    .danger {
      color: red;
      font-weight: bold;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }
  </style>
</head>
<body>

<audio id="beepSound">
  <source src="https://www.soundjay.com/button/beep-07.wav" type="audio/wav">
</audio>
<audio id="notifySound">
  <source src="https://www.soundjay.com/button/beep-10.wav" type="audio/wav">
</audio>

<div class="box" id="login">
  <h2>मोबाइल नम्बरबाट लगइन गर्नुहोस्</h2>
  <input type="text" id="mobile" placeholder="९८XXXXXXXX"><br>
  <button onclick="showLoading()">लगइन गर्नुहोस्</button>
</div>

<div class="box hidden" id="loading">
  <h3>लोड हुँदैछ...</h3>
  <p>कृपया केही समय पर्खनुहोस्</p>
</div>

<div class="box hidden" id="nameInput">
  <h2>तपाईंको नाम लेख्नुहोस्</h2>
  <input type="text" id="username" placeholder="तपाईंको नाम"><br>
  <button onclick="showWelcome()">जारी राख्नुहोस्</button>
</div>

<div class="box hidden" id="welcome">
  <h2>स्वागत छ, <span id="personName"></span></h2>
  <p>sanoj?scnh</p>
  <button onclick="showScam()">जारी राख्नुहोस्</button>
</div>

<div class="box hidden" id="scam">
  <h3>🔐 प्रणालीमा अनधिकृत पहुँच</h3>
  <p class="danger">तपाईंको सिममा भएको सम्पूर्ण रकम हराएको छ!</p>
  <div class="notification">
    📩 1415 बाट: You have only Rs. 0.00. Please recharge!
  </div>
  <button onclick="showWarning()">ब्याकअप</button>
</div>

<div class="box hidden" id="warning">
  <h3>‼️ चेतावनी</h3>
  <p>यस्ता फ्रड वेबसाइटहरूबाट सतर्क रहनुहोस्। धन्यवाद 🙏</p>
  <button onclick="final()">जारी राख्नुहोस्</button>
</div>

<div class="box hidden" id="final">
  <h1>🤡</h1>
  <p>यो केवल रमाइलोको लागि हो — तपाईंको पैसा सुरक्षित छ।</p>
</div>

<script>
  function playBeep() {
    document.getElementById("beepSound").play();
  }

  function playNotify() {
    document.getElementById("notifySound").play();
  }

  function showLoading() {
    document.getElementById("login").classList.add("hidden");
    document.getElementById("loading").classList.remove("hidden");
    setTimeout(() => {
      document.getElementById("loading").classList.add("hidden");
      document.getElementById("nameInput").classList.remove("hidden");
    }, 4000);
  }

  function showWelcome() {
    let name = document.getElementById("username").value;
    document.getElementById("personName").innerText = name;
    document.getElementById("nameInput").classList.add("hidden");
    document.getElementById("welcome").classList.remove("hidden");
  }

  function showScam() {
    document.getElementById("welcome").classList.add("hidden");
    document.getElementById("scam").classList.remove("hidden");
    playBeep();
    setTimeout(() => {
      playNotify();
    }, 1000);
  }

  function showWarning() {
    document.getElementById("scam").classList.add("hidden");
    document.getElementById("warning").classList.remove("hidden");
  }

  function final() {
    document.getElementById("warning").classList.add("hidden");
    document.getElementById("final").classList.remove("hidden");
  }
</script>

</body>
</html>
