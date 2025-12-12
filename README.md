# Banking App: Secure Account Manager

A Python-based banking simulation built in Jupyter Notebook. Users can deposit, withdraw, view transactions, and project savings interest — all with real-time input and feedback.

### 🔗 Live Demo
[Explore the banking app](https://your-banking-demo.netlify.app)

### 📄 Features
- Interactive deposit and withdrawal system
- Transaction history with timestamps and unique IDs
- Savings interest projection (1–3 years)
- Account summary and final balance display
- Built with Python 3.11 and Jupyter Notebook

### 📂 Source Notebook
[bank account (1).ipynb](https://github.com/user-attachments/files/24121243/bank.account.1.ipynb)


{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "fa4d32da-5d91-4643-b01c-39073b77c8a1",
   "metadata": {},
   "outputs": [
    {
     "name": "stdin",
     "output_type": "stream",
     "text": [
      "Enter initial deposit for Checking: $ 100\n",
      "Enter initial deposit for Savings: $ 300\n"
     ]
    }
   ],
   "source": [
    "# Simple Banking Application - Setup\n",
    "\n",
    "checking_balance = float(input(\"Enter initial deposit for Checking: $\"))\n",
    "savings_balance = float(input(\"Enter initial deposit for Savings: $\"))\n",
    "interest_rate = 0.04  # 4% per year\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "id": "dcf787f3-789a-42f6-8d62-9c12ff85b184",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Do you want to make a withdrawal?\n",
      "1. Checking\n",
      "2. Savings\n",
      "3. No withdrawal\n"
     ]
    },
    {
     "name": "stdin",
     "output_type": "stream",
     "text": [
      "Choose 1, 2, or 3:  1\n",
      "Enter withdrawal amount from Checking: $ 100\n"
     ]
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "Remaining Checking Balance: $0.00\n"
     ]
    }
   ],
   "source": [
    "print(\"\\nDo you want to make a withdrawal?\")\n",
    "print(\"1. Checking\")\n",
    "print(\"2. Savings\")\n",
    "print(\"3. No withdrawal\")\n",
    "\n",
    "choice = input(\"Choose 1, 2, or 3: \")\n",
    "\n",
    "if choice == \"1\":\n",
    "    amount = float(input(\"Enter withdrawal amount from Checking: $\"))\n",
    "    if amount <= checking_balance:\n",
    "        checking_balance -= amount\n",
    "        print(f\"Remaining Checking Balance: ${checking_balance:.2f}\")\n",
    "    else:\n",
    "        print(\"Insufficient funds in Checking.\")\n",
    "\n",
    "elif choice == \"2\":\n",
    "    amount = float(input(\"Enter withdrawal amount from Savings: $\"))\n",
    "    if amount <= savings_balance:\n",
    "        savings_balance -= amount\n",
    "        print(f\"Remaining Savings Balance: ${savings_balance:.2f}\")\n",
    "    else:\n",
    "        print(\"Insufficient funds in Savings.\")\n",
    "\n",
    "else:\n",
    "    print(\"No withdrawal made.\")\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "id": "5b72f15f-363f-4434-91b0-5c2301dc717e",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Savings Projection with 4% Interest:\n",
      "Year 1: $312.00\n",
      "Year 2: $324.48\n",
      "Year 3: $337.46\n"
     ]
    }
   ],
   "source": [
    "print(\"\\nSavings Projection with 4% Interest:\")\n",
    "for year in range(1, 4):\n",
    "    future = savings_balance * ((1 + interest_rate) ** year)\n",
    "    print(f\"Year {year}: ${future:.2f}\")\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "id": "42c0ab6f-afbe-4750-b236-3e3d397fd92f",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Final Account Balances:\n",
      "Checking: $0.00\n",
      "Savings:  $300.00\n"
     ]
    }
   ],
   "source": [
    "print(\"\\nFinal Account Balances:\")\n",
    "print(f\"Checking: ${checking_balance:.2f}\")\n",
    "print(f\"Savings:  ${savings_balance:.2f}\")\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "id": "ce3dde81-f2c1-4cb0-aaba-06bffa036de1",
   "metadata": {},
   "outputs": [
    {
     "name": "stdin",
     "output_type": "stream",
     "text": [
      "Enter initial deposit for Checking: $ 700\n",
      "Enter initial deposit for Savings: $ 500\n"
     ]
    }
   ],
   "source": [
    "import datetime, random, string\n",
    "\n",
    "def generate_transaction_id():\n",
    "    return \"BA10-\" + ''.join(random.choices(string.ascii_uppercase, k=5))\n",
    "\n",
    "def get_timestamp():\n",
    "    now = datetime.datetime.now()\n",
    "    return now.strftime(\"%m/%d/%Y %I:%M:%S %p\")\n",
    "\n",
    "# Starting balances\n",
    "checking_balance = float(input(\"Enter initial deposit for Checking: $\"))\n",
    "savings_balance = float(input(\"Enter initial deposit for Savings: $\"))\n",
    "\n",
    "interest_rate = 0.04\n",
    "transactions = []\n",
    "\n",
    "# Record initial deposits\n",
    "for account, amount in [(\"Checking\", checking_balance), (\"Savings\", savings_balance)]:\n",
    "    transactions.append({\n",
    "        \"ID\": generate_transaction_id(),\n",
    "        \"Date\": get_timestamp(),\n",
    "        \"Type\": \"Deposit\",\n",
    "        \"Account\": account,\n",
    "        \"Amount\": amount\n",
    "    })\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "id": "ffc6ae05-9a08-423a-b9f7-e0586105c6a3",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "--- Main Menu ---\n",
      "1. Deposit\n",
      "2. Withdrawal\n",
      "3. View Transactions\n",
      "4. Account Summary\n",
      "5. Savings Interest (1–3 years)\n",
      "6. Exit\n"
     ]
    },
    {
     "name": "stdin",
     "output_type": "stream",
     "text": [
      "Choose 1-6:  6\n"
     ]
    },
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "\n",
      "Final Balances:\n",
      "Checking: $700.00\n",
      "Savings:  $500.00\n",
      "Goodbye!\n"
     ]
    }
   ],
   "source": [
    "\n",
    "while True:\n",
    "    print(\"\\n--- Main Menu ---\")\n",
    "    print(\"1. Deposit\")\n",
    "    print(\"2. Withdrawal\")\n",
    "    print(\"3. View Transactions\")\n",
    "    print(\"4. Account Summary\")\n",
    "    print(\"5. Savings Interest (1–3 years)\")\n",
    "    print(\"6. Exit\")\n",
    "\n",
    "    choice = input(\"Choose 1-6: \")\n",
    "\n",
    "    if choice == \"1\":  # Deposit\n",
    "        acc = input(\"Deposit to (C)hecking or (S)avings? \").lower()\n",
    "        amount = float(input(\"Enter deposit amount: $\"))\n",
    "        if acc.startswith(\"c\"):\n",
    "            checking_balance += amount\n",
    "            account = \"Checking\"\n",
    "        else:\n",
    "            savings_balance += amount\n",
    "            account = \"Savings\"\n",
    "        transactions.append({\n",
    "            \"ID\": generate_transaction_id(),\n",
    "            \"Date\": get_timestamp(),\n",
    "            \"Type\": \"Deposit\",\n",
    "            \"Account\": account,\n",
    "            \"Amount\": amount\n",
    "        })\n",
    "        print(f\"Deposited ${amount:.2f} into {account}.\")\n",
    "\n",
    "    elif choice == \"2\":  # Withdrawal\n",
    "        acc = input(\"Withdraw from (C)hecking or (S)avings? \").lower()\n",
    "        amount = float(input(\"Enter withdrawal amount: $\"))\n",
    "        if acc.startswith(\"c\"):\n",
    "            if amount <= checking_balance:\n",
    "                checking_balance -= amount\n",
    "                account = \"Checking\"\n",
    "                transactions.append({\n",
    "                    \"ID\": generate_transaction_id(),\n",
    "                    \"Date\": get_timestamp(),\n",
    "                    \"Type\": \"Withdrawal\",\n",
    "                    \"Account\": account,\n",
    "                    \"Amount\": amount\n",
    "                })\n",
    "                print(f\"Withdrew ${amount:.2f} from Checking.\")\n",
    "            else:\n",
    "                print(\"Insufficient funds in Checking.\")\n",
    "        else:\n",
    "            if amount <= savings_balance:\n",
    "                savings_balance -= amount\n",
    "                account = \"Savings\"\n",
    "                transactions.append({\n",
    "                    \"ID\": generate_transaction_id(),\n",
    "                    \"Date\": get_timestamp(),\n",
    "                    \"Type\": \"Withdrawal\",\n",
    "                    \"Account\": account,\n",
    "                    \"Amount\": amount\n",
    "                })\n",
    "                print(f\"Withdrew ${amount:.2f} from Savings.\")\n",
    "            else:\n",
    "                print(\"Insufficient funds in Savings.\")\n",
    "\n",
    "    elif choice == \"3\":  # Transactions\n",
    "        print(\"\\nTransaction History:\")\n",
    "        for t in transactions:\n",
    "            print(f\"{t['Date']} | {t['ID']} | {t['Type']} | {t['Account']} | ${t['Amount']:.2f}\")\n",
    "\n",
    "    elif choice == \"4\":  # Summary\n",
    "        total = checking_balance + savings_balance\n",
    "        print(\"\\nAccount Summary:\")\n",
    "        print(f\"Checking: ${checking_balance:.2f}\")\n",
    "        print(f\"Savings:  ${savings_balance:.2f}\")\n",
    "        print(f\"Total:    ${total:.2f}\")\n",
    "\n",
    "    elif choice == \"5\":  # Interest\n",
    "        print(\"\\nSavings Projection (4% per year):\")\n",
    "        for year in range(1, 4):\n",
    "            future = savings_balance * ((1 + interest_rate) ** year)\n",
    "            print(f\"Year {year}: ${future:.2f}\")\n",
    "\n",
    "    elif choice == \"6\":  # Exit\n",
    "        print(\"\\nFinal Balances:\")\n",
    "        print(f\"Checking: ${checking_balance:.2f}\")\n",
    "        print(f\"Savings:  ${savings_balance:.2f}\")\n",
    "        print(\"Goodbye!\")\n",
    "        break\n",
    "\n",
    "    else:\n",
    "        print(\"Invalid choice. Please enter 1-6.\")\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "4a889e44-ed5d-495b-a7c3-16bf5a359181",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "anaconda-panel-2023.05-py310",
   "language": "python",
   "name": "conda-env-anaconda-panel-2023.05-py310-py"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.11.5"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
