<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Project MKSIRS</title>
  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Orbitron', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: radial-gradient(circle at top, #000000 0%, #050d1c 100%);
      overflow: hidden;
      color: white;
    }

    .container {
      background: rgba(0, 0, 0, 0.7);
      backdrop-filter: blur(10px);
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 0 20px #00ffe5, 0 0 40px #007BFF inset;
      width: 100%;
      max-width: 500px;
      animation: fadeIn 1s ease-out;
    }

    h1 {
      font-size: 40px;
      margin-bottom: 10px;
      color: #00ffe5;
      text-shadow: 0 0 10px #00ffe5;
    }

    p {
      margin-bottom: 30px;
      font-size: 16px;
      color: #c5d8f7;
    }

    fieldset.accordion {
      border: none;
      margin-bottom: 20px;
      width: 100%;
    }

    legend {
      font-weight: bold;
      cursor: pointer;
      background: linear-gradient(135deg, #007BFF, #00ffe5);
      color: black;
      padding: 12px 20px;
      border-radius: 10px;
      font-size: 18px;
      box-shadow: 0 0 10px #00ffe5;
      transition: transform 0.3s ease;
    }

    legend:hover {
      transform: scale(1.05);
    }

    .accordion-content {
      display: none;
      margin-top: 10px;
      background: rgba(0, 123, 255, 0.2);
      padding: 15px;
      border-radius: 10px;
      box-shadow: inset 0 0 10px #007BFF;
    }

    label {
      display: block;
      cursor: pointer;
      padding: 10px;
      margin: 6px 0;
      background-color: #0056b3;
      border-radius: 8px;
      font-size: 16px;
      transition: background 0.3s ease, transform 0.2s ease;
    }

    input[type="radio"]:checked + label {
      background: #00ffe5;
      color: #000;
      font-weight: bold;
      transform: scale(1.03);
    }

    input[type="radio"], input[type="checkbox"] {
      display: none;
    }

    textarea, input[type="text"] {
      width: 100%;
      margin-top: 10px;
      padding: 12px;
      border: 2px solid #00ffe5;
      border-radius: 10px;
      background-color: #050d1c;
      color: white;
      font-size: 16px;
      transition: border-color 0.3s ease, background-color 0.3s ease;
    }

    textarea:focus, input[type="text"]:focus {
      border-color: #007BFF;
      background-color: #0a162f;
      outline: none;
    }

    input[type="range"] {
      width: 100%;
      margin-top: 15px;
      accent-color: #00ffe5;
    }

    button {
      width: 100%;
      padding: 15px;
      background: linear-gradient(90deg, #00ffe5, #007BFF);
      color: black;
      font-weight: bold;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-size: 18px;
      margin-top: 25px;
      box-shadow: 0 0 12px #00ffe5;
      transition: all 0.3s ease;
    }

    button:hover {
      transform: scale(1.05);
      background: linear-gradient(90deg, #007BFF, #00ffe5);
    }

    .fullscreen-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background: rgba(0, 0, 0, 0.95);
      display: none;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      color: white;
      font-size: 36px;
      text-align: center;
    }

    .fullscreen-overlay img {
      width: 120px;
      margin-bottom: 30px;
    }

    .error-message {
      display: none;
      color: #ff4b4b;
      font-size: 32px;
      font-weight: bold;
      padding: 40px;
      text-shadow: 0 0 5px red;
    }

    .close-button {
      margin-top: 30px;
      padding: 12px 24px;
      font-size: 20px;
      background: red;
      color: white;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      box-shadow: 0 0 10px red;
      transition: transform 0.2s ease;
    }

    .close-button:hover {
      transform: scale(1.1);
    }

    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(-20px);}
      to {opacity: 1; transform: translateY(0);}
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>SIRS</h1>
    <p>BUILD YOUR OWN FRIEND.</p>
    <form id="charForm">
      <fieldset class="accordion">
        <legend onclick="toggleAccordion(this)">Gender-Programmierung</legend>
        <div class="accordion-content">
          <input type="radio" id="gender1" name="gender_programming" value="Maskulin"> <label for="gender1">Maskulin</label>
          <input type="radio" id="gender2" name="gender_programming" value="Feminin"> <label for="gender2">Feminin</label>
          <input type="radio" id="gender3" name="gender_programming" value="Divers"> <label for="gender3">Divers</label>
        </div>
      </fieldset>
      <fieldset class="accordion">
        <legend onclick="toggleAccordion(this)">Intelligenz</legend>
        <div class="accordion-content">
          <input type="range" id="intelligence" name="intelligence" min="1" max="100">
        </div>
      </fieldset>
      <fieldset class="accordion">
        <legend onclick="toggleAccordion(this)">Persönlichkeit</legend>
        <div class="accordion-content">
          <input type="radio" id="personality1" name="personality" value="Elegant, Kultiviert, Intelligent"> <label for="personality1">Elegant, Kultiviert, Intelligent</label>
          <input type="radio" id="personality2" name="personality" value="Freundschaftlich, Hilfsbereit, Motivierend"> <label for="personality2">Freundschaftlich, Hilfsbereit, Motivierend</label>
          <input type="radio" id="personality3" name="personality" value="Romantisch, Neugierig, Liebevoll"> <label for="personality3">Romantisch, Neugierig, Liebevoll</label>
        </div>
      </fieldset>
      <fieldset class="accordion">
        <legend onclick="toggleAccordion(this)">Eigenschaft</legend>
        <div class="accordion-content">
          <input type="radio" id="trait1" name="trait" value="Popkultur & Unterhaltung"> <label for="trait1">Popkultur & Unterhaltung</label>
          <input type="radio" id="trait2" name="trait" value="Philosophische Themen"> <label for="trait2">Philosophische Themen</label>
          <input type="radio" id="trait3" name="trait" value="Intime Ansprechthemen"> <label for="trait3">Intime Ansprechthemen</label>
        </div>
      </fieldset>
      <fieldset class="accordion">
        <legend onclick="toggleAccordion(this)">Name</legend>
        <div class="accordion-content">
          <textarea id="thoughts" placeholder="Schreibe einen Namen..."></textarea>
        </div>
      </fieldset>
      <button type="button" onclick="validateAndGenerate()">Erstellen</button>
    </form>
  </div>

  <div class="fullscreen-overlay" id="loadingOverlay">
    <img src="https://cdnl.iconscout.com/lottie/premium/thumb/loading-circle-5922100-4936396.gif" alt="Ladeanimation">
  </div>

  <div class="fullscreen-overlay error-message" id="errorMessage">
    "Warum einen Freund erschaffen, wenn Du auch welche selber finden kannst. In der echten Welt."
    <button class="close-button" onclick="closeError()">Schließen</button>
  </div>

  <script>
    function toggleAccordion(element) {
      const content = element.nextElementSibling;
      content.style.display = content.style.display === "block" ? "none" : "block";
    }

    function validateAndGenerate() {
      document.getElementById("loadingOverlay").style.display = "flex";
      setTimeout(() => {
        document.getElementById("loadingOverlay").style.display = "none";
        document.getElementById("errorMessage").style.display = "flex";
      }, 5000);
    }

    function closeError() {
      document.getElementById("errorMessage").style.display = "none";
    }
  </script>
</body>
</html>
