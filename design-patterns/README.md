# Design Patterns

## What is design patterns
All software engineers and software architects use patterns when designing applications. Design patterns help solve 
common problems, improve cohesion, and manage dependencies (coupling) between components. They provide proven, 
reusable solutions that lead to more maintainable, scalable, and understandable software.

Design patterns are at the heart of software development and form a shared vocabulary among practitioners. They enable 
teams to communicate complex design ideas clearly and efficiently, making them an essential part of a software 
craftsman’s toolkit.

This document covers the **23 classic design patterns** implemented in **JavaScript**, as introduced in the legendary 
book often referred to as the "_bible_" of software architecture:

**Design Patterns: Elements of Reusable Object-Oriented Software**
by **Erich Gamma**, **Richard Helm**, **Ralph Johnson**, and **John Vlissides**

These authors are collectively known as the **Gang of Four (GoF)**, and their work continues to influence modern 
software design across languages and paradigms.

They recommend first learning the patterns below:
- Abstract Factory
- Adapter
- Composite
- Decorator
- Factory (Factory Method)
- Observer
- Strategy
- Template Method

These are the core patterns that every architect should know in my humble opinion.

Excerpt From
Design Patterns: Elements of Reusable Object-Oriented Software (Kem Apak's Library)
Erich Gamma
This material may be protected by copyright.

## Dedication
This is a huge undertaking, and before I begin, I seek the blessing and support of the **Great Architect of the Universe**.

This work is dedicated to my son and my father, **Özcan Apak**; to my brother, **Kerimcan Apak**; and to my grandfather, 
**Kemalettin Apak**. Their light, wisdom, and guidance have always helped me find a safe harbor when the waters were 
rough and have calmed me when my emotions ran high.

**Kem (Kemalettin) Apak** 
January 7th, 2026

## Table of Contents
- **Basic concepts**
  - Anatomy of a pattern
  - Cohesion & Coupling
  - Inheritance
  - Polymorphism
  - Interface
  - UML
- **Creational Patterns**
  - Abstract Factory
  - Builder
  - Factory (Factory Method)
  - Prototype
  - Singleton
- **Structural Patterns**
  - Adapter
  - Bridge
  - Composite
  - Decorator
  - Facade
  - Flyweight
  - Proxy
- **Behavioral Patterns**
  - Chain of Responsibility
  - Command
  - Interpreter
  - Iterator
  - Mediator
  - Memento
  - Observer
  - State
  - Strategy
  - Template (Template Method)
  - Visitor