<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Earn Panel</title>

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
  padding:18px;
  text-align:center;
  font-size:22px;
  font-weight:bold;
}

.container{
  max-width:700px;
  margin:auto;
  padding:20px;
}

.balance{
  background:#111827;
  color:white;
  padding:25px;
  border-radius:16px;
  margin-bottom:20px;
}

.balance small{
  opacity:.8;
}

.balance h1{
  margin-top:8px;
  font-size:32px;
}

.menu{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:14px;
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

button{
  width:100%;
  margin-top:15px;
  padding:12px;
  border:0;
  border-radius:10px;
  background:#2563eb;
  color:white;
  font-size:15px;
  font-weight:bold;
  cursor:pointer;
}

.page{
  display:none;
}

.page.active{
  display:block;
}

.back{
  background:#374151;
  margin-bottom:15px;
}

.task{
  background:white;
  padding:18px;
  border-radius:14px;
  margin-bottom:12px;
  box-shadow:0 2px 8px rgba(0,0,0,.06);
}

.task h3{
  margin-bottom:7px;
}

.task p{
  color:#666;
  font-size:14px;
}

input{
  width:100%;
  padding:13px;
  margin-top:10px;
  border:1px solid #ddd;
  border-radius:10px;
  outline:none;
}

.history{
  background:white;
  padding:16px;
  border-radius:12px;
  margin-bottom:10px;
}

footer{
  text-align:center;
  color:#777;
  font-size:13px;
  padding:30px 10px;
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

  <!-- DASHBOARD -->
  <section id="home" class="page active">

    <div class="balance">
      <small>Available Balance</small>
      <h1>₹0.00</h1>
      <p>Complete genuine tasks to earn.</p>
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
        <button onclick="showPage('withdraw')">Request Withdrawal</button>
      </div>

      <div class="card">
        <div style="font-size:30px;">👤</div>
        <h3>Profile</h3>
        <p>Manage your account information.</p>
        <button onclick="showPage('profile')">Open Profile</button>
      </div>

    </div>

  </section>


  <!-- TASKS -->
  <section id="tasks" class="page">

    <button class="back" onclick="showPage('home')">← Back to Dashboard</button>

    <h2 style="margin-bottom:15px;">📋 Available Tasks</h2>

    <div class="task">
      <h3>Task 1</h3>
      <p>Genuine task will appear here after the backend is connected.</p>
      <button onclick="alert('This task is not active yet.')">View Task</button>
    </div>

    <div class="task">
      <h3>Task 2</h3>
      <p>Task details and reward information will appear here.</p>
      <button onclick="alert('This task is not active yet.')">View Task</button>
    </div>

    <div class="task">
      <h3>Task 3</h3>
      <p>More verified tasks can be added from the admin panel.</p>
      <button onclick="alert('This task is not active yet.')">View Task</button>
    </div>

  </section>


  <!-- HISTORY -->
  <section id="history" class="page">

    <button class="back" onclick="showPage('home')">← Back to Dashboard</button>

    <h2 style="margin-bottom:15px;">📈 Earning History</h2>

    <div class="history">
      <strong>No earnings yet</strong>
      <p style="color:#777;margin-top:5px;">
        Your completed genuine tasks will appear here.
      </p>
    </div>

  </section>


  <!-- WITHDRAW -->
  <section id="withdraw" class="page">

    <button class="back" onclick="showPage('home')">← Back to Dashboard</button>

    <h2>💸 Withdraw</h2>

    <div class="card" style="margin-top:15px;">
      <p>
        Withdrawal requests will become available after your
        account has an eligible balance.
      </p>

      <input type="text" placeholder="UPI ID">

      <input type="number" placeholder="Amount">

      <button onclick="alert('Withdrawal system will be connected with the backend later.')">
        Submit Request
      </button>
    </div>

  </section>


  <!-- PROFILE -->
  <section id="profile" class="page">

    <button class="back" onclick="showPage('home')">← Back to Dashboard</button>

    <h2>👤 Profile</h2>

    <div class="card" style="margin-top:15px;">

      <label>Name</label>
      <input type="text" placeholder="Your name">

      <label style="display:block;margin-top:15px;">Email</label>
      <input type="email" placeholder="Your email">

      <button onclick="alert('Profile saving will be connected with the database later.')">
        Save Profile
      </button>

    </div>

  </section>

</div>

<footer>
  © 2026 Earn Panel
</footer>


<script>

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

</script>

</body>
</html>
