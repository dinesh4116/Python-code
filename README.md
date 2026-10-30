# personal expense tracker


expenses = []

def add_expense():
    name = input("Enter expense name: ")
    amount = float(input("Enter amount: "))

    expenses.append([name, amount])
    print("Expense added successfully!")

def view_expenses():
    print("\n--- Expense Details ---")
    for item in expenses:
        print(item[0], ":", item[1])

def total_expenses():
    total = 0
    for item in expenses:
        total += item[1]

    print("Total Expenses =", total)

while True:
    print("\n1. Add Expense")
    print("2. View Expenses")
    print("3. Total Expenses")
    print("4. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        add_expense()
    elif choice == "2":
        view_expenses()
    elif choice == "3":
        total_expenses()
    elif choice == "4":
        print("Thank you!")
        break
    else:
        print("Invalid choice!")
