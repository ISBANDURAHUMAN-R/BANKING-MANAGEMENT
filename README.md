<p align="center">
  <img src="assets/banner.png" alt="BANKING-MANAGEMENT Banner" width="100%">
</p>

# ◈ Banking Management System

[![CI](https://github.com/ISBANDURAHUMAN-R/Banking-Management-System/actions/workflows/ci.yml/badge.svg)](https://github.com/ISBANDURAHUMAN-R/Banking-Management-System/actions/workflows/ci.yml)

## ◆ About the Project
The Banking Management System is a command-line financial management program developed in Python. It provides core personal banking operations including account creation, money deposits, withdrawals with overdraft checks, balance inquiries, and historical transaction logging using persistent CSV storage.

## ❖ Key Features
- Bank account registration and initialization with unique account numbers.
- Secure deposit and withdrawal processing with balance validation.
- Real-time balance inquiry for registered accounts.
- Automated ledger recording storing transaction logs in `transactions.csv` and account states in `accounts.csv`.
- Menu-driven console interface designed for terminal navigation.

## ◆ System Architecture
```mermaid
graph TD
    subgraph CLI ["Terminal User Interface"]
        Menu["Interactive Menu Loop"] --> Selection{"Operation Choice"}
        Selection -- 1 --> OpCreate["Create Account"]
        Selection -- 2 --> OpDeposit["Deposit Funds"]
        Selection -- 3 --> OpWithdraw["Withdraw Funds"]
        Selection -- 4 --> OpBalance["Check Balance"]
        Selection -- 5 --> OpHistory["Transaction History"]
    end

    subgraph CoreEngine ["Banking Business Logic"]
        OpCreate --> ValAcct["Unique Account &<br/>Initial Balance Check"]
        OpDeposit --> ValDep["Positive Amount<br/>Validator"]
        OpWithdraw --> ValOverdraft{"Balance >=<br/>Withdrawal?"}
        ValOverdraft -- No --> ErrFunds["Insufficient Funds<br/>Alert"]
        ValOverdraft -- Yes --> ExecTrans["Apply Balance Delta"]
        OpBalance --> QueryAcct["Account Lookup"]
        OpHistory --> QueryTrans["Filter Transaction<br/>Ledger"]
    end

    subgraph LedgerStorage ["Persistent CSV Storage"]
        ValAcct --> AcctCSV[("accounts.csv<br/>AccountNo, Name, Balance")]
        ExecTrans --> AcctCSV
        ExecTrans --> TransCSV[("transactions.csv<br/>AccountNo, Type, Amount")]
        QueryAcct --> AcctCSV
        QueryTrans --> TransCSV
    end
```

## ⬢ Technologies Used
- Python 3
- Python Standard Library (`csv`, `os`, `datetime`)

## § Requirements
- Python 3.8 or higher

## ▲ Installation & Execution
```bash
# Run the application
python main.py
```

## ※ Developer
Developer: ISBANDU RAHUMAN R  
GitHub: https://github.com/ISBANDURAHUMAN-R
