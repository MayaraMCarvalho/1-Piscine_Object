# 🗂️ UML (Car Composition) - Module 02 - Piscine Object
(42 São Paulo)

Available in: [🇧🇷 Português](README.md)

![Language](https://img.shields.io/badge/UML-model-blue.svg?logo=uml)

This repository contains the solution for **Exercise 00** of **Module 02** from the 42 São Paulo Object Piscine. The objective is to model the architecture of a complex automotive system using the Unified Modeling Language (UML).

---

## 📜 Table of Contents

* [Project Overview](#-project-overview)
* [Tools Used](#%EF%B8%8F-tools-used)
* [Diagram Structure](#-diagram-structure)
* [Implementation Decisions & Bonuses](#-implementation-decisions--bonuses)
* [Author](#-author)

---

## 🚗 Project Overview

The project consists of creating a **Class Diagram** (`subject.png`) representing the internal structure of a car, including the engine, transmission, steering, brakes, electronics, and cockpit controls. The focus is to demonstrate a solid understanding of:

- Object-Oriented Programming (OOP).
- Class Relationships (Inheritance, Composition, Aggregation).
- Design Patterns (Singleton).
- Standard UML Notation.

> **Submission:** `ex00/subject.png` (Class diagram PNG).

---

## 🛠️ Tools Used

- **Diagramming Software:** StarUML
- **Submission Format:** PNG

---

## 📋 Diagram Structure

The diagram was built strictly following the *subject* specifications, detailing the following structures:

### 1. Abstract Classes and Interfaces
- **LinkablePart:** Acts as a virtual base class for components that can receive pressure commands, such as `Injector` and `BrakeController`.

### 2. The Car Core (Composition)
The `Car` class acts as the main container (Composition), aggregating vital subsystems:
- **Motor:** Internally composed of `Injector`, `ExplosionChamber`, and `Crankshaft`.
- **Transmission:** Manages the force sent to the wheels.
- **Direction & BrakeController:** Movement control and braking systems.
- **Cockpit & Electronics:** User interfaces and electronic control.

### 3. Design Patterns
- **Singleton:** Applied to the `GearLever` class, ensuring that only one instance of gear control exists in the system by inheriting from `Singleton<GearLever>`.

### 4. Key Relationships
- **Composition (Filled Diamond):** Used where objects are instantiated directly inside the class (e.g., `Motor` contains `Crankshaft`). Indicates a dependent lifecycle.
- **Aggregation/Association (Hollow Diamond):** Used where there is a reference via pointers (e.g., `Transmission` points to `Wheel`). Indicates that objects can exist independently.
- **Inheritance (Triangular Arrow):** Used for specializations (e.g., `Injector` **is a** `LinkablePart`).

---

## 💡 Implementation Decisions & Bonuses

To ensure clarity and adherence to UML best practices, the following conventions were adopted in the diagram:

### 1. Multiplicities
Logical multiplicities were defined for the automotive domain:
* `Direction` ↔ `Wheel`: `2..*` (Minimum of two directional wheels).
* `Transmission` → `Wheel`: `0..*`.
* `Motor` (Composition): `1` for its vital internal components.

### 2. Visibility and Encapsulation
* **Attributes:** Defined as private (`-`) to ensure data encapsulation.
* **Methods:** Defined as public (`+`) when they represent the object's communication interface (e.g., `+ execute()`).

### 3. Sequence Diagrams (Bonus)
*(If you are not submitting the sequence diagrams, remove this item 3)*
Additional diagrams were created to illustrate object interaction in critical scenarios:
1. **Acceleration:** Flow from `Pedal` to `Wheel`.
2. **Braking:** `BrakeController` actuation.

---

# 👩🏻 Author
**Mayara Carvalho**
<br>
[:octocat: @MayaraMCarvalho](https://github.com/MayaraMCarvalho) | 42 Login: `macarval`

---
