<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#0b0b0f">
  <title>IRSH — Your Coding Platform</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Display",
                   "Segoe UI", sans-serif;
    }

    body {
      min-height: 100vh;
      background:
        radial-gradient(circle at top, #25252d 0%, #0b0b0f 45%);
      color: #fff;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
    }

    .app {
      width: 100%;
      max-width: 430px;
      min-height: 760px;
      background: rgba(15, 15, 20, 0.96);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 32px;
      padding: 28px 24px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      box-shadow: 0 25px 80px rgba(0,0,0,.5);
    }

    .logo {
      width: 72px;
      height: 72px;
      border-radius: 22px;
      background: #fff;
      color: #0b0b0f;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 26px;
      font-weight: 800;
      margin: 0 auto 28px;
      letter-spacing: -1px;
    }

    h1 {
      text-align: center;
      font-size: 42px;
      letter-spacing: -2px;
      margin-bottom: 10px;
    }

    .subtitle {
      text-align: center;
      color: #a1a1aa;
      font-size: 16px;
      margin-bottom: 45px;
    }

    .buttons {
      display: flex;
      flex-direction: column;
      gap: 13px;
    }

    button {
      width: 100%;
      padding: 17px;
      border-radius: 15px;
      border: none;
      font-size: 16px;
      font-weight: 700;
      cursor: pointer;
      transition: .2s;
    }

    .primary {
      background: #fff;
      color: #09090b;
    }

    .secondary {
      background: #1c1c23;
      color: #fff;
      border: 1px solid #30303a;
    }

    button:active {
      transform: scale(.97);
    }

    .footer {
      text-align: center;
      color: #666672;
      font-size: 12px;
      margin-top: 45px;
    }

    .modal {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,.75);
      backdrop-filter: blur(12px);
      align-items: center;
      justify-content: center;
      padding: 20px;
    }

    .modal-box {
      width: 100%;
      max-width: 400px;
      background: #15151b;
      border: 1px solid #292932;
      border-radius: 25px;
      padding: 25px;
    }

    .modal-box h2 {
      margin-bottom: 22px;
      font-size: 25px;
    }

    input {
      width: 100%;
      padding: 15px;
      margin-bottom: 12px;
      border-radius: 13px;
      border: 1px solid #30303a;
      background: #0d0d11;
      color: white;
      outline: none;
      font-size: 15px;
    }

    input:focus {
      border-color: #777;
    }

    .close {
      background: transparent;
      color: #999;
      margin-top: 8px;
    }

    .dashboard {
      display: none;
      text-align: center;
    }

    .dashboard h2 {
      font-size: 30px;
      margin-bottom: 10px;
    }

    .dashboard p {
      color: #999;
      margin-bottom: 25px;
    }

    .card {
      background: #19191f;
      border: 1px solid #292932;
      border-radius: 18px;
      padding: 20px;
      text-align: left;
      margin-bottom: 12px;
    }

    .card strong {
      display: block;
      margin-bottom: 5px;
    }

    .card span {
      color: #888;
      font-size: 13px;
    }
  </style>
</head>

<body>

  <main class="app">

    <!-- HOME -->
    <section id="home">
      <div class="logo">IR</div>

      <h1>IRSH</h1>

      <p class="subtitle">
        Your coding platform.
      </p>

      <div class="buttons">
        <button class="primary" onclick="openModal('signin')">
          Sign In
        </button>

        <button class="secondary" onclick="openModal('signup')">
          Create Account
        </button>
      </div>

      <div class="footer">
        © 2026 IRSH. Build something great.
      </div>
    </section>

    <!-- DASHBOARD -->
    <section id="dashboard" class="dashboard">

      <div class="logo">IR</div>

      <h2>Welcome to IRSH</h2>
      <p>Your projects, your code, your space.</p>

      <div class="card">
        <strong>📁 My Projects</strong>
        <span>Create and manage your projects.</span>
      </div>

      <div class="card">
        <strong>💻 Repositories</strong>
        <span>Store and manage your code.</span>
      </div>

      <div class="card">
        <strong>🌐 Deploy</strong>
        <span>Turn your projects into live websites.</span>
      </div>

      <button class="secondary" onclick="logout()">
        Sign Out
      </button>

    </section>

  </main>


  <!-- MODAL -->
  <div class="modal" id="modal">

    <div class="modal-box">

      <h2 id="modalTitle">Sign In</h2>

      <input
        type="email"
        id="email"
        placeholder="Email address"
      >

      <input
        type="password"
        id="password"
        placeholder="Password"
      >

      <button class="primary" onclick="submitForm()">
        Continue
      </button>

      <button class="close" onclick="closeModal()">
        Cancel
      </button>

    </div>

  </div>


  <script>

    let mode = "signin";

    function openModal(type) {
      mode = type;

      document.getElementById("modal").style.display = "flex";

      document.getElementById("modalTitle").textContent =
        type === "signin" ? "Sign In" : "Create Account";
    }

    function closeModal() {
      document.getElementById("modal").style.display = "none";
    }

    function submitForm() {

      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;

      if (!email || !password) {
        alert("Please enter your email and password.");
        return;
      }

      closeModal();

      document.getElementById("home").style.display = "none";
      document.getElementById("dashboard").style.display = "block";
    }

    function logout() {
      document.getElementById("dashboard").style.display = "none";
      document.getElementById("home").style.display = "block";
    }

  </script>

</body>
</html>