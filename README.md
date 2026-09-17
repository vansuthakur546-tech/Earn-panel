<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Earn Panel</title>

<script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js@2"></script>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
  font-family:Arial,sans-serif;
}

body{
  background:#f4f6f9;
  color:#222;
}

header{
  background:#111827;
  color:white;
  padding:20px;
  text-align:center;
  font-size:24px;
  font-weight:bold;
}

.container{
  max-width:700px;
  margin:auto;
  padding:20px;
}

.page{
  display:none;
}

.page.active{
  display:block;
}

.auth-box{
  background:white;
  padding:25px;
  border-radius:18px;
  box-shadow:0 3px 12px rgba(0,0,0,.08);
  margin-top:30px;
}

.auth-box h2{
  margin-bottom:15px;
}

input{
  width:100%;
  padding:13px;
  margin-top:10px;
  border:1px solid #ddd;
  border-radius:10px;
  outline:none;
}

button{
  width:100%;
  margin-top:15px;
  padding:13px;
  border:0;
  border-radius:10px;
  background:#2563eb;
  color:white;
  font-size:15px;
  font-weight:bold;
}

.secondary{
  background:#374151;
}

.link-btn{
  background:none;
  color:#2563eb;
  padding:5px;
}

.balance{
  background:#111827;
  color:white;
  padding:25px;
  border-radius:18px;
  margin-bottom:20px;
}

.balance small{
  opacity:.8;
}

.balance h1{
  margin:8px 0;
  font-size:34px;
}

.menu{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:15px;
}

.card{
  background:white;
  padding:20px;
  border-radius:16px;
  box-shadow:0 3px 12px rgba(0,0,0,.08);
}

.card h3{
  margin:10px 0;
}

.card p{
  color:#666;
  font-size:14px;
  line-height:1.5;
}

.back{
  background:#374151;
  margin-bottom:18px;
}

.task,
.history{
  background:white;
  padding:18px;
  border-radius:14px;
  margin-bottom:14px;
  box-shadow:0 2px 8px rgba(0,0,0,.06);
}

.task h3{
  margin-bottom:8px;
}

.task p{
  color:#666;
  font-size:14px;
}

footer{
  text-align:center;
  color:#777;
  padding:30px 10px;
  font-size:13px;
}

#userEmail{
  color:#666;
  margin-top:8px;
  font-size:14px;
}

@media(max-width:500px){
  .menu{
    grid-template-columns:1fr;
  }
}
</style>
</head>

<body>

<header>
💰 Earn Panel
</header>

<div class="container">

<!-- LOGIN -->
<section id="login" class="page active">

<div class="auth-box">

<h2>🔐 Login</h2>

<input id="loginEmail" type="email" placeholder="Email">

<input id="loginPassword" type="password" placeholder="Password">

<button onclick="loginUser()">Login</button>

<button class="link-btn" onclick="showPage('signup')">
Create New Account
</button>

<p id="loginMessage"></p>

</div>

</section>


<!-- SIGNUP -->
<section id="signup" class="page">

<div class="auth-box">

<h2>📝 Create Account</h2>

<input id="signupName" type="text" placeholder="Your Name">

<input id="signupEmail" type="email" placeholder="Email">

<input id="signupPassword" type="password" placeholder="Password">

<button onclick="signupUser()">Sign Up</button>

<button class="link-btn" onclick="showPage('login')">
Already have an account? Login
</button>

<p id="signupMessage"></p>

</div>

</section>


<!-- HOME -->
<section id="home" class="page">

<div class="balance">

<small>Available Balance</small>

<h1>₹0.00</h1>

<p>Complete genuine tasks to earn.</p>

</div>

<div class="card" style="margin-bottom:20px;">

<strong>👤 Account</strong>

<p id="userEmail"></p>

<button class="secondary" onclick="logoutUser()">
Logout
</button>

</div>

<div class="menu">

<div class="card">
<div style="font-size:30px;">📋</div>
<h3>Complete Tasks</h3>
<p>View available genuine tasks and services.</p>
<button onclick="showPage('tasks')">View Tasks</button>
</div>

<div class="card">
<div style="font-size:30px;">📈</div>
<h3>Earning History</h3>
<p>See your completed tasks and earnings.</p>
<button onclick="showPage('history')">View History</button>
</div>

<div class="card">
<div style="font-size:30px;">💸</div>
<h3>Withdraw</h3>
<p>Submit a withdrawal request when eligible.</p>
<button onclick="showPage('withdraw')">
Request Withdrawal
</button>
</div>

<div class="card">
<div style="font-size:30px;">👤</div>
<h3>Profile</h3>
<p>Manage your account information.</p>
<button onclick="showPage('profile')">
Open Profile
</button>
</div>

</div>

</section>


<!-- TASKS -->
<section id="tasks" class="page">

<button class="back" onclick="showPage('home')">
← Back to Dashboard
</button>

<h2>📋 Available Tasks</h2>

<div class="task" style="margin-top:15px;">
<h3>Task 1</h3>
<p>Verified genuine task will appear here.</p>
<button onclick="alert('This task is not active yet.')">
View Task
</button>
</div>

<div class="task">
<h3>Task 2</h3>
<p>Task details and reward will appear here.</p>
<button onclick="alert('This task is not active yet.')">
View Task
</button>
</div>

<div class="task">
<h3>Task 3</h3>
<p>More verified tasks can be added later.</p>
<button onclick="alert('This task is not active yet.')">
View Task
</button>
</div>

</section>


<!-- HISTORY -->
<section id="history" class="page">

<button class="back" onclick="showPage('home')">
← Back to Dashboard
</button>

<h2>📈 Earning History</h2>

<div class="history" style="margin-top:15px;">

<strong>No earnings yet</strong>

<p style="color:#777;margin-top:7px;">
Your completed tasks and genuine earnings will appear here.
</p>

</div>

</section>


<!-- WITHDRAW -->
<section id="withdraw" class="page">

<button class="back" onclick="showPage('home')">
← Back to Dashboard
</button>

<h2>💸 Withdraw</h2>

<div class="card" style="margin-top:15px;">

<p>
Withdrawal requests will be available when your balance meets
the required minimum.
</p>

<input type="text" placeholder="UPI ID">

<input type="number" placeholder="Withdrawal Amount">

<button onclick="alert('Withdrawal system will be connected later.')">
Submit Withdrawal Request
</button>

</div>

</section>


<!-- PROFILE -->
<section id="profile" class="page">

<button class="back" onclick="showPage('home')">
← Back to Dashboard
</button>

<h2>👤 Profile</h2>

<div class="card" style="margin-top:15px;">

<label>Name</label>

<input id="profileName" type="text" placeholder="Enter your name">

<label style="display:block;margin-top:15px;">
Email
</label>

<input id="profileEmail" type="email" readonly>

<button onclick="alert('Profile saving will be connected later.')">
Save Profile
</button>

</div>

</section>

</div>

<footer>
© 2026 Earn Panel
</footer>


<script>

/* =========================
   SUPABASE CONNECTION
========================= */

const SUPABASE_URL =
"https://nifuokxsyjkqkyrlcwiv.supabase.co";

const SUPABASE_PUBLISHABLE_KEY =
sb_publishable_KGM5pbp1HlKc4bSxAhhpGg_1HTxIjG8

const supabaseClient =
supabase.createClient(
SUPABASE_URL,
SUPABASE_PUBLISHABLE_KEY
);

/* =========================
   PAGE SWITCH
========================= */

function showPage(pageId){

let pages = document.querySelectorAll(".page");

pages.forEach(function(page){
page.classList.remove("active");
});

document.getElementById(pageId).classList.add("active");

window.scrollTo({
top:0,
behavior:"smooth"
});

}


/* =========================
   SIGNUP
========================= */

async function signupUser(){

const name =
document.getElementById("signupName").value.trim();

const email =
document.getElementById("signupEmail").value.trim();

const password =
document.getElementById("signupPassword").value;

const message =
document.getElementById("signupMessage");

if(!name || !email || !password){

message.innerText =
"Please fill all fields.";

return;

}

const { data, error } =
await supabaseClient.auth.signUp({

email:email,

password:password,

options:{
data:{
name:name
}
}

});

if(error){

message.innerText = error.message;

return;

}

message.innerText =
"Account created successfully. You can now login.";

setTimeout(function(){

showPage("login");

},1500);

}


/* =========================
   LOGIN
========================= */

async function loginUser(){

const email =
document.getElementById("loginEmail").value.trim();

const password =
document.getElementById("loginPassword").value;

const message =
document.getElementById("loginMessage");

if(!email || !password){

message.innerText =
"Please enter email and password.";

return;

}

const { data, error } =
await supabaseClient.auth.signInWithPassword({

email:email,

password:password

});

if(error){

message.innerText =
error.message;

return;

}

message.innerText =
"Login successful!";

loadUser();

}


/* =========================
   LOAD USER
========================= */

async function loadUser(){

const { data } =
await supabaseClient.auth.getUser();

if(!data.user){

showPage("login");

return;

}

document.getElementById("userEmail").innerText =
data.user.email;

document.getElementById("profileEmail").value =
data.user.email;

document.getElementById("profileName").value =
data.user.user_metadata?.name || "";

showPage("home");

}


/* =========================
   LOGOUT
========================= */

async function logoutUser(){

await supabaseClient.auth.signOut();

showPage("login");

}


/* =========================
   CHECK LOGIN
========================= */

loadUser();

</script>

</body>
</html>
