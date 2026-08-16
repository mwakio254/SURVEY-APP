<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>SURVEY-EARN Pro</title>

<style>
:root{
  --primary:#1877f2;
  --primary-dark:#0d5dcc;
  --bg:#f0f2f5;
  --surface:#fff;
  --text:#222;
  --muted:#65676b;
  --border:#e4e6eb;
  --success:#24b47e;
  --danger:#fa3e3e;
  --warning:#f5a623;
}

*{
  box-sizing:border-box;
  margin:0;
  padding:0;
  font-family:Arial,Helvetica,sans-serif;
}

body{
  background:var(--bg);
  color:var(--text);
  padding:15px;
  min-height:100vh;
}

.navbar{
  max-width:900px;
  margin:auto;
  background:white;
  padding:15px 20px;
  border-radius:12px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  box-shadow:0 2px 6px rgba(0,0,0,.08);
  margin-bottom:20px;
}

.brand{
  color:var(--primary);
  font-size:20px;
  font-weight:bold;
}

.app-container{
  max-width:900px;
  margin:auto;
  background:white;
  border-radius:16px;
  padding:25px;
  box-shadow:0 4px 12px rgba(0,0,0,.08);
}

.screen{
  display:none;
}

.screen.active{
  display:block;
}

h1,h2,h3{
  margin-bottom:15px;
}

p{
  color:var(--muted);
  line-height:1.5;
  margin-bottom:18px;
}

.btn{
  width:100%;
  padding:13px;
  border:none;
  border-radius:8px;
  font-size:15px;
  font-weight:bold;
  cursor:pointer;
  margin-bottom:10px;
}

.btn-primary{
  background:var(--primary);
  color:white;
}

.btn-primary:hover{
  background:var(--primary-dark);
}

.btn-success{
  background:var(--success);
  color:white;
}

.btn-danger{
  background:var(--danger);
  color:white;
}

.btn-dark{
  background:#242526;
  color:white;
}

.btn-outline{
  background:white;
  color:var(--text);
  border:1px solid var(--border);
}

.input-field{
  width:100%;
  padding:13px;
  border:1px solid var(--border);
  border-radius:8px;
  margin-bottom:14px;
  font-size:16px;
}

.metric-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
  gap:15px;
  margin:20px 0;
}

.metric-card{
  background:var(--bg);
  border:1px solid var(--border);
  border-radius:10px;
  padding:18px;
  text-align:center;
}

.metric-val{
  font-size:25px;
  font-weight:bold;
  margin-top:7px;
}

.progress-container{
  height:9px;
  background:var(--border);
  border-radius:5px;
  overflow:hidden;
  margin-bottom:20px;
}

.progress-bar{
  height:100%;
  width:0%;
  background:var(--primary);
  transition:.3s;
}

.quiz-meta{
  display:flex;
  justify-content:space-between;
  margin-bottom:20px;
  font-weight:bold;
}

.timer{
  color:var(--danger);
}

.answer-option{
  text-align:left;
  background:#f5f6f7;
  border:1px solid var(--border);
}

.answer-option:hover{
  background:#e8eaed;
}

.admin-card{
  background:var(--bg);
  border-radius:10px;
  padding:18px;
  margin-bottom:15px;
}

.table-responsive{
  overflow-x:auto;
}

table{
  width:100%;
  border-collapse:collapse;
  margin-top:15px;
}

th,td{
  padding:11px;
  border-bottom:1px solid var(--border);
  text-align:left;
  white-space:nowrap;
}

th{
  background:var(--bg);
}

.badge{
  padding:4px 8px;
  border-radius:5px;
  font-size:12px;
  font-weight:bold;
}

.paid{
  background:#e3fcef;
  color:var(--success);
}

.pending{
  background:#fff3cd;
  color:#a66b00;
}

.unpaid{
  background:#ffebe9;
  color:var(--danger);
}

.hidden{
  display:none!important;
}

.notice{
  background:#eaf3ff;
  border-radius:8px;
  padding:14px;
  margin-bottom:18px;
  color:#0759ad;
  font-size:14px;
}

.warning{
  background:#fff3cd;
  color:#765600;
}

.success-box{
  background:#e3fcef;
  color:#147a55;
  padding:15px;
  border-radius:8px;
  margin-bottom:15px;
}

.modal{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.55);
  display:none;
  align-items:center;
  justify-content:center;
  padding:20px;
  z-index:999;
}

.modal.active{
  display:flex;
}

.modal-content{
  background:white;
  width:100%;
  max-width:400px;
  padding:25px;
  border-radius:12px;
}

.small{
  font-size:13px;
  color:var(--muted);
}

@media(max-width:600px){
  body{
    padding:8px;
  }

  .app-container{
    padding:18px;
  }

  .navbar{
    padding:13px;
  }

  .brand{
    font-size:16px;
  }
}
</style>
</head>

<body>

<div class="navbar">
  <div class="brand">SURVEY-EARN Pro</div>

  <button class="btn btn-dark"
          style="width:auto;margin:0"
          onclick="handleAdminPanelAccess()">
    Admin Panel
  </button>
</div>

<div class="app-container">

<!-- ================= AUTH ================= -->

<div id="scrAuth" class="screen active">

  <h2>Create Survey Account</h2>

  <p>
    Create a demo survey account and complete surveys to earn points.
  </p>

  <input id="regName"
         class="input-field"
         type="text"
         placeholder="Full Name">

  <input id="regEmail"
         class="input-field"
         type="email"
         placeholder="Email Address">

  <input id="regPhone"
         class="input-field"
         type="tel"
         placeholder="M-PESA Phone Number">

  <div class="notice warning">
    <strong>Demo mode:</strong>
    Payment functionality is simulated. No real money is collected.
  </div>

  <button class="btn btn-primary"
          onclick="processRegistration()">
    Create Account
  </button>

</div>


<!-- ================= USER DASHBOARD ================= -->

<div id="scrUserHome" class="screen">

  <h2>
    Welcome, <span id="lblUserName">User</span>!
  </h2>

  <p>
    Complete available surveys and earn points.
  </p>

  <div class="metric-grid">

    <div class="metric-card">
      <div>Wallet Balance</div>
      <div class="metric-val"
           id="lblUserBalance"
           style="color:var(--success)">
        KSh 0.00
      </div>
    </div>

    <div class="metric-card">
      <div>Total Points</div>
      <div class="metric-val"
           id="lblUserPoints">
        0
      </div>
    </div>

    <div class="metric-card">
      <div>Surveys Completed</div>
      <div class="metric-val"
           id="lblCompleted">
        0
      </div>
    </div>

  </div>

  <div class="admin-card">

    <h3>Available Survey</h3>

    <p>
      <strong>Consumer Preferences Survey</strong>
    </p>

    <p>
      5 questions • 50 points • KSh 500 demo value
    </p>

    <button class="btn btn-success"
            onclick="startSurveyProcess()">
      Start Survey
    </button>

  </div>

  <button class="btn btn-primary"
          onclick="requestPayout()">
    Request M-PESA Withdrawal
  </button>

  <button class="btn btn-outline"
          onclick="logoutUser()">
    Logout
  </button>

</div>


<!-- ================= QUIZ ================= -->

<div id="scrQuiz" class="screen">

  <div class="progress-container">
    <div id="quizProgressBar"
         class="progress-bar">
    </div>
  </div>

  <div class="quiz-meta">

    <span id="lblProgressTracker">
      Question 1 of 5
    </span>

    <span class="timer">
      ⏱ <span id="lblTimerCount">15</span>s
    </span>

  </div>

  <h3 id="lblQuestionText">
    Question
  </h3>

  <button id="opt0"
          class="btn answer-option"
          onclick="submitUserAnswer(0)">
  </button>

  <button id="opt1"
          class="btn answer-option"
          onclick="submitUserAnswer(1)">
  </button>

  <button id="opt2"
          class="btn answer-option"
          onclick="submitUserAnswer(2)">
  </button>

  <button id="opt3"
          class="btn answer-option"
          onclick="submitUserAnswer(3)">
  </button>

</div>


<!-- ================= RESULTS ================= -->

<div id="scrResult" class="screen">

  <h2 style="color:var(--success)">
    Survey Completed 🎉
  </h2>

  <div class="success-box">
    Your answers have been recorded in this demo.
  </div>

  <div class="metric-grid">

    <div class="metric-card">
      <div>Points Earned</div>
      <div id="lblEarnedPoints"
           class="metric-val">
        +0
      </div>
    </div>

    <div class="metric-card">
      <div>Cash Value</div>
      <div id="lblEarnedCash"
           class="metric-val"
           style="color:var(--success)">
        KSh 0
      </div>
    </div>

  </div>

  <button class="btn btn-primary"
          onclick="returnToDashboardHome()">
    Return to Dashboard
  </button>

</div>


<!-- ================= ADMIN LOGIN ================= -->

<div id="scrAdminLogin" class="screen">

  <h2>Admin Login</h2>

  <p>
    Enter administrator credentials.
  </p>

  <input id="adminUsername"
         class="input-field"
         placeholder="Username">

  <input id="adminPassword"
         type="password"
         class="input-field"
         placeholder="Password">

  <div class="notice">
    Demo credentials:<br>
    Username: <strong>admin</strong><br>
    Password: <strong>1234</strong>
  </div>

  <button class="btn btn-primary"
          onclick="adminLogin()">
    Login
  </button>

  <button class="btn btn-outline"
          onclick="showScreen('scrAuth')">
    Back
  </button>

</div>


<!-- ================= ADMIN DASHBOARD ================= -->

<div id="scrAdmin" class="screen">

  <h2>Admin Dashboard</h2>

  <p>
    Manage demo users, surveys and withdrawal requests.
  </p>

  <div class="metric-grid">

    <div class="metric-card">
      <div>Total Users</div>
      <div id="adminUsers"
           class="metric-val">
        0
      </div>
    </div>

    <div class="metric-card">
      <div>Total Points</div>
      <div id="adminPoints"
           class="metric-val">
        0
      </div>
    </div>

    <div class="metric-card">
      <div>Completed Surveys</div>
      <div id="adminSurveys"
           class="metric-val">
        0
      </div>
    </div>

  </div>


  <div class="admin-card">

    <h3>Survey Management</h3>

    <input id="newQuestion"
           class="input-field"
           placeholder="New survey question">

    <button class="btn btn-primary"
            onclick="addQuestion()">
      Add Question
    </button>

  </div>


  <h3>Registered Users</h3>

  <div class="table-responsive">

    <table>

      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
          <th>Phone</th>
          <th>Points</th>
          <th>Balance</th>
          <th>Status</th>
        </tr>
      </thead>

      <tbody id="usersTable">
      </tbody>

    </table>

  </div>

  <br>

  <button class="btn btn-danger"
          onclick="resetDemo()">
    Reset Demo Data
  </button>

  <button class="btn btn-outline"
          onclick="logoutAdmin()">
    Logout Admin
  </button>

</div>

</div>


<!-- ================= PAYOUT MODAL ================= -->

<div id="payoutModal" class="modal">

  <div class="modal-content">

    <h3>Request Withdrawal</h3>

    <p>
      Enter the amount you want to request.
    </p>

    <input id="payoutAmount"
           class="input-field"
           type="number"
           placeholder="Amount in KSh">

    <button class="btn btn-success"
            onclick="confirmPayout()">
      Submit Request
    </button>

    <button class="btn btn-outline"
            onclick="closePayoutModal()">
      Cancel
    </button>

  </div>

</div>


<script>

/* ==========================================
   DATA
========================================== */

let users =
  JSON.parse(localStorage.getItem("surveyUsers")) || [];

let currentUser =
  JSON.parse(localStorage.getItem("currentSurveyUser")) || null;

let adminLoggedIn = false;

let currentQuestion = 0;

let score = 0;

let timer = null;

let timeLeft = 15;


/* ==========================================
   QUESTIONS
========================================== */

let questions = [

  {
    question:"Which device do you use most often?",
    options:[
      "Smartphone",
      "Laptop",
      "Tablet",
      "Desktop"
    ],
    answer:0
  },

  {
    question:"How often do you shop online?",
    options:[
      "Daily",
      "Weekly",
      "Monthly",
      "Rarely"
    ],
    answer:1
  },

  {
    question:"Which factor is most important when buying a product?",
    options:[
      "Price",
      "Colour",
      "Packaging",
      "Advertisement"
    ],
    answer:0
  },

  {
    question:"How do you usually discover new products?",
    options:[
      "Social media",
      "Television",
      "Newspaper",
      "Radio"
    ],
    answer:0
  },

  {
    question:"Would you recommend a good product to friends?",
    options:[
      "Yes",
      "No",
      "Maybe",
      "Not sure"
    ],
    answer:0
  }

];


/* ==========================================
   SCREEN CONTROL
========================================== */

function showScreen(id){

  document
    .querySelectorAll(".screen")
    .forEach(screen=>{
      screen.classList.remove("active");
    });

  document
    .getElementById(id)
    .classList.add("active");
}


/* ==========================================
   REGISTRATION
========================================== */

function processRegistration(){

  const name =
    document.getElementById("regName").value.trim();

  const email =
    document.getElementById("regEmail").value.trim();

  const phone =
    document.getElementById("regPhone").value.trim();

  if(!name || !email || !phone){

    alert("Please fill in all fields.");

    return;
  }

  const user = {

    id:Date.now(),

    name:name,

    email:email,

    phone:phone,

    points:0,

    balance:0,

    completed:0,

    status:"Active",

    payoutStatus:"None"

  };

  users.push(user);

  saveUsers();

  currentUser = user;

  localStorage.setItem(
    "currentSurveyUser",
    JSON.stringify(currentUser)
  );

  alert(
    "Account created successfully. Demo mode is active; no payment was taken."
  );

  updateDashboard();

  showScreen("scrUserHome");

}


/* ==========================================
   SAVE DATA
========================================== */

function saveUsers(){

  localStorage.setItem(
    "surveyUsers",
    JSON.stringify(users)
  );

}


/* ==========================================
   DASHBOARD
========================================== */

function updateDashboard(){

  if(!currentUser) return;

  document.getElementById("lblUserName")
    .textContent = currentUser.name;

  document.getElementById("lblUserBalance")
    .textContent =
    "KSh " +
    Number(currentUser.balance).toFixed(2);

  document.getElementById("lblUserPoints")
    .textContent =
    currentUser.points;

  document.getElementById("lblCompleted")
    .textContent =
    currentUser.completed;

}


/* ==========================================
   START SURVEY
========================================== */

function startSurveyProcess(){

  if(!currentUser){

    alert("Please create an account first.");

    showScreen("scrAuth");

    return;
  }

  currentQuestion = 0;

  score = 0;

  showScreen("scrQuiz");

  loadQuestion();

}


/* ==========================================
   LOAD QUESTION
========================================== */

function loadQuestion(){

  clearInterval(timer);

  const q = questions[currentQuestion];

  document.getElementById("lblQuestionText")
    .textContent = q.question;

  document.getElementById("lblProgressTracker")
    .textContent =
    "Question " +
    (currentQuestion + 1) +
    " of " +
    questions.length;

  document.getElementById("quizProgressBar")
    .style.width =
    ((currentQuestion) / questions.length * 100) + "%";

  for(let i=0;i<4;i++){

    document.getElementById("opt"+i)
      .textContent = q.options[i];

  }

  startTimer();

}


/* ==========================================
   TIMER
========================================== */

function startTimer(){

  timeLeft = 15;

  document.getElementById("lblTimerCount")
    .textContent = timeLeft;

  timer = setInterval(()=>{

    timeLeft--;

    document.getElementById("lblTimerCount")
      .textContent = timeLeft;

    if(timeLeft <= 0){

      clearInterval(timer);

      submitUserAnswer(-1);

    }

  },1000);

}


/* ==========================================
   ANSWER
========================================== */

function submitUserAnswer(selected){

  clearInterval(timer);

  const q = questions[currentQuestion];

  if(selected === q.answer){

    score++;

  }

  currentQuestion++;

  if(currentQuestion >= questions.length){

    finishSurvey();

  }else{

    loadQuestion();

  }

}


/* ==========================================
   FINISH SURVEY
========================================== */

function finishSurvey(){

  const earnedPoints =
    score * 10;

  const earnedCash =
    score * 100;

  currentUser.points += earnedPoints;

  currentUser.balance += earnedCash;

  currentUser.completed++;

  users = users.map(user =>
    user.id === currentUser.id
      ? currentUser
      : user
  );

  saveUsers();

  document.getElementById("quizProgressBar")
    .style.width = "100%";

  document.getElementById("lblEarnedPoints")
    .textContent =
    "+" + earnedPoints;

  document.getElementById("lblEarnedCash")
    .textContent =
    "KSh " + earnedCash;

  showScreen("scrResult");

}


/* ==========================================
   RETURN HOME
========================================== */

function returnToDashboardHome(){

  updateDashboard();

  showScreen("scrUserHome");

}


/* ==========================================
   PAYOUT
========================================== */

function requestPayout(){

  if(!currentUser) return;

  if(currentUser.balance <= 0){

    alert(
      "You do not have a balance available for withdrawal."
    );

    return;
  }

  document.getElementById("payoutAmount")
    .value = "";

  document.getElementById("payoutModal")
    .classList.add("active");

}


function closePayoutModal(){

  document.getElementById("payoutModal")
    .classList.remove("active");

}


function confirmPayout(){

  const amount =
    Number(
      document.getElementById("payoutAmount").value
    );

  if(!amount || amount <= 0){

    alert("Enter a valid amount.");

    return;
  }

  if(amount > currentUser.balance){

    alert("Amount exceeds your balance.");

    return;
  }

  currentUser.payoutStatus =
    "Pending";

  users = users.map(user =>
    user.id === currentUser.id
      ? currentUser
      : user
  );

  saveUsers();

  closePayoutModal();

  alert(
    "Withdrawal request recorded as PENDING in demo mode. No real M-PESA transaction was made."
  );

}


/* ==========================================
   ADMIN ACCESS
========================================== */

function handleAdminPanelAccess(){

  if(adminLoggedIn){

    showScreen("scrAdmin");

    updateAdminDashboard();

  }else{

    showScreen("scrAdminLogin");

  }

}


/* ==========================================
   ADMIN LOGIN
========================================== */

function adminLogin(){

  const username =
    document.getElementById("adminUsername").value;

  const password =
    document.getElementById("adminPassword").value;

  if(
    username === "admin" &&
    password === "1234"
  ){

    adminLoggedIn = true;

    updateAdminDashboard();

    showScreen("scrAdmin");

  }else{

    alert("Incorrect admin credentials.");

  }

}


/* ==========================================
   ADMIN DASHBOARD
========================================== */

function updateAdminDashboard(){

  document.getElementById("adminUsers")
    .textContent =
    users.length;

  document.getElementById("adminPoints")
    .textContent =
    users.reduce(
      (total,user)=>total + user.points,
      0
    );

  document.getElementById("adminSurveys")
    .textContent =
    users.reduce(
      (total,user)=>total + user.completed,
      0
    );

  renderUsers();

}


/* ==========================================
   USER TABLE
========================================== */

function renderUsers(){

  const table =
    document.getElementById("usersTable");

  table.innerHTML = "";

  users.forEach(user=>{

    let statusClass =
      user.payoutStatus === "Pending"
      ? "pending"
      : "paid";

    const row =
      document.createElement("tr");

    row.innerHTML = `

      <td>${escapeHTML(user.name)}</td>

      <td>${escapeHTML(user.email)}</td>

      <td>${escapeHTML(user.phone)}</td>

      <td>${user.points}</td>

      <td>KSh ${Number(user.balance).toFixed(2)}</td>

      <td>
        <span class="badge ${statusClass}">
          ${user.payoutStatus}
        </span>
      </td>

    `;

    table.appendChild(row);

  });

}


/* ==========================================
   ADD QUESTION
========================================== */

function addQuestion(){

  const input =
    document.getElementById("newQuestion");

  const question =
    input.value.trim();

  if(!question){

    alert("Enter a question.");

    return;
  }

  questions.push({

    question:question,

    options:[
      "Yes",
      "No",
      "Maybe",
      "Not sure"
    ],

    answer:0

  });

  input.value = "";

  alert(
    "Question added to the current demo survey."
  );

}


/* ==========================================
   LOGOUT USER
========================================== */

function logoutUser(){

  currentUser = null;

  localStorage.removeItem(
    "currentSurveyUser"
  );

  showScreen("scrAuth");

}


/* ==========================================
   LOGOUT ADMIN
========================================== */

function logoutAdmin(){

  adminLoggedIn = false;

  showScreen("scrAuth");

}


/* ==========================================
   RESET DEMO
========================================== */

function resetDemo(){

  const confirmReset =
    confirm(
      "Delete all demo users and data?"
    );

  if(!confirmReset) return;

  users = [];

  currentUser = null;

  localStorage.removeItem("surveyUsers");

  localStorage.removeItem(
    "currentSurveyUser"
  );

  updateAdminDashboard();

  alert("Demo data has been reset.");

}


/* ==========================================
   SECURITY HELPER
========================================== */

function escapeHTML(value){

  return String(value)
    .replace(/&/g,"&amp;")
    .replace(/</g,"&lt;")
    .replace(/>/g,"&gt;")
    .replace(/"/g,"&quot;")
    .replace(/'/g,"&#039;");

}


/* ==========================================
   LOAD EXISTING USER
========================================== */

if(currentUser){

  const savedUser =
    users.find(
      user => user.id === currentUser.id
    );

  if(savedUser){

    currentUser = savedUser;

    updateDashboard();

    showScreen("scrUserHome");

  }else{

    currentUser = null;

  }

}

</script>

</body>
</html>
