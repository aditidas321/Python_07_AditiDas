# Python_07_AditiDas

import csv

class Employee:
    def __init__(self, emp_id, name, department, designation, salary):
        self.emp_id = emp_id
        self.name = name
        self.department = department
        self.designation = designation
        self.salary = float(salary)

employees = []

def add_employee():
    emp_id = input("Enter Employee ID: ")
    name = input("Enter Name: ")
    department = input("Enter Department: ")
    designation = input("Enter Designation: ")
    salary = float(input("Enter Salary: "))

    emp = Employee(emp_id, name, department, designation, salary)
    employees.append(emp)
    print("\nEmployee Added Successfully!\n")

def view_employees():
    if not employees:
        print("\nNo Employees Found.\n")
        return

    print("-" * 80)
    print(f"{'ID':<10}{'Name':<20}{'Department':<15}{'Designation':<15}{'Salary'}")
    print("-" * 80)

    for emp in employees:
        print(f"{emp.emp_id:<10}{emp.name:<20}{emp.department:<15}{emp.designation:<15}{emp.salary}")

def search_employee():
    choice = input("Search by (1-ID / 2-Name): ")

    if choice == "1":
        key = input("Enter Employee ID: ")
        for emp in employees:
            if emp.emp_id == key:
                print(vars(emp))
                return
    elif choice == "2":
        key = input("Enter Employee Name: ")
        for emp in employees:
            if emp.name.lower() == key.lower():
                print(vars(emp))
                return

    print("Employee Not Found")

def update_employee():
    emp_id = input("Enter Employee ID to Update: ")

    for emp in employees:
        if emp.emp_id == emp_id:
            emp.department = input("New Department: ")
            emp.designation = input("New Designation: ")
            emp.salary = float(input("New Salary: "))
            print("Employee Updated Successfully")
            return

    print("Employee Not Found")

def delete_employee():
    emp_id = input("Enter Employee ID to Delete: ")

    for emp in employees:
        if emp.emp_id == emp_id:
            employees.remove(emp)
            print("Employee Deleted Successfully")
            return

    print("Employee Not Found")

def salary_statistics():
    if not employees:
        print("No Employees Available")
        return

    salaries = [emp.salary for emp in employees]

    print("\nSalary Statistics")
    print("Highest Salary :", max(salaries))
    print("Lowest Salary :", min(salaries))
    print("Average Salary :", sum(salaries) / len(salaries))
    print("Total Employees :", len(employees))

def export_data():
    with open("employees.csv", "w", newline="") as file:
        writer = csv.writer(file)

        writer.writerow(["ID", "Name", "Department", "Designation", "Salary"])

        for emp in employees:
            writer.writerow([
                emp.emp_id,
                emp.name,
                emp.department,
                emp.designation,
                emp.salary
            ])

    print("Data Exported Successfully")

    print("\nReading Data from CSV\n")

    with open("employees.csv", "r") as file:
        print(file.read())

while True:
    print("""
========= Employee Management System =========
1. Add Employee
2. View Employees
3. Search Employee
4. Update Employee
5. Delete Employee
6. Salary Statistics
7. Export Data
8. Exit
""")

    choice = input("Enter Choice: ")

    if choice == "1":
        add_employee()

    elif choice == "2":
        view_employees()

    elif choice == "3":
        search_employee()

    elif choice == "4":
        update_employee()

    elif choice == "5":
        delete_employee()

    elif choice == "6":
        salary_statistics()

    elif choice == "7":
        export_data()

    elif choice == "8":
        print("Thank You!")
        break

    else:
        print("Invalid Choice")

   # Employee Management System

## Project Description

This project is developed using Python Object-Oriented Programming.

### Features

- Add Employee
- View Employees
- Search Employee
- Update Employee
- Delete Employee
- Salary Statistics
- Export Data to CSV
- Read CSV File

## Technologies Used

- Python 3
- CSV Module

## How to Run

python employee_management.py

========= Employee Management System =========

1. Add Employee
2. View Employees
3. Search Employee
4. Update Employee
5. Delete Employee
6. Salary Statistics
7. Export Data
8. Exit

Enter Choice: 1

Enter Employee ID: 101
Enter Name: Rahul
Enter Department: IT
Enter Designation: Developer
Enter Salary: 50000

Employee Added Successfully
