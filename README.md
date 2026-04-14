<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>ログイン</title>
</head>
<body>

<h2>ログイン画面</h2>

<input type="email" id="email" placeholder="メール"><br><br>
<input type="password" id="password" placeholder="パスワード"><br><br>

<button onclick="login()">ログイン</button>

<script type="module">
  // Firebase最新の書き方
  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
  import { getAuth, signInWithEmailAndPassword } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-auth.js";

  const firebaseConfig = {
    apiKey: "ここにコピーした値",
    authDomain: "ここにコピーした値",
    projectId: "ここにコピーした値"
  };

  const app = initializeApp(firebaseConfig);
  const auth = getAuth(app);

  window.login = function () {
    const email = document.getElementById("email").value;
    const password = document.getElementById("password").value;

    signInWithEmailAndPassword(auth, email, password)
      .then(() => {
        alert("ログイン成功！");
      })
      .catch((error) => {
        alert(error.message);
      });
  }
</script>

</body>
</html>
