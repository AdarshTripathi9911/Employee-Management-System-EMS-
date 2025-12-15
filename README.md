This is a simple console-based Python program for managing employee records. It lets users add employees, view all details, and search by ID. Employee data is stored in a dictionary, making it easy to manage. The project uses basic Python concepts like functions, loops, and conditionals — ideal for beginners learning data handling.
# Employee Management System

# Step 1 - Data Storage (Using Dictionary)
employees = {
    101: {'name': 'Satya', 'age': 27, 'department': 'HR', 'salary': 50000},
    102: {'name': 'Anjali', 'age': 25, 'department': 'IT', 'salary': 60000},
    103: {'name': 'Rohit', 'age': 30, 'department': 'Finance', 'salary': 55000}
}


# Step 2 - Menu System
def main_menu():
    while True:
        print("\n--- Employee Management System ---")
        print("1. Add Employee")
        print("2. View All Employees")
        print("3. Search for Employee")
        print("4. Exit")

        choice = input("Enter your choice (1-4): ")

        if choice == '1':
            add_employee()
        elif choice == '2':
            view_employees()
        elif choice == '3':
            search_employee()
        elif choice == '4':
            print("Thank you for using the Employee Management System. Goodbye!")
            break
        else:
            print("Invalid choice! Please try again.")


# Step 3 - Add Employee Function
def add_employee():
    print("\n--- Add New Employee ---")

    try:
        emp_id = int(input("Enter Employee ID: "))
    except ValueError:
        print("Invalid ID! Please enter a number.")
        return

    if emp_id in employees:
        print("Employee ID already exists! Please use a different ID.")
        return

    name = input("Enter Employee Name: ")
    try:
        age = int(input("Enter Employee Age: "))
    except ValueError:
        print("Invalid age! Please enter a number.")
        return

    department = input("Enter Employee Department: ")

    try:
        salary = float(input("Enter Employee Salary: "))
    except ValueError:
        print("Invalid salary! Please enter a number.")
        return

    employees[emp_id] = {
        'name': name,
        'age': age,
        'department': department,
        'salary': salary
    }

    print("✅ Employee added successfully!")


# Step 4 - View All Employees
def view_employees():
    print("\n--- All Employees ---")

    if not employees:
        print("No employees available.")
        return

    print("{:<10} {:<15} {:<10} {:<15} {:<10}".format("Emp ID", "Name", "Age", "Department", "Salary"))
    print("-" * 60)

    for emp_id, details in employees.items():
        print("{:<10} {:<15} {:<10} {:<15} {:<10}".format(
            emp_id, details['name'], details['age'], details['department'], details['salary']
        ))


# Step 5 - Search Employee
def search_employee():
    print("\n--- Search Employee ---")
    try:
        emp_id = int(input("Enter Employee ID to search: "))
    except ValueError:
        print("Invalid ID! Please enter a number.")
        return

    if emp_id in employees:
        emp = employees[emp_id]
        print("\nEmployee Found:")
        print(f"Name: {emp['name']}")
        print(f"Age: {emp['age']}")
        print(f"Department: {emp['department']}")
        print(f"Salary: {emp['salary']}")
    else:
        print("Employee not found.")


# Step 6 - Start the Program
main_menu()
