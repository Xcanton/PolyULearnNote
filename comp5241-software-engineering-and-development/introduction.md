# Introduction

## What is Software Engineering?

The software consists of computer programs and all documents associated with them (such as requirements, design models, and user manuals)

## What is software engineering?

An engineering discipline concerned with all aspects of software production.

It tells software engineers a systematic and organized approach to their work, and provides them proper tools depending on the problem, constraints, and resources.

## Why do we need Software Engineering?

Programming myths and software crisis.

## What is Programming?

Translating a design into a program

## What is Debugging?

programmers carry out some program testing to discover and remove falts in the program

## What is Prototyping?

A prototype is an initial version of a system used to demonstrate concepts and try out design options.

Used in (Requirement engineering, Design process, Testing process)

<figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>

### Advantages

* improved system usability
* closer match to users' real needs
* improved design quality
* improved maintainability
* reduce development effort

### Disadvantages (Throw-away)

* maybe impossible to tune the system to meet non-functional requirements
* normally undocumented
* degraded through rapid change
* will not meet normal organizational quality standards

## What is the Software Process?

Key to organize various aspects of the software engineering discipline.

Software Processing is a set of organized activities that leads to a software product.

### Fundamental activities

* <mark style="color:red;">Specification</mark> (functionality, performance, constraints)
* <mark style="color:red;">Design & Implementation</mark>
* <mark style="color:red;">Validation and Verification</mark> (V\&V)
  * 保证specification的是客户需要的
  * 保证design and implementation与specification对应
* <mark style="color:red;">Evolution</mark> (meet changing customer needs)

### Software Process Models

A software process model is an abstraction of certain types of software processes.&#x20;

#### Waterfall (sequential organization)

separate and distinct stages of specification and development

<figure><img src="../.gitbook/assets/image (230).png" alt=""><figcaption><p>Waterfall Model</p></figcaption></figure>

* <mark style="color:red;">Requirements analysis and definition</mark> (establish goals, services, and constraints)
* <mark style="color:red;">System and software design</mark> (Partition the requirements to either hardware or software system)
* <mark style="color:red;">Implementation and unit test</mark> (Software design -> programs or program units)
* <mark style="color:red;">Integration and system testing</mark> (Integrate and test program units)
* <mark style="color:red;">Operation and maintenance</mark> (Correct errors, improve system units, enhance system's services)

<mark style="color:red;">Advantages</mark>

1. Documentation is produced at each phase.&#x20;
2. Ease of planning and management
3. Ease of trace responsibility
4. Complies with other engineering process models

<mark style="color:red;">Disadvantage</mark>

1. Hard to accommodate changes after the process is underway. One phase has to be completed before moving into the next phase.

<mark style="color:red;">Suitable software projects</mark>

1. Well-understood software projects
2. Mature application domains where changes are limited
3. Safety/mission-critical applications

#### Evolutionary Development (interleaved)

interleaved specification, development, validation

<figure><img src="../.gitbook/assets/image (231).png" alt=""><figcaption><p>Evolutionary Development</p></figcaption></figure>

<mark style="color:red;">Subtypes</mark>:

1.  Exploratory development (边做边探索)

    well-understood requirements and add new features as proposed by the customer
2.  Throw-away prototyping (Better understand the customer's requirements)

    poorly understood requirements to clarify what is really needed

<mark style="color:red;">Advantages</mark>

1. More effective than waterfall in meeting the immediate needs of customers.&#x20;
2. Specifications can be developed incrementally: as users develop a better understanding of their problem.&#x20;
3. May be the best approach to develop small or medium sized systems.

<mark style="color:red;">Disadvantage</mark>

1. Invisible process:&#x20;
2. managers need regular deliverables to measure progress;&#x20;
3. frequent/quick changes hamper documentation.
4. Poorly structured: continuous change tends to corrupt the software structure.

#### Component-based software engineering

assembling from existing components.

relies on systematic reuse of existing components or COTS systems

<figure><img src="../.gitbook/assets/image (232).png" alt=""><figcaption><p>CBSE</p></figcaption></figure>

* <mark style="color:red;">Component analysis</mark> (given the requirement specifications, search components to implement them)
* <mark style="color:red;">Requirements modification</mark> (modify requirements to reflect available components)
* <mark style="color:red;">System design with reuse</mark> (system framework is designed considering reusable components)
* <mark style="color:red;">Development and integration</mark> (Develop new system, non-COTS parts, and integrate COTS components)

<mark style="color:red;">Advantages</mark>

1. Reduce the amount of software to develop
2. Reduce cost and risks
3. Faster delivery

<mark style="color:red;">Disadvantages</mark>

1. May lead to a system that does not meet the real needs of users
2. Some system evolution control is lost if the new version of reusable components are not under control

### Process Activities

depends on the software type, people, and organization structures

#### <mark style="color:red;">Specification/ requirement engineering</mark>

services, constraints, development

Requirement documentation levels

1. End-user/customers: high-level statement
2. System developer: more detailed specification

<figure><img src="../.gitbook/assets/image (176).png" alt=""><figcaption><p>Requirement Engineering Process</p></figcaption></figure>

1. Feasibility study (can the user needs be satisfied with current technologies)
2. Requirements elicitation and analysis (Deriving requirements by observing existing systems, and discussing with users)
3. Requirements specification (Translating gathered info into requirement documents)
4. Requirements validation (check the realism, consistency, and completeness of requirements)

#### Design and Implementation

The process of converting system specification into an executable system.

* Software Design (design a structure that realizes the specification)
* Implementation (translate this structure into an executable program)

<figure><img src="../.gitbook/assets/image (177).png" alt=""><figcaption><p>Software design process model</p></figcaption></figure>

Six Design Process Activities

* Architectural design (subsystems and their relationships)
* Abstract specification (within each subsystem, produce an abstract specification for each subsystem)
* Interface design (design and document interface for each subsystem)
* Component design (allocate service to and design interface of components)
* Data structure design (design and specify data structures for implementation)
* Algorithm design (design and specify algorithms to provide services)

Other methods (Structured methods, systematic approaches to develop a software design)

* Object-oriented design were proposed and unified in 1990s to create UML
* Object model (class and dependencies)
* Sequence model (workflow between objects)
* State transition model (state transition)
* Structural model (isa, hasa, aggregation)
* Data-flow model (data transition)

<figure><img src="../.gitbook/assets/image (178).png" alt=""><figcaption><p>The debugging process</p></figcaption></figure>

Debugging is different from testing:&#x20;

* testing: establishes the existence of defects
* debugging: locates and corrects the defects

#### Validation and Verification

Purpose of V\&V: to show that a system meets the requirements of the users, and conforms to the specifications.

How to V\&V:

* Checking and review processes
* Testing (execute the system with test cases that are derived from the specification)
* mathematical/mechanical proving (model checking, static/dynamic analysis)

<figure><img src="../.gitbook/assets/image (179).png" alt=""><figcaption><p>Testing Process</p></figcaption></figure>

1.  Component or unit testing&#x20;

    Individual components are tested independently
2.  System testing

    testing of the system as a whole
3.  Acceptance testing

    testing with customer data to check that the system meets the customers' needs

<figure><img src="../.gitbook/assets/image (180).png" alt=""><figcaption><p>Testing phases in software process</p></figcaption></figure>

#### Evolution

<figure><img src="../.gitbook/assets/image (181).png" alt=""><figcaption><p>System Evolution</p></figcaption></figure>

### Coping with changes

Changing cost (rework, as well as implementing new functionality)

#### Why Changing is inevitable?

* Business changes lead to new and changed system requirements
* New technologies open up new possibilities for improving implementations
* Changing platforms requires application changes

#### How to reduce the costs of rework

* Change avoidance (Activities to foresee possible changes before significant rework is required)
* Change tolerance (Process designs to accommodate changes at low cost)

[#what-is-prototyping](introduction.md#what-is-prototyping "mention")

#### Development/delivery

The evolutionary development software process model is the natural choice (waterfall or CBSE can incremental delivery)

Incremental delivery (在各个阶段交付功能)

Differences between incremental：

* one focuses on development (from the end user's perspective, the increments can be invisible)
* the other focuses on delivery (the delivery to the end user is incremental, and visible)

Advantage

* Customer value can be delivered with each increment so system functionality is available earlier.&#x20;
* Early increments act as a prototype to help elicit requirements for later increments.&#x20;
* Lower risk of overall project failure.&#x20;
* The highest priority system services tend to receive the most testing.

### Computer-aided software engineering (CASE)

CASE is to support software development and evolution process

#### Disadvantage

1. SE requires creative thought, not readily automated
2. SE is a team activity and for large projects, which CASE doesn't support.

Activities automated by using CASE:

* Graphical editors for system model development
* Data dictionary to manage design entities
* Graphical UI builder for user interface construction
* Debuggers to support program fault-finding
* Automated translators to generate new versions of a program

#### CASE tool classification (3 perspectives)

* functional perspectives: specific function
* process perspective: process activities that are supported
* integration perspective how they are organized

<figure><img src="../.gitbook/assets/image (173).png" alt=""><figcaption><p>Tools in different types</p></figcaption></figure>

#### Integration based classification

* Tools (support individual process)
* Workbenches (Support a process phase, e.g., specification or design)
* Environments (Support all or a substantial part of an entire process)
