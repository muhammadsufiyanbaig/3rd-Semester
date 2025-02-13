# CHAPTER #03: SOFTWARE DESIGN

---

## Basic Concept of Software Design

**Design**
In software design phase input is SRS document and output is SDD. Software designing is most creative process, where we actually decide how a problem will be solved.

**Characteristics of a Good SDD**
- The SDD must contain all the requirement which were given in SRS.
- The design document must be readable, easy to understand and maintainable.
- It must describe a complete picture of data, functional and behavioural domain.

**Steps of Design**
Software Designing in 3-step process:
1. Interface Design
2. Architectual Design
3. Details Design

## Interface Design
- In this, we treat system as a whole and understand the relationship between the system & environment.
- Here we treat system as a black box and do not concentrate how a function will be implemented but we decide what is input & what should be the output according to user requirement or SRS. **(Like a `black box testing:` "Are we building the right product?")**
![Diagram 1](1.jpg)
## Architectural design
- In this we understand what are the major modules that must be implemented in the system and what are their responsibility and how they will communicate with each other.
- We do not give stress on individual modules but concentrate coupling and cohesion between the modules. Here we treat modules as black box. 
![Diagram 2](2.png)
## Detailed design/Low level design
- In this, specification of internal elements of all modules their functions, their processing methods, data structure, algorithms, everything is defined properly.
![Diagram 3](3.png)

## Modularity
In modular architecture, we understand that a system is composed of well defined conceptually simple and independent units interacting through a well-defined interface.

