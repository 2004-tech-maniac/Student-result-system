# student_result_system.py

def calculate_result(marks):
    total = sum(marks)
    average = total / len(marks)
    status = "Pass" if all(m >= 35 for m in marks) else "Fail"
    return total, average, status

def main():
    students = []

    while True:
        print("\n--- Student Result System ---")
        name = input("Enter student name: ")
        roll = input("Enter roll number: ")

        try:
            marks = []
            for i in range(1, 4):
                mark = float(input(f"Enter mark for Subject {i}: "))
                marks.append(mark)
        except ValueError:
            print("Please enter valid numbers.")
            continue

        total, avg, status = calculate_result(marks)

        student = {
            "name": name,
            "roll": roll,
            "marks": marks,
            "total": total,
            "average": avg,
            "status": status
        }

        students.append(student)

        choice = input("Do you want to add another student? (yes/no): ").lower()
        if choice != "yes":
            break

    print("\n--- Results ---")
    print("{:<10} {:<10} {:<8} {:<8} {:<8} {:<8} {:<8}".format("Name", "Roll", "Sub1", "Sub2", "Sub3", "Total", "Status"))
    for s in students:
        print("{:<10} {:<10} {:<8} {:<8} {:<8} {:<8} {:<8}".format(
            s["name"], s["roll"],
            s["marks"][0], s["marks"][1], s["marks"][2],
            s["total"], s["status"]
        ))

if __name__ == "__main__":
    main()
