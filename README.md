 About the Project:

Ever wondered what happens behind the screen when you slide your card into an ATM? This project answers that question. **ATM Database System** is a relational database design that models the complete backend of a bank ATM, from verifying a customer's identity to recording every rupee that moves in or out of their account.

At its core are two connected tables. The `customers` table holds each account's ID, PIN, name, and live balance, while the `transaction_history` table keeps a timestamped record of every deposit and withdrawal, linked back to the account through a foreign key. Sample data is included, so you can run the script and see the system working within seconds.

 How It Works:

Every operation begins with **PIN verification**: a customer is only granted access when the account ID and PIN match, and the same query returns their balance. **Deposits** instantly update the balance and are written to the transaction log. **Withdrawals** come with built-in **overdraft protection**, so funds are deducted only when the balance can cover the amount, which makes it impossible to withdraw money that isn't there. Finally, a **mini statement** query pulls the five most recent transactions for any account, just like the receipt a real ATM prints.

Highlight: Overdraft-Protected Withdrawal

```sql
UPDATE customers
SET balance = balance - 1500.00
WHERE account_id = 1001
  AND pin = 1234
  AND balance >= 1500.00;
```

One condition in the `WHERE` clause does the work of a safety check, so the balance can never go negative.

## 🚀 Getting Started

Open any PostgreSQL client such as `psql` or pgAdmin, run the script to create the tables and load the sample customers, and then execute each operation to watch the ATM logic in action.

## 🔮 What's Next

Future upgrades could include stored procedures that wrap each operation in a single atomic transaction, hashed PINs for stronger security, and a limit on failed PIN attempts to lock suspicious accounts.

---

<p align="center">⭐ If you found this project useful, consider giving it a star! ⭐</p>
