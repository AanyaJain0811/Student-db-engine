# 🗄️ Student DB Engine

An in-memory, menu-driven student record manager for the terminal, written in pure C on top of a dynamically allocated singly linked list.

![C](https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black)
![Linked List](https://img.shields.io/badge/Singly_Linked_List-F472B6?style=for-the-badge&labelColor=240918)
![Heap Memory](https://img.shields.io/badge/Heap_Allocation-F472B6?style=for-the-badge&labelColor=240918)

---

## Overview

Each student record is a `struct` stored in a heap-allocated node of a singly linked list. There is no database library and no file I/O: data lives in memory for the duration of the session, and every operation (insert, search, display) is implemented by hand.

## Features

- **Insert** a record with roll number, name, age, gender, course, marks, and email
- **Search** by:
  - Roll number
  - Name
  - Course
  - Marks range
- **Display** all records
- Menu-driven interface that loops until you choose Exit

## Menu

```
--- Student Database Menu ---
1. Insert Record
2. Search by roll number
3. Search by name
4. Search by course
5. Search by marks range
6. Display all records
7. Exit
```

## Design

| Component | Implementation | Complexity |
|:---|:---|:---:|
| Record node | `struct student` with `roll`, `name[50]`, `age`, `gender`, `course[50]`, `marks` (float), `email[50]`, and a `next` pointer | n/a |
| Allocation | One `malloc` per record | O(1) per insert |
| Insertion | Prepend at the list head (`newnode->next = head; head = newnode;`) | O(1) |
| Search | Linear traversal of the list | O(n) |
| Display | Linear traversal, printing each record | O(n) |

### Behavior notes

- Because insertion prepends, records are displayed **newest first**.
- Search by roll number stops at the **first match**; search by name, course, and marks range prints **every match**.
- Name and course matching use `strcmp`, so they are **exact and case-sensitive**.
- The marks range is **inclusive** on both ends.

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
- Nodes are not explicitly freed; memory is reclaimed by the OS when the program exits.
- Input is not validated (return values of `scanf` are unchecked, and duplicate roll numbers are allowed).

## Possible Extensions

- Update and delete operations, with proper `free` of removed nodes
- Input validation and duplicate roll number checks
- Persistence by saving and loading records from a file
- Sorting records by marks or name
ye le sorry ye ai kahi ka
