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
  max-width:700px;
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
    <p>Create a demo survey account and complete surveys to earn points.</p>

    <input id="regName" class="input-field" type="text" placeholder="Full Name">
    <input id="regEmail" class="input-field" type="email" placeholder="Email Address">
    <input id="regPhone" class="input-field" type="tel" placeholder="M-PESA Phone Number">

    <div class="notice warning">
      <strong>Demo mode:</strong> Payment functionality is simulated. No real money is collected.
    </div>

    <button class="btn btn-primary" onclick="processRegistration()">Create Account</button>
  </div>

  <!-- ================= USER DASHBOARD ================= -->
  <div id="scrUserHome" class="screen">
    <h2>Welcome, <span id="lblUserName">User</span>!</h2>
    <p>Complete available surveys and earn points.</p>

    <div class="metric-grid">
      <div class="metric-card">
        <div>Wallet Balance</div>
        <div class="metric-val" id="lblUserBalance" style="color:var(--success)">KSh 0.00</div>
      </div>

      <div class="metric-card">
        <div>Total Points</div>
        <div class="metric-val" id="lblUserPoints">0</div>
      </div>

      <div class="metric-card">
        <div>Surveys Completed</div>
        <div class="metric-val" id="lblCompleted">0</div>
      </div>
    </div>

    <div class="admin-card">
      <h3>Available Survey</h3>
      <p><strong>Consumer Preferences Survey</strong></p>
      <p>5 questions • 50 points • KSh 500 demo value</p>
      <button class="btn btn-success" onclick="startSurveyProcess()">Start Survey</button>
    </div>

    <button class="btn btn-primary" onclick="requestPayout()">Request M-PESA Withdrawal</button>
    <button class="btn btn-outline" onclick="logoutUser()">Logout</button>
  </div>

  <!-- ================= QUIZ ================= -->
  <div id="scrQuiz" class="screen">
    <div class="progress-container">
      <div id="quizProgressBar" class="progress-bar"></div>
    </div>

    <div class="quiz-meta">
      <span id="lblProgressTracker">Question 1 of 5</span>
      <span class="timer">⏱ <span id="lblTimerCount">15</span>s</span>
    </div>

    <h3 id="lblQuestionText">Question</h3>

    <button id="opt0" class="btn answer-option" onclick="submitUserAnswer(0)"></button>
    <button id="opt1" class="btn answer-option" onclick="submitUserAnswer(1)"></button>
    <button id="opt2" class="btn answer-option" onclick="submitUserAnswer(2)"></button>
    <button id="opt3" class="btn answer-option" onclick="submitUserAnswer(3)"></button>
  </div>

  <!-- ================= RESULTS ================= -->
  <div id="scrResult" class="screen">
    <h2 style="color:var(--success)">Survey Completed 🎉</h2>
    <div class="success-box">Your answers have been recorded in this demo.</div>

    <div class="metric-grid">
      <div class="metric-card">
        <div>Points Earned</div>
        <div id="lblEarnedPoints" class="metric-val">+0</div>
      </div>

      <div class="metric-card">
        <div>Cash Value</div>
        <div id="lblEarnedCash" class="metric-val" style="color:var(--success)">KSh 0</div>
      </div>
    </div>

    <button class="btn btn-primary" onclick="returnToDashboardHome()">Return to Dashboard</button>
  </div>

</div>

<!-- ================= DYNAMIC ADMIN OVERLAY MODAL ================= -->
<div id="adminModalElement" class="modal">
  <div class="modal-content">
    <h2>Admin Panel Ledger (Simulation)</h2>
    <p>Manage withdrawal payout actions and verify transaction processing pipeline logs locally.</p>
    <div class="table-responsive">
      <table>
        <thead>
          <tr>
            <th>Tx ID</th>
            <th>Recipient</th>
            <th>Amount</th>
            <th>Status</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody id="adminTableBody">
          <!-- Populated dynamically via JS -->
        </tbody>
      </table>
    </div>
    <button class="btn btn-dark" style="margin-top:20px" onclick="closeAdminPanelModal()">Close Admin Workspace</button>
  </div>
</div>

<!-- ================= APPLICATION ARCHITECTURE ENGINE ================= -->
<script>
  // --- CORE DATA CONFIGURATION ---
  const questions = [
    {
      question: "Which of the following beverage categories do you consume most frequently?",
      answers: ["Carbonated Soft Drinks", "Bottled Water / Juices", "Coffee / Tea Products", "Energy / Sports Drinks"],
      correct: 1
    },
    {
      question: "How do you primarily discover new consumer products?",
      answers: ["Social Media Ads", "Television Commercials", "Word of Mouth", "In-Store Displays"],
      correct: 0
    },
    {
      question: "What is your most important factor when choosing a shopping brand?",
      answers: ["Product Quality", "Low Pricing / Discounts", "Brand Reputation", "Eco-Friendly Practices"],
      correct: 0
    },
    {
      question: "On average, how many hours a day do you spend streaming video content?",
      answers: ["Less than 1 hour", "1 to 3 hours", "3 to 5 hours", "More than 5 hours"],
      correct: 1
    },
    {
      question: "Which device do you prefer using for online e-commerce shopping?",
      answers: ["Smartphone / Mobile App", "Laptop / Desktop PC", "Tablet Device", "Smart TV / Other"],
      correct: 0
    }
  ];

  // --- STATE VARIABLE STORES ---
  let currentUser = null;
  let currentQuestionIndex = 0;
