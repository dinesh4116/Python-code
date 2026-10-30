# Daily expense tracker

import csv
import os
from datetime import datetime

FILE = "expenses.csv"

def create_file():
    if not os.path.exists(FILE):
        with open(FILE, "w", newline="") as f:
            writer = csv.writer(f)
            writer.writerow(["Date", "Category", "Description", "Amount"])


def add_expense(category, description, amount):
    if amount <= 0:
        print("Invalid amount!")
        return

    with open(FILE, "a", newline="") as f:
        writer = csv.writer(f)
        writer.writerow([
            datetime.now().strftime("%Y-%m-%d"),
            category,
            description,
            amount
        ])

    print("Expense added successfully!")


def view_expenses():
    with open(FILE, "r", newline="") as f:
        reader = csv.DictReader(f)

        print("\n--- Expense Details ---")
        for row in reader:
            print(row)


def total_expenses():
    total = 0

    with open(FILE, "r", newline="") as f:
        reader = csv.DictReader(f)

        for row in reader:
            total += float(row["Amount"])

    print("Total Expenses: Rs.", total)


def main():
    create_file()

    # Sample expense entries
    add_expense("Food", "Lunch", 150)
    add_expense("Travel", "Bus", 50)

    view_expenses()
    total_expenses()


if __name__ == "__main__":
    main()
