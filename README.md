# python-program-
'''Create a simple Python program that manages student data in a file.
The program should allow the following operations: Add a student:
The user should be able to add a new student's information (roll number, name, and grade) to the file students.txt.
The data should be appended to the file. Delete a student:
The user should be able to delete a student from the file by entering the student's roll number.
The program should search for the roll number in the file and remove that student's record. Exit:
The program should allow the user to exit the program.'''
'''import os

def display_menu():
    print("\nStudent Data Management System")
    print("1. Add Student")
    print("2. Delete Student")
    print("3. Exit")

def add_student():
    print("\nAdd Student Information")
    roll_number = input("Enter Roll Number: ")
    name = input("Enter Name: ")
    grade = input("Enter Grade: ")
    
    with open("students.txt", "a") as file:
        file.write(f"{roll_number},{name},{grade}\n")
    print("Student added successfully!")

def delete_student():
    roll_number = input("\nEnter Roll Number of student to delete: ")
    
    # Read all students into memory
    students = []
    found = False
    
    try:
        with open("students.txt", "r") as file:
            for line in file:
                if line.strip():
                    parts = line.strip().split(',')
                    if parts[0] == roll_number:
                        found = True
                        print(f"Deleting student: Roll No: {parts[0]}, Name: {parts[1]}, Grade: {parts[2]}")
                    else:
                        students.append(line)
    except FileNotFoundError:
        print("No students found in the database.")
        return
    
    if not found:
        print(f"Student with Roll Number {roll_number} not found.")
        return
    
    # Write all students back except the deleted one
    with open("students.txt", "w") as file:
        for student in students:
            file.write(student)
    
    print("Student deleted successfully!")

def main():
    while True:
        display_menu()
        choice = input("Enter your choice (1-3): ")
        
        if choice == '1':
            add_student()
        elif choice == '2':
            delete_student()
        elif choice == '3':
            print("Exiting program. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter 1, 2, or 3.")

if __name__ == "__main__":
    main()'''
'''email_set=set()
while True:
    print("****login****")
    print("1.Add")
    print("2.search")
    print("3.remove")
    print("4.list")
    print("5.exit")
    opt=int(input("enter your option"))
    if opt==1:
        email_id=input("enter email_id")
        if email_id in email_set:
            print("this email id exist")
        else:
            email_set.add(email_id)
    elif opt==2:
            email_id=input("enter email_id")
            if email_id in email_set:
                print(email_id,"is found")
            else:
               print("this  email id  not exists")
    elif opt==3:
        email_id=input("enter email-id")
        if email_id in email_set:
           email_set.remove(email_id)
        else:
            print("this email id not exists")
    elif opt==4:
        for email_id in email_set:
            print(email_id)
    elif opt==5:
        break'''
def add_student():
    roll_no = input("Enter Roll Number: ").strip()
    name = input("Enter Name: ").strip()
    grade = input("Enter Grade: ").strip()

    with open("students.txt", "a") as file:
        file.write(f"{roll_no},{name},{grade}\n")
    print("Student added successfully.\n")


def delete_student():
    roll_no = input("Enter Roll Number to delete: ").strip()
    found = False

    try:
        with open("students.txt", "r") as file:
            lines = file.readlines()

        with open("students.txt", "w") as file:
            for line in lines:
                if not line.startswith(roll_no + ","):
                    file.write(line)
                else:
                    found = True

        if found:
            print("Student deleted successfully.\n")
        else:
            print("Student with that roll number not found.\n")

    except FileNotFoundError:
        print("No student data found. Add some students first.\n")


def main():
    while True:
        print("---- Student Management System ----")
        print("1. Add Student")
        print("2. Delete Student")
        print("3. Exit")

        choice = input("Enter your choice (1/2/3): ")

        if choice == "1":
            add_student()
        elif choice == "2":
            delete_student()
        elif choice == "3":
            print("Exiting program. Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.\n")


if __name__ == "__main__":
    main()
