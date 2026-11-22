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
    subgraph CLI ["&nbsp; Terminal User Interface &nbsp;"]
        Menu["&nbsp; Interactive &nbsp;<br/>&nbsp; Menu Loop &nbsp;"] --> Selection{"&nbsp; Operation? &nbsp;"}
        Selection -- 1 --> OpCreate["&nbsp; Create Account &nbsp;"]
        Selection -- 2 --> OpDeposit["&nbsp; Deposit Funds &nbsp;"]
        Selection -- 3 --> OpWithdraw["&nbsp; Withdraw Funds &nbsp;"]
        Selection -- 4 --> OpBalance["&nbsp; Check Balance &nbsp;"]
        Selection -- 5 --> OpHistory["&nbsp; Transaction &nbsp;<br/>&nbsp; History &nbsp;"]
    end

    subgraph CoreEngine ["&nbsp; Banking Business Logic &nbsp;"]
        OpCreate --> ValAcct["&nbsp; Account &amp; Balance &nbsp;<br/>&nbsp; Validator &nbsp;"]
        OpDeposit --> ValDep["&nbsp; Positive Amount &nbsp;<br/>&nbsp; Validator &nbsp;"]
        OpWithdraw --> ValOverdraft{"&nbsp; Balance &gt;= &nbsp;<br/>&nbsp; Withdrawal? &nbsp;"}
        ValOverdraft -- No --> ErrFunds["&nbsp; Insufficient &nbsp;<br/>&nbsp; Funds Alert &nbsp;"]
        ValOverdraft -- Yes --> ExecTrans["&nbsp; Apply Balance &nbsp;<br/>&nbsp; Delta &nbsp;"]
        OpBalance --> QueryAcct["&nbsp; Account &nbsp;<br/>&nbsp; Lookup &nbsp;"]
        OpHistory --> QueryTrans["&nbsp; Filter Transaction &nbsp;<br/>&nbsp; Ledger &nbsp;"]
    end

    subgraph LedgerStorage ["&nbsp; Persistent CSV Storage &nbsp;"]
        ValAcct --> AcctCSV[("&nbsp; accounts.csv &nbsp;<br/>&nbsp; AcctNo, Name, Bal &nbsp;")]
        ExecTrans --> AcctCSV
        ExecTrans --> TransCSV[("&nbsp; transactions.csv &nbsp;<br/>&nbsp; AcctNo, Type, Amt &nbsp;")]
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
