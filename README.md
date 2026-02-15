<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SETTING SUPPORT</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700&display=swap" rel="stylesheet">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Orbitron',sans-serif;
  color:#00ffff; /* TOÀN BỘ CHỮ XANH */
}

body{
  background: radial-gradient(circle at top,#001a1a,#000);
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  overflow:hidden;
}

/* Glow background */
body::before{
  content:"";
  position:absolute;
  width:600px;
  height:600px;
  background:radial-gradient(circle,#00ffff33,transparent 70%);
  filter:blur(120px);
  animation:moveGlow 8s infinite alternate;
}

@keyframes moveGlow{
  from{transform:translate(-100px,-100px);}
  to{transform:translate(100px,100px);}
}

/* Glass box */
.box{
  position:relative;
  width:95%;
  max-width:400px;
  padding:30px 20px;
  border-radius:20px;
  backdrop-filter:blur(20px);
  background:rgba(0,0,0,0.6);
  border:1px solid #00ffff55;
  box-shadow:0 0 30px #00ffff33;
  text-align:center;
  animation:fade 1s ease;
}

@keyframes fade{
  from{opacity:0; transform:translateY(20px);}
  to{opacity:1; transform:translateY(0);}
}

h2{
  margin-bottom:20px;
  letter-spacing:2px;
  text-shadow:0 0 10px #00ffff;
}

input{
  width:85%;
  padding:12px;
  border-radius:10px;
  border:none;
  outline:none;
  text-align:center;
  margin-bottom:15px;
  background:#111;
  font-size:16px;
  box-shadow:0 0 10px #00ffff33 inset;
}

button{
  padding:12px 25px;
  border:none;
  border-radius:10px;
  background:#00ffff;
  color:#00ffff; /* CHỮ XANH */
  font-weight:bold;
  cursor:pointer;
  transition:0.3s;
  box-shadow:0 0 10px #00ffff55;
}

button:hover{
  box-shadow:0 0 20px #00ffff;
  transform:scale(1.05);
}

.error{
  color:red;
  margin-top:10px;
  display:none;
}

.menu{
  display:none;
}

.title{
  font-size:22px;
  margin-bottom:20px;
  text-shadow:0 0 10px #00ffff;
}

/* Toggle */
.toggle{
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding:12px 15px;
  margin-bottom:12px;
  border-radius:12px;
  background:#111;
  transition:0.3s;
}

.toggle:hover{
  background:#1a1a1a;
  box-shadow:0 0 10px #00ffff33;
}

.switch{
  position:relative;
  width:50px;
  height:25px;
}

.switch input{
  opacity:0;
  width:0;
  height:0;
}

.slider{
  position:absolute;
  cursor:pointer;
  top:0;
  left:0;
  right:0;
  bottom:0;
  background:#333;
  border-radius:25px;
  transition:0.4s;
}

.slider:before{
  position:absolute;
  content:"";
  height:19px;
  width:19px;
  left:3px;
  bottom:3px;
  background:#00ffff;
  border-radius:50%;
  transition:0.4s;
}

input:checked + .slider{
  background:#00ffff;
  box-shadow:0 0 15px #00ffff;
}

input:checked + .slider:before{
  transform:translateX(24px);
}

/* File input */
.file-input{
  font-size:12px;
  width:150px;
  }

/* Success text */
.success{
  margin-top:10px;
  display:none;
  animation:fadeIn 0.5s ease forwards;
  text-shadow:0 0 8px #00ffff;
}

@keyframes fadeIn{
  from{opacity:0; transform:translateY(10px);}
  to{opacity:1; transform:translateY(0);}
}

</style>
</head>

<body>

<div class="box" id="loginBox">
  <h2>🔒 LOGIN</h2>
  <input type="password" id="password" placeholder="Nhập mật khẩu...">
  <br>
  <button onclick="login()">ĐĂNG NHẬP</button>
  <div class="error" id="error">Sai mật khẩu!</div>
</div>

<div class="box menu" id="menuBox">
  <div class="title">FREE FIRE</div>

  <div class="toggle">
    <span>UNLOCK SECRET KEY</span>
    <label class="switch">
      <input type="checkbox">
      <span class="slider"></span>
    </label>
  </div>

  <div class="toggle">
    <span>MAGIC</span>
    <label class="switch">
      <input type="checkbox">
      <span class="slider"></span>
    </label>
  </div>

  <div class="toggle">
    <span>REDUCE RESISTANCE</span>
    <label class="switch">
      <input type="checkbox">
      <span class="slider"></span>
    </label>
  </div>

  <div class="toggle">
    <span>REDUCE DISPLAY</span>
    <label class="switch">
      <input type="checkbox">
      <span class="slider"></span>
    </label>
  </div>

  <div class="toggle">
    <span>REDUCE VIBRATION</span>
    <label class="switch">
      <input type="checkbox">
      <span class="slider"></span>
    </label>
  </div>

  <div class="toggle">
    <span>AIMING ASSIST</span>
    <label class="switch">
      <input type="checkbox">
      <span class="slider"></span>
    </label>
  </div>

  <div class="toggle">
    <span>CACHE</span>
    <input type="file" id="cacheFile" class="file-input">
  </div>

  <button onclick="confirmCache()">XÁC NHẬN</button>
  <div class="success" id="cacheSuccess">Xác nhận thành công</div>

</div>

<script>
function login(){
  const pass=document.getElementById("password").value;
  const error=document.getElementById("error");
  if(pass==="1234"){
    document.getElementById("loginBox").style.display="none";
    document.getElementById("menuBox").style.display="block";
  }else{
    error.style.display="block";
  }
}

function confirmCache(){
  const fileInput = document.getElementById("cacheFile");
  const success = document.getElementById("cacheSuccess");

  if(fileInput.files.length > 0){
    success.style.display="block";
  }else{
    alert("Vui lòng chọn tệp trước!");
  }
}

document.addEventListener("keypress",function(e){
  if(e.key==="Enter"){
    login();
  }
});
</script>

</body>
</html>
