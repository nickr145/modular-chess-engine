# Chess Game Engine — Design & Architecture

**Note**
This project was completed as part of **CS246 (Object-Oriented Software Development)** at the **University of Waterloo**.
Due to course policies, the **source code cannot be released publicly**. This repository contains the project design documentation and overview only.

If you’re interested in the implementation details, architecture decisions, or extending the system, feel free to reach out at nicholas.rebello@gmail.com

---

## Project Overview

This project is a **fully featured chess game engine** designed with strong object-oriented principles, extensibility, and maintainability in mind. The system supports standard chess rules, multiple player types (human and computer), and both text-based and graphical displays.

Rather than focusing solely on gameplay, the project emphasizes **clean architecture**, **design patterns**, and **robust handling of complex game rules** such as check, checkmate, castling, en passant, pawn promotion, and stalemate.

---

## Key Features

* Complete implementation of standard chess rules
* Modular, object-oriented design with clear separation of concerns
* Support for:

  * Human vs Human
  * Human vs Computer
  * Computer vs Computer
* Multiple computer difficulty levels
* Text-based and graphical board displays
* Custom board setup for testing and experimentation
* Efficient move validation and rule enforcement

---

## Design Philosophy

The system was designed to be:

* **Maintainable** — logic encapsulated within well-defined classes
* **Extensible** — new rules, features, or variants can be added with minimal refactoring
* **Safe** — careful memory management and avoidance of leaks
* **Testable** — piece logic and board state can be verified independently

To achieve this, the project relies heavily on **object-oriented design principles** and established **software design patterns**.

---

## Architecture Overview

At a high level, the system is built around three core abstractions:

### Board

* Owns the 8×8 grid of squares and all active pieces
* Manages turn order, move execution, and game state
* Tracks special conditions such as check, checkmate, and stalemate
* Acts as the central **subject** in the Observer pattern

### Piece Hierarchy

* Abstract `Piece` base class with concrete subclasses:

  * King, Queen, Rook, Bishop, Knight, Pawn
* Each piece implements its own move-generation logic
* Special rules (e.g., castling, en passant, promotion) are handled within the relevant piece classes

### Square

* Represents an individual board cell
* Tracks occupancy, color, and piece assignment
* Notifies observers when its state changes

---

## Design Patterns Used

* **Observer Pattern**
  Used to keep text and graphical displays synchronized with board state changes, enabling clean separation between game logic and UI.

* **Inheritance & Polymorphism**
  Each chess piece encapsulates its own movement and rule logic.

* **Encapsulation**
  Internal state (e.g., whether a rook can castle or a king is in check) is managed through controlled interfaces.

---

## Computer Player Design

The computer player is structured to allow **multiple difficulty levels**, where higher levels may reuse or build upon logic from simpler ones. This layered approach enables:

* Incremental improvement of AI strength
* Easier debugging and testing
* Future expansion (e.g., opening books or deeper lookahead)

---

## Extensibility

The design explicitly supports future enhancements, including:

* Opening books for early-game play
* Undo/redo functionality using board-state stacks
* Chess variants (e.g., four-player chess)
* Additional evaluation heuristics for stronger AI

Many of these extensions are discussed directly in the design document .

---

## What’s in This Repository

```text
.
├── README.md
└── Chess_Design_Document.pdf
```

* `README.md` — Project overview and design summary
* `Chess_Design_Document.pdf` — Full architectural design, UML diagrams, and rationale

---

## Technologies & Concepts

* C++
* Object-Oriented Design
* UML Modeling
* Design Patterns (Observer, Inheritance)
* Game State Management

---

## Why This Project Matters

Chess is deceptively complex. Supporting its full rule set cleanly requires careful design, disciplined abstraction, and attention to edge cases. This project demonstrates how **thoughtful software architecture** can tame complexity and produce a system that is both powerful and adaptable.
