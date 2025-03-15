# `Understanding Requirements: Requirement Engineering`

It involves **seven tasks** that may occur in parallel:

1. **Inception** – Understanding the problem, stakeholders, desired solution, and initial collaboration.
2. **Elicitation** – Gathering requirements from all stakeholders.
3. **Elaboration** – Creating an analysis model that refines data, function, and behavior.
4. **Negotiation** – Agreeing on realistic deliverables for both developers and customers.
5. **Specification** – Documenting requirements in various forms (text, diagrams, use-cases, prototypes, etc.).
6. **Validation** – Reviewing requirements for errors, inconsistencies, and missing details.
7. **Requirements Management** – Tracking and controlling changes throughout the project lifecycle.

---

### **Inception: Establishing the Groundwork**
- Identify **stakeholders** (direct or indirect beneficiaries).
- Ask relevant questions to clarify the scope:
  - Who requested this project?
  - Who will use it?
  - What economic benefits does it provide?
  - Are there alternative solutions?
- Encourage **collaboration** and resolve conflicts early.

---

### **Eliciting Requirements**
- Involves problem-solving, negotiation, and formal documentation.
- **Effective meetings**:
  - Include developers and stakeholders.
  - Follow structured agendas with facilitators.
  - Use tools like worksheets or virtual forums.
- Goals:
  - Define the problem.
  - Suggest solutions.
  - Identify and document key requirements.

---

### **SafeHome Project: Example of Requirement Gathering**
- **Product Request**: A home security system with wireless sensors for detecting threats (e.g., fire, burglary).
- **Object List**: Control panel, sensors, alarms, event logs, PC, phone numbers, etc.
- **Services List**: Configuring, monitoring, alarm activation, etc.
- **Constraints**: System must detect faulty sensors, be user-friendly, and connect to standard phone lines.
- **Performance Criteria**: Event detection in under one second, priority-based alerts.

---

### **Quality Function Deployment (QFD)**
A method to **translate customer needs into technical requirements**:
1. **Normal requirements** – Clearly stated by customers.
2. **Expected requirements** – Implicit but essential (e.g., reliability).
3. **Exciting requirements** – Features that exceed expectations and create satisfaction.

---

### **Use-Cases**
- Define **actors** (users or devices interacting with the system).
- Answer key questions:
  - Who is the primary/secondary actor?
  - What are their goals and tasks?
  - What system responses and variations exist?
- **Example: SafeHome Use-Case**
  - Homeowner logs in via a control panel.
  - System verifies the password.
  - Activates alarm in "stay" (perimeter sensors only) or "away" mode (all sensors).
  - Displays alerts for activation status.

---

### **Building Requirement/Analysis Models**
1. **Scenario-based models** – Functional descriptions and use-cases.
2. **Class-based models** – Categorize system objects into classes.
3. **Behavioral models** – Use state diagrams for system state transitions.
4. **Flow-oriented models** – Represent data flow and transformations.

---

### **UML & Requirement Analysis**
- **Use-Case Diagrams**: Define system interactions.
- **Activity Diagrams**: Represent workflows.
- **Class Diagrams**: Define object relationships.
- **State Diagrams**: Illustrate system state transitions.

---

### **Negotiating & Validating Requirements**
- Balance **functionality, performance, cost, and time**.
- Ensure requirements are:
  - Consistent with system objectives.
  - Unambiguous and achievable.
  - Free of conflicts.
  - Properly attributed to sources.
- Use **patterns** to simplify requirements modeling.

---

### **Final Notes**
- Requirements **evolve over time**, requiring continuous management.
- Use a **structured process** to gather, document, and validate them efficiently.
- Proper negotiation ensures a **win-win** outcome for all stakeholders.
