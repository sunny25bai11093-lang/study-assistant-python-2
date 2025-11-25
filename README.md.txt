# Python Study Assistant

This is a easy Python program that helps people to  manage their study tasks.  
It allows many features such as adding tasks, sorting them, calculating total time, finding the syllabus and givingmotivational messages.

## Features
- Add aim
- View task abouts
- Total time
- Highest time aim
- Remove duplicate tasks
- Sort by type
- Motivational speech

## How to Run
1. Install Python 
2. Run:




tasks = []
#make a function with parameters
def add_task():
    subject = input("Enter subject: ")
    topic = input("Enter topic: ")
    hours = float(input("Enter estimated hours: "))
    priority = int(input("Enter priority (1=High, 2=Medium, 3=Low): "))

    task = {"subject": subject, "topic": topic, "hours": hours, "priority": priority} 

    tasks.append(task)
    print("Task added!\n")
#define one more function
def display_tasks():
    if not tasks:
        print("No tasks yet.\n")
        return
    print("\n--- All Tasks ---")
    for i, t in enumerate(tasks, start=1):
        print(f"{i}. {t['subject']} - {t['topic']} | Hours: {t['hours']} | Priority: {t['priority']}")
    print()
#write third function
def total_hours():
    print("Total study hours =", sum(t["hours"] for t in tasks), "\n")
#head


def max_task():
    if not tasks:
        print("No tasks yet.\n")
        return
    t = max(tasks, key=lambda x: x["hours"])
    print("Task requiring most time:", t, "\n")

def remove_duplicates():
    unique = []
    for t in tasks:
        if t not in unique:
            unique.append(t)
    tasks.clear()
    tasks.extend(unique)
    print("Duplicates removed.\n")

def sort_priority():
    tasks.sort(key=lambda t: t["priority"])
    print("Tasks sorted by priority.\n")

def motivate():
    import random
    msgs = [
        "Keep going!", 
        "You got this!", 
        "Stay focused and win!"
    ]
    print(random.choice(msgs), "\n")

def menu():
    while True:
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Total Hours")
        print("4. Task with Maximum Time")
        print("5. Remove Duplicates")
        print("6. Sort by Priority")
        print("7. Motivational Message")
        print("8. Exit")

        ch = input("Enter choice: ")

        if ch == "1": add_task()
        elif ch == "2": display_tasks()
        elif ch == "3": total_hours()
        elif ch == "4": max_task()
        elif ch == "5": remove_duplicates()
        elif ch == "6": sort_priority()
        elif ch == "7": motivate()
        elif ch == "8":
            print("Goodbye!")
            break
        else:
            print("Invalid choice.\n")

menu()

