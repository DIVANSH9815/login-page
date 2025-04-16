<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hacker Login</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <div class="login-container">
    <div class="login-box">
      <h1>Login</h1>
      <form id="loginForm" onsubmit="return handleLogin(event)">
        <div class="textbox">
          <input type="text" id="username" name="username" placeholder="Username" required>
        </div>
        <div class="textbox">
          <input type="password" id="password" name="password" placeholder="Password" required>
        </div>
        <input type="submit" value="Login" class="btn">
      </form>
      <div id="error-message" class="error-message"></div>
    </div>
  </div>

  <script src="scripts.js"></script>
</body>
</html>

/* Global Styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #141414;
  font-family: 'Courier New', Courier, monospace;
  color: #00FF00;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

h1 {
  text-align: center;
  font-size: 36px;
  margin-bottom: 20px;
  text-transform: uppercase;
}

.login-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.login-box {
  background: rgba(0, 0, 0, 0.8);
  padding: 30px;
  border-radius: 10px;
  width: 300px;
  box-shadow: 0 0 10px rgba(0, 255, 0, 0.3);
}

.textbox {
  margin-bottom: 15px;
  position: relative;
}

.textbox input {
  width: 100%;
  padding: 12px;
  background: #141414;
  border: 2px solid #00FF00;
  color: #00FF00;
  border-radius: 5px;
  font-size: 16px;
  outline: none;
}

.textbox input:focus {
  border-color: #00CC00;
}

.btn {
  width: 100%;
  padding: 12px;
  background: #00FF00;
  border: none;
  color: #141414;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  border-radius: 5px;
  transition: background 0.3s ease;
}

.btn:hover {
  background: #00CC00;
}

.error-message {
  color: red;
  margin-top: 10px;
  text-align: center;
}

function handleLogin(event) {
  event.preventDefault();  // Prevent form from submitting to keep page from refreshing
  
  const username = document.getElementById('username').value;
  const password = document.getElementById('password').value;
  const errorMessage = document.getElementById('error-message');

  // Basic input validation
  if (username === "" || password === "") {
    errorMessage.innerText = "Both fields are required!";
    return false;
  }

  // Simulating login check (you can replace this with an actual backend call)
  if (username === "admin" && password === "password123") {
    errorMessage.innerText = "Login successful!";
    errorMessage.style.color = "green";
    // Here you can redirect or show the next page
    setTimeout(() => {
      window.location.href = "dashboard.html"; // Redirect to a dashboard or homepage
    }, 1000);
  } else {
    errorMessage.innerText = "Invalid username or password!";
  }
  return false;  // Prevent form submission
}
