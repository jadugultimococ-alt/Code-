# Code-
Final code

# ==========================================================
                                                        # Student Document Request Monitoring System
                                                           # PHINMA Cagayan de Oro College
                                                 # ==========================================================


                   #==========================================================FINAL CODE==========================================================



admin_username = "admin"
admin_password = "admin123"

                                                  #==================== Student Accounts already exist ====================
students = {
    "jay": {
        "password": "jay123",
        "student_id": "126519120056",
        "gender": "Male"
    }
}

document_requests = {}
request_number = 1001


                                                      # ==================== Admin Login ====================

def admin_login():
    print("=================== Admin Login ===================")
    username = input("Enter username: ")
    password = input("Enter password: ")

    if username == admin_username and password == admin_password:
        print("Admin Login Successful.")
        admin_menu()
    else:
        print("Invalid admin credentials.")


                                                       # ==================== Admin Menu ====================

def admin_menu():
    while True:
        print("=================== Admin Menu ===================")
        print("1. View document requests")
        print("2. Update request status")
        print("3. View student accounts")
        print("4. View request records")
        print("5. Back to Main Menu")
        print("6. Logout")

        choice = input("Enter choice: ")

                                               #==================== admin can View document requests ====================
        if choice == "1":
            if not document_requests:
                print("No document requests yet.")
            else:
                print("========== Student Document Requests ==========")
                print("Request No. | Student | Student ID | Gender | Document | Price | Status")
                print("-" * 100)

                for number, info in document_requests.items():
                    print(
                        number, "|",
                        info["username"], "|",
                        info["student_id"], "|",
                        info["gender"], "|",
                        info["document"], "|",
                        ""+ str(info["price"]), "|",
                        info["status"]
                    )

                                               # ==================== admin can view Update request status ====================
        elif choice == "2":
            if not document_requests:
                print("No document requests available to update.")
                continue

            print("Available Request Numbers:")

            for number in document_requests:
                print(number, end=" ")

            print()
            request_no = input("Enter request number: ")

            if request_no not in document_requests:
                print("Request number not found.")
                continue

            print("Status Options:")
            print("1. Pending")
            print("2. Processing")
            print("3. Ready for Claiming")
            print("4. Completed")

            status_choice = input("Enter choice: ")

            if status_choice == "1":
                new_status = "Pending"
            elif status_choice == "2":
                new_status = "Processing"
            elif status_choice == "3":
                new_status = "Ready for Claiming"
            elif status_choice == "4":
                new_status = "Completed"
            else:
                print("Invalid status choice.")
                continue

            confirm = input(
                "Confirm status update? (yes/no): "
            ).lower()

            if confirm == "yes":
                document_requests[request_no]["status"] = new_status
                print("Request status updated successfully.")
            else:
                print("Status update cancelled.")

                                                   #==================== admin can View student accounts ====================
        elif choice == "3":
            if not students:
                print("No student accounts yet.")
            else:
                print("================ Student Accounts ================")

                for username, info in students.items():
                    print(f"Username: {username}")
                    print(f"School ID: {info['student_id']}")
                    print(f"Gender: {info['gender']}")
                    print("==================================================")

                                        
