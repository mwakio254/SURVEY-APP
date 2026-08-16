<!DOCTYPE html>
<html lang="e">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Premium Paid Survey & Secure Admin Platform</title>
  <style>
    :root {
      --primary: #1877f2;
      --primary-hover: #0d5dcc;
      --bg: #f0f2f5;
      --surface: #ffffff;
      --text: #222222;
      --text-muted: #65676b;
      --border: #e4e6eb;
      --success: #24b47e;
      --danger: #fa3e3e;
      --warning: #f5a623;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background: var(--bg);
      color: var(--text);
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
    }

    /* Platform Header Navbar */
    .navbar {
      width: 100%;
      max-width: 900px;
      background: var(--surface);
      padding: 15px 25px;
      border-radius: 12px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.08);
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .brand {
      font-size: 20px;
      font-weight: 800;
      color: var(--primary);
      letter-spacing: 0.5px;
    }

    .view-toggle-btn {
      background: #242526;
      color: #fff;
      border: none;
      padding: 8px 16px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 14px;
      font-weight: 600;
      transition: opacity 0.2s;
    }

    .view-toggle-btn:hover {
      opacity: 0.9;
    }

    /* App Shell Container */
    .app-container {
      width: 100%;
      max-width: 900px;
      background: var(--surface);
      border-radius: 16px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      padding: 30px;
      position: relative;
    }

    .screen {
      display: none;
    }

    .screen.active {
      display: block;
    }

    h1, h2, h3 {
      margin-bottom: 15px;
    }

    p {
      color: var(--text-muted);
      margin-bottom: 20px;
      line-height: 1.5;
    }

    /* Global UI Elements */
    .btn {
      width: 100%;
      padding: 14px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      transition: background 0.2s;
      margin-bottom: 12px;
    }

    .btn-primary { background: var(--primary); color: white; }
    .btn-primary:hover { background: var(--primary-hover); }
    
    .btn-success { background: var(--success); color: white; }
    .btn-success:hover { opacity: 0.9; }

    .btn-outline { background: transparent; border: 1px solid var(--border); color: var(--text); }
    .btn-outline:hover { background: var(--bg); }

    .input-field {
      width: 100%;
      padding: 12px;
      border: 1px solid var(--border);
      border-radius: 8px;
      margin-bottom: 15px;
      font-size: 16px;
      outline: none;
    }

    .input-field:focus {
      border-color: var(--primary);
    }

    /* Badges & Metric Cards */
    .metric-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      margin-bottom: 25px;
    }

    .metric-card {
      background: var(--bg);
      padding: 15px;
      border-radius: 10px;
      text-align: center;
      border: 1px solid var(--border);
    }

    .metric-val {
      font-size: 24px;
      font-weight: 700;
      color: var(--text);
      margin-top: 5px;
    }

    /* Quiz Styling */
    .progress-container {
      background: var(--border);
      height: 8px;
      border-radius: 4px;
      margin-bottom: 20px;
      overflow: hidden;
    }

    .progress-bar {
      background: var(--primary);
      width: 0%;
      height: 100%;
      transition: width 0.3s ease;
    }

    .quiz-meta {
      display: flex;
      justify-content: space-between;
      font-weight: bold;
      margin-bottom: 15px;
    }

    .timer-badge {
      background: #ffebe9;
      color: var(--danger);
      padding: 4px 10px;
      border-radius: 4px;
    }

    .answer-option {
      background: var(--bg);
      color: var(--text);
      text-align: left;
      border: 1px solid var(--border);
    }

    .answer-option:hover {
      background: var(--border);
    }

    /* Table / Admin Roster Styles */
    .table-responsive {
      overflow-x: auto;
      margin-top: 15px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
      font-size: 14px;
    }

    th, td {
      padding: 12px;
      border-bottom: 1px solid var(--border);
    }

    th {
      background: var(--bg);
      color: var(--text-muted);
      font-weight: 600;
    }

    .status-badge {
      padding: 4px 8px;
      border-radius: 4px;
      font-size: 12px;
      font-weight: bold;
    }

    .status-paid { background: #e3fcef; color: var(--success); }
    .status-pending { background: #fff3cd; color: var(--warning); }
    .status-unpaid { background: #ffebe9; color: var(--danger); }

    .action-btn {
      padding: 4px 8px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 12px;
      font-weight: bold;
    }

    /* Modal Styling for Login Protection */
    .modal-overlay {
      position: fixed;
      top: 0; left: 0; right: 0; bottom: 0;
      background: rgba(0,0,0,0.5);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 1000;
      visibility: hidden;
      opacity: 0;
      transition: visibility 0s, opacity 0.2s;
    }
    .modal-overlay.active {
      visibility: visible;
      opacity: 1;
    }
    .modal-content {
      background: white;
      padding: 30px;
      border-radius: 12px;
      max-width: 400px;
      width: 90%;
      box-shadow: 0 4px 20px rgba(0,0,0,0.25);
    }
  </style>
</head>
<body>

  <!-- Navigation Hub -->
  <div class="navbar">
    <div class="brand">SURVEY-EARN Pro</div>
    <button class="view-toggle-btn" id="toggleViewBtn" onclick="handleAdminPanelAccess()">Admin Panel Access</button>
  </div>

  <div class="app-container">

    <!-- USER SEGMENT -->
    <div id="userSegment" class="segment-wrapper">
      
      <!-- SCREEN 1: Welcome & Authentication / Portal Gateway -->
      <div id="scrAuth" class="screen active">
        <h2>Create Survey Account</h2>
        <p>Join thousands getting paid for providing consumer insights. New accounts require a standard verification fee configuration.</p>
        
        <input type="text" id="regName" class="input-field" placeholder="Full Name">
        <input type="email" id="regEmail" class="input-field" placeholder="Email Address">
        
        <div style="background: #eaf3ff; padding: 15px; border-radius: 8px; margin-bottom: 20px; font-size: 14px; color: #0056b3; font-weight: 500;">
          ⚠️ Mandatory Account Activation Fee: <strong>KSh 130</strong>
        </div>

        <button class="btn btn-primary" onclick="processRegistration()">Pay Registration Fee & Start</button>
      </div>

      <!-- SCREEN 2: User Home Dashboard -->
      <div id="scrUserHome" class="screen">
        <h2>Welcome Back, <span id="lblUserName">User</span>!</h2>
        <p>Your subscription is active. Complete available market surveys below to request real-time balance payouts.</p>

        <div class="metric-grid">
          <div class="metric-card">
            <div>Survey Wallet Balance</div>
            <div class="metric-val" style="color: var(--success);" id="lblUserBalance">KSh 0.00</div>
          </div>
          <div class="metric-card">
            <div>Total Points Accrued</div>
            <div class="metric-val" id="lblUserPoints">0</div>
          </div>
        </div>

        <div style="border-top: 1px solid var(--border); padding-top: 20px;">
          <h3>Available Tasks</h3>
          <p>Task #204: Global Consumer Preferences Survey (Worth 50 Points / KSh 500 potential payout)</p>
          <button class="btn btn-success" onclick="startSurveyProcess()">Launch Survey Workspace</button>
          <button class="btn btn-outline" id="btnRequestPayout" onclick="requestPayoutPayout()">Withdraw Balance to MPESA</button>
        </div>
      </div>

      <!-- SCREEN 3: Quiz Workspace Engine -->
      <div id="scrQuiz" class="screen">
        <div class="progress-container">
          <div id="quizProgressBar" class="progress-bar"></div>
        </div>
        
        <div class="quiz-meta">
          <span id="lblProgressTracker">Question 1 of 5</span>
          <span class="timer-badge">⏱️ <span id="lblTimerCount">15</span>s</span>
        </div>

        <h3 id="lblQuestionText" style="margin-bottom: 20px;">Loading question content...</h3>

        <button class="btn answer-option" onclick="submitUserAnswer(0)" id="opt0"></button>
        <button class="btn answer-option" onclick="submitUserAnswer(1)" id="opt1"></button>
        <button class="btn answer-option" onclick="submitUserAnswer(2)" id="opt2"></button>
        <button class="btn answer-option" onclick="submitUserAnswer(3)" id="opt3"></button>
      </div>

      <!-- SCREEN 4: Quiz Completion Summary -->
      <div id="scrResult" class="screen">
        <h2 style="color: var(--success);">Survey Set Finalized! 🎉</h2>
        <p>Your response configurations have been indexed by our corporate data consumers.</p>

        <div class="metric-grid">
          <div class="metric-card">
            <div>Points Earned</div>
            <div class="metric-val" id="lblEarnedPoints">+0</div>
          </div>
          <div class="metric-card">
            <div>Cash Added</div>
            <div class="metric-val" id="lblEarnedCash" style="color: var(--success);">KSh 0</div>
          </div>
        </div>

        <button class="btn btn-primary" onclick="returnToDashboardHome()">Return to Dashboard</button>
      </div>

    </div>


    <!-- ADMIN SEGMENT -->

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Premium Paid Survey & Admin Platform</title>
  <style>
    :root {
      --primary: #1877f2;
      --primary-hover: #0d5dcc;
      --bg: #f0f2f5;
      --surface: #ffffff;
      --text: #222222;
      --text-muted: #65676b;
      --border: #e4e6eb;
      --success: #24b47e;
      --danger: #fa3e3e;
      --warning: #f5a623;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background: var(--bg);
      color: var(--text);
      padding: 20px;
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
    }

    /* Platform Header Navbar */
    .navbar {
      width: 100%;
      max-width: 900px;
      background: var(--surface);
      padding: 15px 25px;
      border-radius: 12px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.08);
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .brand {
      font-size: 20px;
      font-weight: 800;
      color: var(--primary);
      letter-spacing: 0.5px;
    }

    .view-toggle-btn {
      background: #242526;
      color: #fff;
      border: none;
      padding: 8px 16px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 14px;
      font-weight: 600;
      transition: opacity 0.2s;
    }

    .view-toggle-btn:hover {
      opacity: 0.9;
    }

    /* App Shell Container */
    .app-container {
      width: 100%;
      max-width: 900px;
      background: var(--surface);
      border-radius: 16px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      padding: 30px;
      position: relative;
    }

    .screen {
      display: none;
    }

    .screen.active {
      display: block;
    }

    h1, h2, h3 {
      margin-bottom: 15px;
    }

    p {
      color: var(--text-muted);
      margin-bottom: 20px;
      line-height: 1.5;
    }

    /* Global UI Elements */
    .btn {
      width: 100%;
      padding: 14px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      transition: background 0.2s;
      margin-bottom: 12px;
    }

    .btn-primary { background: var(--primary); color: white; }
    .btn-primary:hover { background: var(--primary-hover); }
    
    .btn-success { background: var(--success); color: white; }
    .btn-success:hover { opacity: 0.9; }

    .btn-outline { background: transparent; border: 1px solid var(--border); color: var(--text); }
    .btn-outline:hover { background: var(--bg); }

    .input-field {
      width: 100%;
      padding: 12px;
      border: 1px solid var(--border);
      border-radius: 8px;
      margin-bottom: 15px;
      font-size: 16px;
      outline: none;
    }

    .input-field:focus {
      border-color: var(--primary);
    }

    /* Badges & Metric Cards */
    .metric-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 15px;
      margin-bottom: 25px;
    }

    .metric-card {
      background: var(--bg);
      padding: 15px;
      border-radius: 10px;
      text-align: center;
      border: 1px solid var(--border);
    }

    .metric-val {
      font-size: 24px;
      font-weight: 700;
      color: var(--text);
      margin-top: 5px;
    }

    /* Quiz Styling */
    .progress-container {
      background: var(--border);
      height: 8px;
      border-radius: 4px;
      margin-bottom: 20px;
      overflow: hidden;
    }

    .progress-bar {
      background: var(--primary);
      width: 0%;
      height: 100%;
      transition: width 0.3s ease;
    }

    .quiz-meta {
      display: flex;
      justify-content: space-between;
      font-weight: bold;
      margin-bottom: 15px;
    }

    .timer-badge {
      background: #ffebe9;
      color: var(--danger);
      padding: 4px 10px;
      border-radius: 4px;
    }

    .answer-option {
      background: var(--bg);
      color: var(--text);
      text-align: left;
      border: 1px solid var(--border);
    }

    .answer-option:hover {
      background: var(--border);
    }

    /* Table / Admin Roster Styles */
    .table-responsive {
      overflow-x: auto;
      margin-top: 15px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
      font-size: 14px;
    }

    th, td {
      padding: 12px;
      border-bottom: 1px solid var(--border);
    }

    th {
      background: var(--bg);
      color: var(--text-muted);
      font-weight: 600;
    }

    .status-badge {
      padding: 4px 8px;
      border-radius: 4px;
      font-size: 12px;
      font-weight: bold;
    }

    .status-paid { background: #e3fcef; color: var(--success); }
    .status-pending { background: #fff3cd; color: var(--warning); }
    .status-unpaid { background: #ffebe9; color: var(--danger); }

    .action-btn {
      padding: 4px 8px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 12px;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <!-- Navigation Hub -->
  <div class="navbar">
    <div class="brand">SURVEY-EARN Pro</div>
    <button class="view-toggle-btn" id="toggleViewBtn" onclick="togglePlatformView()">Switch to Admin View</button>
  </div>

  <div class="app-container">

    <!-- USER SEGMENT -->
    <div id="userSegment" class="segment-wrapper">
      
      <!-- SCREEN 1: Welcome & Authentication / Portal Gateway -->
      <div id="scrAuth" class="screen active">
        <h2>Create Survey Account</h2>
        <p>Join thousands getting paid for providing consumer insights. New accounts require a standard verification fee configuration.</p>
        
        <input type="text" id="regName" class="input-field" placeholder="Full Name">
        <input type="email" id="regEmail" class="input-field" placeholder="Email Address">
        
        <div style="background: #eaf3ff; padding: 15px; border-radius: 8px; margin-bottom: 20px; font-size: 14px; color: #0056b3; font-weight: 500;">
          ⚠️ Mandatory Account Activation Fee: <strong>KSh 130</strong>
        </div>

        <button class="btn btn-primary" onclick="processRegistration()">Pay Registration Fee & Start</button>
      </div>

      <!-- SCREEN 2: User Home Dashboard -->
      <div id="scrUserHome" class="screen">
        <h2>Welcome Back, <span id="lblUserName">User</span>!</h2>
        <p>Your subscription is active. Complete available market surveys below to request real-time balance payouts.</p>

        <div class="metric-grid">
          <div class="metric-card">
            <div>Survey Wallet Balance</div>
            <div class="metric-val" style="color: var(--success);" id="lblUserBalance">KSh 0.00</div>
          </div>
          <div class="metric-card">
            <div>Total Points Accrued</div>
            <div class="metric-val" id="lblUserPoints">0</div>
          </div>
        </div>

        <div style="border-top: 1px solid var(--border); padding-top: 20px;">
          <h3>Available Tasks</h3>
          <p>Task #204: Global Consumer Preferences Survey (Worth 50 Points / KSh 500 potential payout)</p>
          <button class="btn btn-success" onclick="startSurveyProcess()">Launch Survey Workspace</button>
          <button class="btn btn-outline" id="btnRequestPayout" onclick="requestPayoutPayout()">Withdraw Balance to MPESA</button>
        </div>
      </div>

      <!-- SCREEN 3: Quiz Workspace Engine -->
      <div id="scrQuiz" class="screen">
        <div class="progress-container">
          <div id="quizProgressBar" class="progress-bar"></div>
        </div>
        
        <div class="quiz-meta">
          <span id="lblProgressTracker">Question 1 of 5</span>
          <span class="timer-badge">⏱️ <span id="lblTimerCount">15</span>s</span>
        </div>

        <h3 id="lblQuestionText" style="margin-bottom: 20px;">Loading question content...</h3>

        <button class="btn answer-option" onclick="submitUserAnswer(0)" id="opt0"></button>
        <button class="btn answer-option" onclick="submitUserAnswer(1)" id="opt1"></button>
        <button class="btn answer-option" onclick="submitUserAnswer(2)" id="opt2"></button>
        <button class="btn answer-option" onclick="submitUserAnswer(3)" id="opt3"></button>
      </div>

      <!-- SCREEN 4: Quiz Completion Summary -->
      <div id="scrResult" class="screen">
        <h2 style="color: var(--success);">Survey Set Finalized! 🎉</h2>
        <p>Your response configurations have been indexed by our corporate data consumers.</p>

        <div class="metric-grid">
          <div class="metric-card">
            <div>Points Earned</div>
            <div class="metric-val" id="lblEarnedPoints">+0</div>
          </div>
          <div class="metric-card">
            <div>Cash Added</div>
            <div class="metric-val" id="lblEarnedCash" style="color: var(--success);">KSh 0</div>
          </div>
        </div>

        <button class="btn btn-primary" onclick="returnToDashboardHome()">Return to Dashboard</button>
      </div>

    </div>


    <!-- ADMIN SEGMENT -->
    <div id="adminSegment" class="segment-wrapper" style="display: none;">
      <h2>System Management Dashboard</h2>
      <p>Real-time accounting ledger, registration audit parameters, and client transaction pipelines.</p>

      <div class="metric-grid">
        <div class="metric-card">
          <div>Registration Revenue</div>
          <div class="metric-val" style="color: var(--primary);" id="lblAdminRegRev">KSh 0.00</div>
        </div>
        <div class="metric-card">
          <div>Total Payouts Handled</div>
          <div class="metric-val" style="color: var(--danger);" id="lblAdminPaidOut">KSh 0.00</div>
        </div>
