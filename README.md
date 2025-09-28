<html lang="en">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Korawit | demo</title>
  <style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {

    font-family: 'Comic Sans MS', cursive, sans-serif;
    background: url('https://i.postimg.cc/3wjsKkCP/20250920-010358.jpg') no-repeat center center;
    background-size: 100% 100%;
    height: 100vh;
    display: flex;
    justify-content: center; /* จัดกลางแนวนอน */
    align-items: center;     /* จัดกลางแนวตั้ง */
  }

  .top-image {
  position: absolute;   /* ให้อิสระจาก layout ปกติ */
  top: -10px;            /* ขยับลงมาจากด้านบน 30px */
  left: 20px;           /* ขยับมาจากซ้าย 50px */
  width: 160px;          /* ปรับขนาดความกว้าง */
  height: auto;         /* ให้ปรับสัดส่วนอัตโนมัติ */
  transition: transform 0.3s ease, background-color 0.2s ease; /* เผื่ออยากทำเอฟเฟกต์ */
}

.top-image:hover {
  transform: scale(1.1) /* ขยาย + เอียงเวลาเอาเมาส์ไปชี้ */
}

.top-image:active {
  transform: scale(0.9);
}

  .center-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    width: 100%;
    max-width: 540px;
  }

  .login-box {
    background: rgba(255, 240, 245, 0.6);
    backdrop-filter: blur(8px);
    -webkit-backdrop-filter: blur(8px);
    padding: 40px;
    border-radius: 45px;
    text-align: center;
    width: 100%;
    box-shadow: 0 0 20px rgba(0,0,0,0.1);
    transition: transform 0.8s ease, opacity 0.5s ease;
  }

  h2 {
    color: #ff69b4;
    margin-bottom: 20px;
    font-size: 26px;   /* ปรับขนาดตัวอักษร */
  line-height: 2.0;  /* ปรับความสูงบรรทัด */
  }

  .input-box {
  position: relative;
  width: 100%;
  margin: 15px 0;
  min-height: 70px; /* กล่องสูงขึ้น */
}

.input-box input {
  padding: 17px;
  width: 100%;
  border: 2px solid #ffb6c1;
  border-radius: 10px;
  font-size: 16px;
  outline: none;
  background: transparent;
}

.input-box label {
  position: absolute;
  top: 40%;
  left: 15px;
  transform: translateY(-50%);
  color: #999;
  pointer-events: none;
  transition: all 0.3s ease;
  background: rgba(255,240,245,0.6);
  padding: 0 5px;
  border-radius: 5px;
}

.input-box input:focus + label,
.input-box input:not(:placeholder-shown) + label {
  top: -8px;
  font-size: 12px;
  color: #ff69b4;
}

  button {
    padding: 15px 25px;
    background-color: #ff69b4;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-size: 16px;
  }

  /* กล่องล็อกอินเลื่อนออก */
  .login-box.slide-out {
    transform: translateX(-150%);
    opacity: 0;
  }

  /* กล่องรูปภาพตอนซ่อน */
  #imageContainer {
    display: none;
    opacity: 0;
    transform: translateX(150%);
    transition: transform 0.3s ease, opacity 0.3s ease;
  }

  /* กล่องรูปภาพเลื่อนเข้า */
  #imageContainer.show {
    opacity: 1;
    transform: translateX(0);
  }

  .hidden { display: none; }

  .image-container img {
    max-width: 100%;
    border-radius: 15px;
    margin-top: 20px;
    box-shadow: 0 0 15px rgba(0,0,0,0.2);
  }

  #imageContainer.show {
    opacity: 1;
    transform: translateX(0) scale(1);
    animation: popIn 0.3s ease forwards;
}

@keyframes popIn {
    0% {
        transform: translateX(0) scale(0.8);
        opacity: 0;
    }
    100% {
        transform: translateX(0) scale(1);
        opacity: 1;
    }
}


  /* กล่องแจ้งเตือน */
  #errorBox {
    position: fixed;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    background: white;
    padding: 20px 30px;
    border-radius: 15px;
    box-shadow: 0 0 20px rgba(0,0,0,0.3);
    text-align: center;
    z-index: 9999;
  }

  #errorBox p {
    margin-bottom: 15px;
    color: #ff69b4;
    font-weight: bold;
    font-family: 'Kanit', sans-serif;  /* ฟอนต์ใหม่ */
  }

  #errorBox button {
    padding: 10px 20px;
    background: #ff69b4;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
  }
   #bottomRightBox {
    position: fixed;
    bottom: 5px;
    right: 20px;
    background: rgba(255, 182, 193, 0.9);
    color: white;
    padding: 15px 20px;
    border-radius: 12px;
    font-size: 14px; /* <-- ปรับขนาดตัวอักษรที่นี่ */
    opacity: 1;
    transition: opacity 0.3s ease;
    z-index: 10000;
}

button {
    padding: 15px 25px;
    background-color: #ff69b4;
    color: white;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-size: 15px;
    transition: transform 0.1s ease, background-color 0.2s ease; /* <-- เพิ่ม transition */
}

button:active {
    transform: scale(0.80);         /* ย่อปุ่ม 95% */
    background-color: #ff85c1;      /* เปลี่ยนสีชั่วคราว */
}

  .hidden-bottom {
    display: none;      /* ซ่อน element จริง ๆ */
    opacity: 0;
    pointer-events: none;
}

#backgroundOverlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: url('https://i.postimg.cc/3wjsKkCP/20250920-010358.jpg') no-repeat center center;
  background-size: cover;  /* สามารถเปลี่ยนได้เป็น contain, auto, etc. */
  z-index: -1;  /* อยู่หลังทุกอย่าง */
  transition: background 0.5s ease, background-size 0.3s ease;
}

.outside-img {
  max-width: 300px;   /* กำหนดความกว้างสูงสุดของรูป */
  height: auto;       /* ให้ความสูงปรับตามสัดส่วน */
  border-radius: 0;   /* ไม่มีมุมโค้ง */
  box-shadow: none;   /* ไม่มีเงา */
  margin-top: 20px;   /* เว้นระยะบนของรูป */
  display: block;     /* ทำให้รูปเป็น block เพื่อจัด layout ง่าย */
}

</style>
 </head>
 <body id="pageBody">
  <div id="backgroundOverlay"></div> <!-- พื้นหลังใหม่ที่เราจะปรับขนาดได้ -->
    <img src="https://i.postimg.cc/5yBD8bhw/1758548455711.png"width="10%" height="19%" class="top-image" id="backToLogin">
  <div class="center-container" id="loginContainer">
  <!-- กล่องล็อกอิน -->
  <div class="login-box" id="loginForm">
    <h2>Hello everyone who entered. 💖</h2>
    <div class="input-box">
  <input type="text" id="username" placeholder=" " required>
  <label for="username">Username na hubb</label>
</div>

<div class="input-box">
  <input type="password" id="password" placeholder=" " required>
  <label for="password">Password (dd,mm)</label>
</div>

    <button type="button" onclick="login()">Login</button>
  </div>
</div>

<div class="center-container" id="imageContainer">
  <!-- กล่องแสดงรูป -->
  <div class="login-box" id="imageBox">
    <h2>Hi na hub you!! 🌸</h2>
    <div class="image-container">
      <img src="https://i.postimg.cc/FHhLwWpG/how-You-20250914-233456-0000.png" alt="My Image">
    </div>
  </div>

  <!-- เพิ่มรูปสำหรับ korawit -->
       <img src="https://i.postimg.cc/ZR3vQCC6/8b57589a-f721-4045-a41f-cdce91ef30e5.jpg" alt="korawit" class="outside-img" id="img-korawit" style="display:none;">

  <!-- เพิ่มรูปสำหรับ kantamxs -->
       <img src="https://i.postimg.cc/CxN8ckfV/pxfuel-21.jpg" alt="kantamxs" class="outside-img" id="img-kantamxs" style="display:none;">

</div>

  <!-- กล่องข้อความมุมขวาล่าง -->
  <div id="bottomRightBox">ดีฮ่ะ สำหรับคนที่เข้ามาลองดูก็นี่ฮับ<br> Username **korawit** Password **0301**<br>ถ้าใส่ของตัวเองก็น่าจะไม่ได้น่ะ💖<br>เอ่อ..นี่คือ Demo น่ะฮับ อาจจะมี Buck อยู่บ้างน้าา</div>

  <!-- กล่องแจ้งเตือน -->
  <div id="errorBox" class="hidden">
    <p>❌ Username หรือ Password ไม่ถูกต้อง น้าาา</p>
    <button onclick="closeError()">ตกลง</button>
  </div>
  <script>
  // รายชื่อผู้ใช้ พร้อมกำหนดภาพพื้นหลังและภาพแสดงผลเฉพาะของแต่ละคน
  const users = [
    {
      username: 'korawit',
      password: '0301',
      image: 'https://i.postimg.cc/FHhLwWpG/how-You-20250914-233456-0000.png',
      greeting: 'Hi na hub you!! 🌸'
    },
    {
      username: 'kantamxs',
      password: '2606',
      image: 'https://i.postimg.cc/1tRJJw5X/20250915-031854-0000.png',
      greeting: 'Hi na hub JuneNae~ Kantamxs! 🌸'
    }
    // เพิ่มผู้ใช้เพิ่มเติมได้ในรูปแบบเดียวกัน
  ];

  function login() {
  const usernameInput = document.getElementById('username').value.trim();
  const passwordInput = document.getElementById('password').value.trim();

  const user = users.find(u =>
    u.username.toLowerCase() === usernameInput.toLowerCase() &&
    u.password === passwordInput
  );

  if (user) {
    const loginContainer = document.getElementById('loginContainer');
    const bg = document.getElementById('backgroundOverlay');

    loginContainer.style.transition = "all 0.8s ease";
    loginContainer.style.transform = "translateX(-150%)";
    loginContainer.style.opacity = "0";

    setTimeout(() => {
      loginContainer.style.display = 'none';

      const imageContainer = document.getElementById('imageContainer');
      imageContainer.style.display = 'flex';
      setTimeout(() => imageContainer.classList.add('show'), 50);

      document.getElementById('bottomRightBox').classList.add('hidden-bottom');

      const imageBox = document.getElementById('imageBox');
      imageBox.querySelector('h2').textContent = user.greeting;

       // ---- แสดงเฉพาะ img ของผู้ใช้ ----
       document.querySelectorAll('.outside-img').forEach(img => img.style.display = 'none'); // ซ่อนรูปทั้งหมด

       // แสดงเฉพาะ img ของบัญชีที่ล็อกอิน
       const userImg = document.getElementById('img-' + user.username);
       if (userImg) {
           bg.style.backgroundImage = `url('${userImg.src}')`;
           bg.style.backgroundSize = "cover";
           bg.style.backgroundPosition = "center";
      }
    }, 800);

  } else {
  document.getElementById('errorBox').classList.remove('hidden');
}
  }

    function closeError() {
    document.getElementById('errorBox').classList.add('hidden');
  }

  // ฟังเหตุการณ์กด Enter บนช่อง input
  const usernameInput = document.getElementById('username');
  const passwordInput = document.getElementById('password');

  usernameInput.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {  // ถ้ากด Enter
      login();
    }
  });

  passwordInput.addEventListener('keydown', function(event) {
    if (event.key === 'Enter') {
      login();
    }
  });

  // ปุ่มย้อนกลับไปหน้า login
document.getElementById('backToLogin').addEventListener('click', function() {
  const loginContainer = document.getElementById('loginContainer');
  const imageContainer = document.getElementById('imageContainer');

  // ซ่อน imageContainer
  imageContainer.classList.remove('show');
  setTimeout(() => {
    imageContainer.style.display = 'none';
    // แสดง loginContainer
    loginContainer.style.display = 'flex';
    loginContainer.style.opacity = '1';
    loginContainer.style.transform = 'translateX(0)';
  }, 300);

  // คืนค่า background เดิม
  const bg = document.getElementById('backgroundOverlay');
  bg.style.backgroundImage = "url('https://i.postimg.cc/3wjsKkCP/20250920-010358.jpg')";
  bg.style.backgroundSize = "cover";
  bg.style.backgroundPosition = "center";

  // คืนกล่องข้อความมุมล่างขวา
  document.getElementById('bottomRightBox').classList.remove('hidden-bottom');
});

 </script>
</body>
</html>
