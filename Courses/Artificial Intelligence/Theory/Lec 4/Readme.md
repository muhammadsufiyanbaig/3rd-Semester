### **Expert Systems (ES) Overview**

- Expert systems **perform tasks in specific domains** that require human expertise, such as:
  - **Medical diagnosis**
  - **Fault detection**
  - **Data interpretation**
  - **Computer configuration**
- ES **solve problems using domain-specific knowledge** acquired from human experts.
- **Limitation**: ES **cannot** operate in situations requiring common sense.

---

### **Production Model in Expert Systems**

- **Humans solve problems** by applying **rules (knowledge)** to problem-specific information.
- **Knowledge Base (Long-term memory)**: Stores rules.
- **Problem-Specific Data (Short-term memory)**: Stores current facts.
- **Introduced by Stanford University researchers.**

---

### **Structure of Rule-Based Expert Systems**

1. **Knowledge Base**

   - Stores domain knowledge as **IF-THEN rules** (e.g., "IF temperature > 100°C THEN risk of overheating").
   - Created by **knowledge engineers** based on expert insights.

2. **Inference Engine (Brain of ES)**

   - **Applies rules to facts** to derive new conclusions.
   - **Adds new knowledge** dynamically when required.
   - **Resolves rule conflicts** when multiple rules apply.
   - Uses two reasoning strategies:
     - **Forward Chaining** (Data-driven)
     - **Backward Chaining** (Goal-driven)

3. **User Interface**
   - **Bridge between user & system**.
   - Can be **text-based** (commands) or **graphical** (GUI).
   - Provides **explanations** for decisions.

---

### **Expert System Shells**

- **Pre-built frameworks** for building expert systems.
- A shell **manages input/output** between the user, knowledge base, and inference engine.
- **Developers only need to add rules** to make the ES function.

---

### **Characteristics of Expert Systems**

- **Separate knowledge from processing** for easier updates.
- **Use heuristics** (rules of thumb) for problem-solving.
- **Explainable AI**: Can justify its reasoning.
- **Performance-focused**: Speed & accuracy are critical.

---

### **Capabilities of Expert Systems**

- **Advising** users like a consultant.
- **Assisting in decision-making**.
- **Explaining & justifying conclusions**.
- **Predicting outcomes** based on data.
- **Suggesting alternative solutions**.

#### **Can Expert Systems Make Mistakes?**

- Yes, just like human experts.
- They **depend on the quality of their knowledge base**.

---

### **Limitations of Expert Systems**

1. **Difficult Knowledge Acquisition** – Hard to extract expertise from human experts.
2. **High Maintenance** – Keeping knowledge updated is challenging.
3. **Expensive Development** – Requires **time, experts, and resources**.

---

### **Comparison: Expert Systems vs. Conventional Systems**

| Feature                | Expert Systems              | Conventional Systems         |
| ---------------------- | --------------------------- | ---------------------------- |
| **Knowledge Handling** | Uses **rules & heuristics** | Uses **fixed algorithms**    |
| **Decision Making**    | Handles **uncertainty**     | Requires **precise data**    |
| **Learning Ability**   | Can **update knowledge**    | **Fixed logic, no learning** |

---

### **Inference Methods**

#### **1. Forward Chaining (Data-Driven)**

- **Starts with known facts** → **applies rules** → **derives conclusions**.
- Example: Diagnosing a disease based on symptoms.
- **Answers "What’s next?"**

#### **2. Backward Chaining (Goal-Driven)**

- **Starts with a goal** → **works backward** to find supporting facts.
- Example: Checking if a patient has a disease based on known symptoms.
- **Answers "Why did this happen?"**

---

### **Famous Expert Systems**

- **DENDRAL** (1965) – Chemical analysis.
- **MYCIN** (1972) – Blood disease diagnosis.
- **PROSPECTOR** (1972) – Mineral exploration.
- **CADUCEUS** (1975) – Internal medicine.
- **XCON (R1)** (1980) – Computer system configuration.

---

### **Planning in Expert Systems**

- **Planning is needed** to make AI agents autonomous.
- **Agents decide**:
  - **What actions to take** to achieve a goal.
  - **How to sequence actions** efficiently.

---

### **Environment Properties in AI Planning**

| Property            | Type                                      |
| ------------------- | ----------------------------------------- |
| **Observability**   | Fully Observable vs. Partially Observable |
| **Determinism**     | Deterministic vs. Stochastic              |
| **Time Dependency** | Static vs. Dynamic                        |
| **Complexity**      | Single-agent vs. Multi-agent              |

---

### **Types of AI Planners**

1. **State Space Planners**

   - Search through **possible states** to find solutions.
   - Example: **A\* Search Algorithm**.

2. **Partial-Order Planners**
   - Plan **only necessary steps**, avoiding unnecessary sequences.
   - Example: **STRIPS Planning**.

---

### **Final Summary**

- **Expert Systems** solve **domain-specific** problems using **rules & inference**.
- **Knowledge Base + Inference Engine = ES Intelligence**.
- **Forward & Backward Chaining** enable **problem-solving**.
- **Challenges** include **knowledge acquisition & system maintenance**.
- **Planning** allows AI to **make decisions** independently.
