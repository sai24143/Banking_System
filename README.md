# Banking_System


class Account:
    def __init__(self, account_number, name, initial_balance=0):
        self.account_number = account_number
        self.name = name
        self.balance = initial_balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"Deposited ₹{amount} to account {self.account_number}")
        else:
            print("Invalid deposit amount.")

    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            print(f"Withdrew ₹{amount} from account {self.account_number}")
        else:
            print("Invalid or insufficient balance for withdrawal.")

    def display_info(self):
        print(f"Account Number: {self.account_number}, Name: {self.name}, Balance: ₹{self.balance}")


class BankSystem:
    def __init__(self):
        self.accounts = {}

    def create_account(self, account_number, name, initial_balance=0):
        if account_number in self.accounts:
            print("Account already exists!")
        else:
            self.accounts[account_number] = Account(account_number, name, initial_balance)
            print("Account created successfully.")

    def deposit_to_account(self, account_number, amount):
        if account_number in self.accounts:
            self.accounts[account_number].deposit(amount)
        else:
            print("Account not found.")

    def withdraw_from_account(self, account_number, amount):
        if account_number in self.accounts:
            self.accounts[account_number].withdraw(amount)
        else:
            print("Account not found.")

    def display_account(self, account_number):
        if account_number in self.accounts:
            self.accounts[account_number].display_info()
        else:
            print("Account not found.")


# Driver Code
if __name__ == "__main__":
    bank = BankSystem()

    while True:
        print("\n--- Banking System Menu ---")
        print("1. Create Account")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Display Account Info")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            acc_num = input("Enter account number: ")
            name = input("Enter name: ")
            balance = float(input("Enter initial balance: "))
            bank.create_account(acc_num, name, balance)

        elif choice == '2':
            acc_num = input("Enter account number: ")
            amount = float(input("Enter deposit amount: "))
            bank.deposit_to_account(acc_num, amount)

        elif choice == '3':
            acc_num = input("Enter account number: ")
            amount = float(input("Enter withdrawal amount: "))
            bank.withdraw_from_account(acc_num, amount)

        elif choice == '4':
            acc_num = input("Enter account number: ")
            bank.display_account(acc_num)

        elif choice == '5':
            print("Exiting the Banking System. Thank you!")
            break

        else:
            print("Invalid choice. Please try again.")
