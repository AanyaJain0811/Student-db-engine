# 🗄️ Student DB Engine

An in-memory, menu-driven student record manager for the terminal, written in pure C on top of a dynamically allocated singly linked list.

![C](https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black)
![Linked List](https://img.shields.io/badge/Singly_Linked_List-F472B6?style=for-the-badge&labelColor=240918)
![Heap Memory](https://img.shields.io/badge/Heap_Allocation-F472B6?style=for-the-badge&labelColor=240918)

---

## Overview

Student records live as structs in heap-allocated nodes of a singly linked list. There is no database library and no file I/O: all data stays in memory for the duration of the session, and every operation (insert, search, display) is implemented by hand.

## Features

- **Insert** a student record (roll number, name, course, marks)
- **Search** by:
  - Roll number
  - Name
  - Course
  - Marks range
- **Display** all records
- Interactive menu loop driven from `main()`

## Design

| Component | Implementation | Complexity |
|:---|:---|:---:|
| Record node | Struct with `roll_no`, `name[50]`, `course[50]`, `marks`, and a `next` pointer | n/a |
| Allocation | One heap-allocated node per record | O(1) per insert |
| Insertion | Prepend at the list head (`newStudent->next = head; head = newStudent;`) | O(1) |
| Search | Linear traversal of the list (roll number, name, course, marks range) | O(n) |
| Display | Linear traversal, printing each record | O(n) |

## Build and Run

```bash
git clone https://github.com/AanyaJain0811/Student-db-engine.git
cd Student-db-engine
gcc -Wall -Wextra studentdata.c -o student_engine
./student_engine
```

## Project Structure

```
Student-db-engine/
├── studentdata.c   # Record struct, list operations, and menu loop
└── README.md
```

## Limitations

- Records are held in memory only, so data is lost when the program exits.
- Searches are linear scans; lookups are O(n) as the list grows.

## Possible Extensions

- Update and delete operations
- Persistence by saving and loading records from a file
- Sorting records by marks or name
