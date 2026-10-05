# my-new-javascript-app
<!DOCTYPE html>
<html>
<head>
    <title>ATM Banking</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: Arial, Helvetica, sans-serif;
        }

        body {
            min-height: 100vh;
            background:
                radial-gradient(circle at top, #26384f, #0b1420 70%);
            display: flex;
            justify-content: center;
            align-items: center;
            color: #1b2735;
        }

        /* =========================
           LOGIN
        ========================= */

        .login-container {
            width: 410px;
            background: #ffffff;
            padding: 45px;
            border-radius: 18px;
            box-shadow:
                0 25px 70px rgba(0, 0, 0, 0.45);
            text-align: center;
            animation: fadeIn 0.6s ease;
        }

        .bank-icon {
            width: 78px;
            height: 78px;
            margin: auto;
            border-radius: 50%;
            background: linear-gradient(145deg, #1c3b5a, #0c2035);
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 21px;
            font-weight: bold;
            letter-spacing: 1px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.2);
        }

        .login-container h1 {
            margin-top: 18px;
            font-size: 29px;
            letter-spacing: 1px;
            color: #142c43;
        }

        .secure-login {
            margin-top: 7px;
            margin-bottom: 30px;
            font-size: 12px;
            letter-spacing: 3px;
            color: #728092;
        }

        .input-box {
            text-align: left;
            margin-bottom: 18px;
        }

        .input-box label {
            display: block;
            margin-bottom: 7px;
            font-size: 12px;
            font-weight: bold;
            letter-spacing: 1px;
            color: #4d5d6d;
        }

        input {
            width: 100%;
            padding: 14px;
            border: 1px solid #d6dce2;
            border-radius: 9px;
            font-size: 15px;
            outline: none;
            transition: 0.25s;
        }

        input:focus {
            border-color: #1c527d;
            box-shadow: 0 0 0 3px rgba(28,82,125,0.1);
        }

        .login-button {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 9px;
            background: linear-gradient(135deg, #17466b, #102d48);
            color: white;
            font-size: 15px;
            font-weight: bold;
            letter-spacing: 1px;
            cursor: pointer;
            transition: 0.25s;
        }

        .login-button:hover {
            transform: translateY(-2px);
            box-shadow: 0 7px 18px rgba(16,45,72,0.3);
        }

        #loginMessage {
            color: #c62828;
            font-size: 13px;
            margin-top: 15px;
        }

        .security-note {
            margin-top: 25px;
            color: #8995a1;
            font-size: 11px;
        }


        /* =========================
           ATM DASHBOARD
        ========================= */

        .atm-container {
            display: none;
            width: 920px;
            background: #f3f5f7;
            border-radius: 18px;
            overflow: hidden;
            box-shadow:
                0 30px 80px rgba(0,0,0,0.5);
            animation: fadeIn 0.5s ease;
        }


        /* HEADER */

        .header {
            background: linear-gradient(135deg, #173d5c, #0e263d);
            color: white;
            padding: 25px 35px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .header h1 {
            font-size: 24px;
            letter-spacing: 2px;
        }

        .header-right {
            text-align: right;
        }

        .header-right strong {
            display: block;
            font-size: 12px;
            letter-spacing: 1px;
        }

        .header-right span {
            font-size: 11px;
            color: #b7c5d2;
        }


        /* CONTENT */

        .content {
            padding: 35px;
        }

        .welcome {
            margin-bottom: 25px;
        }

        .welcome h2 {
            font-size: 21px;
            color: #173d5c;
            margin-bottom: 6px;
        }

        .welcome p {
            font-size: 14px;
            color: #7b8792;
        }


        /* BALANCE */

        .balance-card {
            background:
                linear-gradient(135deg, #173d5c, #0c243b);
            color: white;
            padding: 30px;
            border-radius: 14px;
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
            box-shadow:
                0 10px 25px rgba(14,38,61,0.25);
        }

        .balance-card::after {
            content: "";
            position: absolute;
            width: 180px;
            height: 180px;
            border-radius: 50%;
            background: rgba(255,255,255,0.04);
            right: -60px;
            top: -70px;
        }

        .balance-label {
            font-size: 12px;
            letter-spacing: 2px;
            color: #b7c9d8;
            margin-bottom: 10px;
        }

        .balance {
            font-size: 40px;
            font-weight: bold;
            letter-spacing: 1px;
        }


        /* SERVICES */

        .menu-title {
            color: #173d5c;
            font-size: 17px;
            margin-bottom: 15px;
        }

        .buttons {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 14px;
        }

        .atm-button {
            padding: 19px;
            background: white;
            border: 1px solid #dce1e5;
            border-radius: 11px;
            color: #173d5c;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.25s ease;
        }

        .atm-button:hover {
            background: #173d5c;
            color: white;
            transform: translateY(-3px);
            box-shadow: 0 8px 18px rgba(23,61,92,0.2);
        }


        /* TRANSACTION AREA */

        .transaction-box {
            display: none;
            margin-top: 20px;
            padding: 20px;
            background: white;
            border-radius: 11px;
            border: 1px solid #dce1e5;
            animation: slideDown 0.3s ease;
        }

        .transaction-box h3 {
            color: #173d5c;
            margin-bottom: 12px;
        }

        .transaction-box input {
            margin-bottom: 10px;
        }

        .confirm-button {
            width: 100%;
            padding: 13px;
            border: none;
            border-radius: 8px;
            background: #218739;
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: 0.2s;
        }

        .confirm-button:hover {
            background: #17692a;
        }


        /* MESSAGE */

        #message {
            margin-top: 20px;
            padding: 15px;
            background: white;
            border-radius: 9px;
            border: 1px solid #dce1e5;
            text-align: center;
            color: #4b5865;
            min-height: 48px;
            transition: 0.3s;
        }


        /* LOGOUT */

        .logout {
            width: 100%;
            margin-top: 18px;
            padding: 14px;
            border: none;
            border-radius: 8px;
            background: #a52a24;
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: 0.25s;
        }

        .logout:hover {
            background: #81201b;
        }


        /* ANIMATIONS */

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(15px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-8px);
            }

            to {
                opacity: 1;
                transform: translateY(0);
            }
        }


        /* MOBILE */

        @media (max-width: 700px) {

            .login-container {
                width: 90%;
            }

            .atm-container {
                width: 95%;
            }

            .buttons {
                grid-template-columns: 1fr;
            }

            .content {
                padding: 20px;
            }

            .header {
                padding: 20px;
            }
        }

    </style>
</head>


<body>


    <!-- =========================
         LOGIN
    ========================== -->

    <div class="login-container" id="loginPage">

        <div class="bank-icon">
            ATM
        </div>

        <h1>ATM BANKING</h1>

        <p class="secure-login">
            SECURE LOGIN
        </p>


        <div class="input-box">

            <label>USERNAME</label>

            <input
                type="text"
                id="username"
                placeholder="Enter username"
            >

        </div>


        <div class="input-box">

            <label>PASSWORD</label>

            <input
                type="password"
                id="password"
                placeholder="Enter password"
            >

        </div>


        <button
            class="login-button"
            onclick="login()"
        >
            LOGIN
        </button>


        <p id="loginMessage"></p>

        <p class="security-note">
            🔒 Secure banking session
        </p>

    </div>



    <!-- =========================
         ATM DASHBOARD
    ========================== -->

    <div class="atm-container" id="atmMenu">

        <div class="header">

            <h1>ATM BANKING</h1>

            <div class="header-right">

                <strong>SECURE ATM SYSTEM</strong>

                <span>Banking Services</span>

            </div>

        </div>


        <div class="content">


            <div class="welcome">

                <h2>
                    Welcome, <span id="displayUsername"></span>
                </h2>

                <p>
                    Select a banking service below.
                </p>

            </div>


            <!-- BALANCE -->

            <div class="balance-card">

                <div class="balance-label">
                    AVAILABLE SAVINGS
                </div>

                <div class="balance">
                    ₱<span id="balance">1,000.00</span>
                </div>

            </div>


            <!-- SERVICES -->

            <h3 class="menu-title">
                BANKING SERVICES
            </h3>


            <div class="buttons">

                <button
                    class="atm-button"
                    onclick="showDeposit()"
                >
                    💰 &nbsp; DEPOSIT
                </button>


                <button
                    class="atm-button"
                    onclick="showWithdraw()"
                >
                    💸 &nbsp; WITHDRAW
                </button>


                <button
                    class="atm-button"
                    onclick="checkSavings()"
                >
                    💳 &nbsp; CHECK SAVINGS
                </button>


                <button
                    class="atm-button"
                    onclick="clearMessage()"
                >
                    ↻ &nbsp; CLEAR
                </button>

            </div>


            <!-- TRANSACTION BOX -->

            <div
                class="transaction-box"
                id="transactionBox"
            >

                <h3 id="transactionTitle">
                    Transaction
                </h3>

                <input
                    type="number"
                    id="transactionAmount"
                    placeholder="Enter amount"
                    min="1"
                >

                <button
                    class="confirm-button"
                    onclick="confirmTransaction()"
                >
                    CONFIRM TRANSACTION
                </button>

            </div>


            <!-- MESSAGE -->

            <div id="message">
                Select a banking service above.
            </div>


            <!-- LOGOUT -->

            <button
                class="logout"
                onclick="logout()"
            >
                LOGOUT
            </button>

        </div>

    </div>



    <script>

        // =========================
        // LOGIN INFORMATION
        // =========================

        let correctUsername = "Karli";
        let correctPassword = "143";


        // STARTING SAVINGS

        let savings = 1000;


        // TRANSACTION TYPE

        let transactionType = "";



        // =========================
        // LOGIN
        // =========================

        function login() {

            let username =
                document.getElementById("username").value;

            let password =
                document.getElementById("password").value;


            if (
                username === correctUsername &&
                password === correctPassword
            ) {

                document.getElementById("loginPage")
                    .style.display = "none";

                document.getElementById("atmMenu")
                    .style.display = "block";

                document.getElementById("displayUsername")
                    .textContent = username;

                updateBalance();

            }

            else {

                document.getElementById("loginMessage")
                    .textContent =
                    "Incorrect username or password.";

            }

        }



        // =========================
        // SHOW DEPOSIT
        // =========================

        function showDeposit() {

            transactionType = "deposit";

            document.getElementById("transactionTitle")
                .textContent =
                "Deposit Money";

            document.getElementById("transactionAmount")
                .value = "";

            document.getElementById("transactionBox")
                .style.display = "block";

        }



        // =========================
        // SHOW WITHDRAW
        // =========================

        function showWithdraw() {

            transactionType = "withdraw";

            document.getElementById("transactionTitle")
                .textContent =
                "Withdraw Money";

            document.getElementById("transactionAmount")
                .value = "";

            document.getElementById("transactionBox")
                .style.display = "block";

        }



        // =========================
        // CONFIRM TRANSACTION
        // =========================

        function confirmTransaction() {

            let amount =
                Number(
                    document.getElementById(
                        "transactionAmount"
                    ).value
                );


            if (amount <= 0) {

                showMessage(
                    "Please enter a valid amount."
                );

                return;

            }


            // DEPOSIT

            if (transactionType === "deposit") {

                savings = savings + amount;

                updateBalance();

                showMessage(
                    "✓ Deposit successful. ₱" +
                    amount.toFixed(2) +
                    " has been added to your savings."
                );

            }


            // WITHDRAW

            else if (transactionType === "withdraw") {

                if (amount > savings) {

                    showMessage(
                        "✕ Transaction declined. " +
                        "Insufficient savings."
                    );

                    return;

                }


                savings = savings - amount;

                updateBalance();

                showMessage(
                    "✓ Withdrawal successful. ₱" +
                    amount.toFixed(2) +
                    " has been withdrawn."
                );

            }


            document.getElementById("transactionBox")
                .style.display = "none";

        }



        // =========================
        // CHECK SAVINGS
        // =========================

        function checkSavings() {

            showMessage(
                "Your current available savings is ₱" +
                savings.toFixed(2)
            );

        }



        // =========================
        // UPDATE BALANCE
        // =========================

        function updateBalance() {

            document.getElementById("balance")
                .textContent =
                savings.toFixed(2);

        }



        // =========================
        // MESSAGE
        // =========================

        function showMessage(text) {

            document.getElementById("message")
                .textContent = text;

        }



        // =========================
        // CLEAR
        // =========================

        function clearMessage() {

            document.getElementById("transactionBox")
                .style.display = "none";

            document.getElementById("message")
                .textContent =
                "Select a banking service above.";

        }

        // =========================
        // LOGOUT
        // =========================

        function logout() {

            document.getElementById("atmMenu")
                .style.display = "none";

            document.getElementById("loginPage")
                .style.display = "block";

            document.getElementById("username")
                .value = "";

            document.getElementById("password")
                .value = "";

            document.getElementById("loginMessage")
                .textContent = "";

        }

    </script>

</body>
</html>
