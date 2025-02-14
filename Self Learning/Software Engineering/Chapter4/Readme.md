# CHAPTER #04: SOFTWARE TESTING

---

## What is Testing?

### Coding

- It is a phase where we translate a design or algorithm into a code of a particular programming language.
- It is a technical phase so there is not much in software engineering to given guideline in this phase, still we can give characteristics of good code.
- **Characteristics of Good Coding:**
  - It must be simple, easy to understand (unconditional jumps must be avoided).
  - It must be readable, i.e. we must use proper space and comments lines and write code in hierarchical fashion.
  - Usability try to code in modular fashion so that we can reuse the previous code.

### Compliance with Design and Coding Standards

- `Definition:` Compliance with design and coding standards refers to adhering to a set of rules, guidelines, and best practices that govern the process of designing and writing software code, ensuring consistent, high-quality, and maintainable software products.
- `Importance:`
  - Improves code readability and maintainability.
  - Facilitates collaboration and communication among team members.
  - Minimizes the introduction of defects and vulnerabilities.
  - Reduces development time and costs.

### Design Standards:

- `Architectural consistency:` Ensuring that the overall structure of the software adheres to established patterns and principles.
- `Component modularity:` Encouraging a modular design that promotes separation of concerns and code reusability.
- `Interface design:` Defining clear, consistent, and easy-to-understand interfaces for components or modules.
- `Scalability and performance:` Designing software to handle future growth and changing requirements without negatively impacting performance.

### Coding Standards:

- `Naming conventions:` Establishing consistent rules for naming variables, functions, classes, and other code elements.
- `Formatting:` Defining guidelines for indentation, whitespace, and code layout to improve readability.
- `Comments and documentation:` Providing clear, concise, and accurate inline comments and external documentation.
- `Error handling:` Implementing proper error handling and reporting mechanisms to improve software robustness and reliability.

### Compliance Enforcement:

- `Code reviews:` Conducting regular peer reviews to ensure adherence to design and coding standards.
- `Automated tools:` Using static code analysis and linter tools to identify deviations from established standards.
- `Continuous integration:` Integrating and testing code changes frequently to catch issues early in the development process.
- `Training and education:` Providing team members with training and resources to stay up- to-date on best practices and standards.

### Challenges:

- Balancing strict adherence to standards with development speed and flexibility.
- Ensuring that standards evolve as new technologies and best practices emerge.
- Obtaining buy-in from all team members and fostering a culture of compliance.

### Testing

- Because of human error there will be a bug or fault in the code and if that bug/fault is executed it become a failure.
- Software testing is a process of executing a program with the intention of finding bugs or fault in the code.
- It is generally very difficult to test a software exhaustibility or completely because the i/p space is very large. So, we have to write test cases wisely so that in minimum test we can provide the maximum reliability.

### Preparation for Testing

- Before we start test, we must have written, complete & approved copy of SRS.
- The budget, time & schedule for the testing must be written and document with proper timeliness & milestones which are to be achieved.
- We must have a proper assembled team with we understood responsibilities.
- We must have a written document of limitation property and scope of testing.

There are two methods of arranging testing:

- `Skilled based approach:` In this, a person works on a specific technology for a long time. here the person has a chance to become a true specialist in that particular area or technology
- `Project based approach:` Here we assign test team to a project so that they can have a much deeper and better understand of that particular project which increases the chance of success.

**Objective of testing**

- To check weather software is build accordance with the requirement or not.
- It guarantees to give a more reliable or better-quality product to the customer which will ensure its satisfaction.
- It also helps in software quality assurance where we understood what are the frequent or normal mistakes we do.

### Principle of software testing/guidelines

1. Testing must be based on user requirement
2. Test time, resource cost is limited.
3. It is impossible to check entire i/p space.
4. Testing must start after a proper test plan.
5. The possibility of existence of more error in a module id directly proportional to error already being found.
6. Testing must be done by a third party (at least not developer)
7. Assign best person of the company during testing.
8. Tester must have a destructive attitude towards the code.
9. We must perform both functional and non-functional testing
10. We must give emphasize on automated test tools but the final testing must be done by the humans

## Unit Testing

- `Definition:` It is the first level of testing that involves testing individual components or units of code to ensure they work correctly in isolation. It is concerned for the testing only a specific module.
- `Purpose:` To verify that each unit of code performs its intended function and to catch bugs early in the development process. Will check internal logic of module and Functionality and interface with the other module
- `Test Cases:` Writing small, specific test cases that cover different input scenarios and edge cases for each unit of code.
  **Example:**

```
const express = require("express");

const app = express();
app.use(express.json());

app.get("/api/hello", (req, res) => {
  res.status(200).json({ message: "Hello, World!" });
});

app.post("/api/add", (req, res) => {
  const { num1, num2 } = req.body;
  if (typeof num1 !== "number" || typeof num2 !== "number") {
    return res.status(400).json({ error: "Invalid input" });
  }
  res.status(200).json({ result: num1 + num2 });
});

module.exports = app;
```

`Create Unit Tests`

```
const request = require("supertest");
const app = require("./server");

describe("Node.js API Unit Tests", () => {

  test("GET /api/hello should return Hello, World!", async () => {
    const res = await request(app).get("/api/hello");
    expect(res.statusCode).toBe(200);
    expect(res.body).toEqual({ message: "Hello, World!" });
  });

  test("POST /api/add should return the sum of two numbers", async () => {
    const res = await request(app)
      .post("/api/add")
      .send({ num1: 5, num2: 10 });

    expect(res.statusCode).toBe(200);
    expect(res.body).toEqual({ result: 15 });
  });

  test("POST /api/add should return error for invalid input", async () => {
    const res = await request(app)
      .post("/api/add")
      .send({ num1: "five", num2: 10 });

    expect(res.statusCode).toBe(400);
    expect(res.body).toEqual({ error: "Invalid input" });
  });
});
```

## Integration Testing

- Integration testing is a phase in software testing in which individual software modules are combined and tested as a group.
- The primary objective of integration testing is to test the module interfaces, i.e. there are no errors in the parameter passing, when one module invokes another module. To verify the functional, performance, and reliability between the modules that interact with each other.
- Integration testing is the phase in software testing in which individual software modules are combined and tested as a group. It occurs after unit testing and before validation testing. Purpose is to expose faults in the interaction between integrated units.
- It can be time-consuming and costly due to the complexity of inter-module dependencies. requires a lot of coordination between different teams. The sequence of tasks is crucial for integration testing which may cause delays if not planned properly.

`Database Connection `

```
require("dotenv").config();
const { neon } = require("@neondatabase/serverless");

const sql = neon(process.env.DATABASE_STRING);

module.exports = { sql };

```

`Express APIs`

```
require("dotenv").config();
const express = require("express");
const { sql } = require("./db");

const app = express();
app.use(express.json());

// Initialize the database (only for testing)
const initializeDB = async () => {
  await sql`CREATE TABLE IF NOT EXISTS users (
    id SERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    email TEXT UNIQUE NOT NULL
  );`;
};
initializeDB();

// API route to add a user
app.post("/api/users", async (req, res) => {
  try {
    const { name, email } = req.body;
    const result = await sql`INSERT INTO users (name, email) VALUES (${name}, ${email}) RETURNING *`;
    res.status(201).json(result[0]);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

// API route to fetch all users
app.get("/api/users", async (req, res) => {
  try {
    const result = await sql`SELECT * FROM users`;
    res.status(200).json(result);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

module.exports = { app, sql };
```

`Integration Testing`

```
require("dotenv").config();
const request = require("supertest");
const { app, sql } = require("./server");

beforeAll(async () => {
  // Clear users table before running tests
  await sql`DELETE FROM users`;
});

afterAll(async () => {
  // No need to close connections since Neon is serverless
});

describe("Integration Testing for User API", () => {

  test("POST /api/users - Should create a new user", async () => {
    const newUser = { name: "John Doe", email: "john@example.com" };

    const res = await request(app).post("/api/users").send(newUser);

    expect(res.statusCode).toBe(201);
    expect(res.body).toHaveProperty("id");
    expect(res.body.name).toBe(newUser.name);
    expect(res.body.email).toBe(newUser.email);
  });

  test("GET /api/users - Should retrieve all users", async () => {
    const res = await request(app).get("/api/users");

    expect(res.statusCode).toBe(200);
    expect(Array.isArray(res.body)).toBe(true);
    expect(res.body.length).toBeGreaterThan(0);
  });
});
```

**Types of Integration Testing:**

- Big Bang Integration Testing
- Increamental Testing
  - Top-Down Integration Testing
  - Bottom-Up Integration Testing
  - Sandwich/Hybrid Integration Testing

### Big Bang Integration Testing:
It's a type of integration testing where all the modules are integrated simulutaneously and then tested as a completed system.

- `Simplicity:` It is easier to set up because testing starts only after all the modules have been integrated.
- `Suitability:` It is better suited for smaller systems where the modules are heavily interlinked.
- `Efficiency:` It can potentially save time, as testing is conducted after the entire software has been developed and integrated.
- `Issue Detection and Resolution:` It can be challenging to isolate and fix bugs because of the high level of integration.
- `High Risk:` There's a high risk involved as any significant issues are only found late in the development process, which can lead to project delays.
- `Resource Consumption:` It can be resource-intensive, requiring a significant amount of time and effort to find and fix bugs.
- `Inefficiency in Large Systems:` It's inefficient for larger systems where problems can become increasingly complex and hard to identify when all modules are integrated at once.

# Incremental Testing

Incremental testing is a software testing approach where individual components or modules of an application are tested incrementally to identify defects early. Instead of testing the entire system at once, components are tested step by step until the whole system is verified.

## Advantages of Incremental Testing
- Defects are detected early, reducing debugging complexity.
- Testing smaller modules simplifies troubleshooting.
- Ensures system stability before full integration.
- Reduces the risk of major system failures.
- Facilitates continuous feedback and improvement.

## Disadvantages of Incremental Testing
- Can be time-consuming and resource-intensive.
- Requires a well-defined test plan and execution strategy.
- Complex dependency management between modules.
- Additional effort is needed to create stubs and drivers for incomplete components.

## Top-Down Integration Testing

Top-down integration testing is an approach where testing starts from the top-level modules and proceeds downwards by integrating lower-level modules step by step. Stubs are used to simulate the behavior of lower-level modules that are not yet integrated.

### Advantages of Top-Down Integration Testing
- Helps identify major design flaws early.
- Allows early testing of critical high-level modules.
- Facilitates systematic debugging and verification.
- Supports early-stage validation of system architecture.

### Disadvantages of Top-Down Integration Testing
- Requires stubs for incomplete lower-level modules.
- Low-level modules are tested later, which may delay defect detection in those components.
- Test execution may become complex as the system scales.

## Bottom-Up Integration Testing

Bottom-up integration testing starts from lower-level modules and progressively integrates higher-level modules. Drivers are used to simulate the behavior of upper-level modules that are not yet integrated.

### Advantages of Bottom-Up Integration Testing
- Ensures that all lower-level modules are thoroughly tested before integration.
- Simplifies debugging as errors are usually confined to specific modules.
- No need for stubs since lower-level modules are tested first.
- Provides a stable foundation for higher-level integrations.

### Disadvantages of Bottom-Up Integration Testing
- High-level functionalities are tested late in the process.
- Requires drivers to simulate higher-level module interactions.
- Critical system-wide defects may only be detected at later stages.

## Sandwich/Hybrid Integration Testing

Sandwich or hybrid integration testing is a combination of top-down and bottom-up testing approaches. The system is divided into three layers: high-level modules, middle-level modules, and low-level modules. Top-down testing is performed for upper modules while bottom-up testing is done for lower modules, and the middle layer acts as the integration point.

### Advantages of Sandwich/Hybrid Integration Testing
- Utilizes the benefits of both top-down and bottom-up approaches.
- Enables parallel testing of different system components.
- Provides early detection of major design and implementation defects.
- Reduces the need for extensive stubs and drivers.

### Disadvantages of Sandwich/Hybrid Integration Testing
- Requires careful planning and coordination.
- Can be complex and resource-intensive.
- Middle-level modules may require additional effort for integration.
- Debugging can be challenging due to concurrent testing of different layers.

## System Testing
- System testing is a level of software testing where the complete and integrated software system as a whole is tested to evaluate its compliance with specified requirements in SRS.
- It is a crucial step before the software gets deployed to the user, aiming to catch any defects that might have slipped through the earlier stages of testing.
- System testing is performed in an environment that closely resembles the real-world or production environment.
- Generally, it is performed by independent testers who haven't been involved in the development phase to ensure unbiased testing.
- It may include functional testing, usability testing, performance testing, security testing, and compatibility testing.

## User Acceptance Testing
- `Definition and Purpose:` User Acceptance Testing (UAT) is the final testing phase before software deployment, aiming to validate if the system meets the business requirements and is fit for use.
- `Participants:` Usually performed by clients or end-users, UAT evaluates the software's functionality in a real-world scenario.
- `Focus:` Emphasizing the software's user-friendliness, efficiency, and effectiveness, UAT goes beyond purely technical aspects to assess overall user experience.
- `Documentation:` During UAT, all scenarios, outcomes, and user feedback are recorded to inform potential changes and improvements.
- `Outcome:` Successful UAT culminates in user sign-off, signifying the system meets the set acceptance criteria and is ready for release.

## Regression Testing
- `Definition:` Regression testing is a type of software testing carried out to ensure that previously developed and tested software still functions as expected after making changes, such as updates or bug fixes.
- `Purpose:` The main goal is to identify any issues or defects introduced by changes in the software, and to ensure that the changes have not disrupted any existing functionality.
- `Types:` Types of regression testing include unit regression, partial regression, and complete regression testing.
- `Test Cases:` Regression testing generally involves re-running previously completed tests and verifying that program behavior has not changed as a result of the newly introduced changes.
- `Automation:` Due to the repetitive nature of these tests, regression testing is often automated to improve efficiency and accuracy.

## Black box Testing/ White box Testing
- `Black Box Testing(Validation)` – Where we treat system as a whole, and check system according to user requirement `(are we making the right product)`, i.e. we check o/p for every i/p.
- `White Box Testing(Verification)` - Here we go inside a system and check how actual functionality is performed `(are we making the product right)`.

## Alpha Testing/ Beta Testing
- Any type of testing which is done on developer side is called alpha testing, usually performed with artificial test cases.
- Any type of testing which is done at customer side is called beta testing, usually performed with real time data.

## Stress Testing
- Stress testing is also known as endurance testing.
- Stress testing evaluates system performance when it is stressed for short periods of time.
- Stress tests are black box tests which are designed to impose a range of abnormal and even illegal input conditions so as to stress the capabilities of the software.

## Boundary value analysis
- Boundary Value Analysis is a software testing technique that focuses on the values at the boundaries of the input domain.
- The theory behind BVA is that errors are more likely to occur at the extremes of an input domain rather than in the center. Hence, it's generally more useful to focus on testing the boundary values.
- BVA is used for testing ranges and data array elements in a software application.
- In practice, BVA can be applied by identifying all the boundaries and then creating test cases for the boundary values and just above and below the boundary values.
- `Example:` Let's consider a simple application that accepts an integer input from 1 to 100.
- The boundary values here would be 0 (just below the valid range), 1 (lower limit), 100 (upper limit), and 101 (just above the valid range).
- You would then create test cases to input these values and verify the system's behavior.

## Equivalence partitioning
- Equivalence Partitioning is a black box testing technique that divides the input data of a software unit into partitions of equivalent data.
- The logic behind EP is that the system should handle all the equivalent data in the same way, thus you can save testing effort by testing only one value from each partition.
- It helps to reduce the total number of test cases from an infinite pool to a more manageable number.
- `Example:` Let's consider the same application that accepts an integer input from 1 to 100.
- The equivalence classes here would be: less than 1 (invalid), between 1 and 100 (valid), and greater than 100 (invalid).
- You would then create test cases to input a value from each of these classes (for example, 0, 50, and 101) and verify the system's behavior.

## Graph-Based Testing Methods
- Uses graphical representation for software testing.
- Nodes represent states; edges represent transitions.
- `Example:` For a web app with Login, Dashboard, and Logout screens, draw nodes for each and edges for transitions. Test paths like Login -> Dashboard -> Logout.

## Formal Technical Review (Peer Reviews)
- A Formal Technical Review (FTR) is a structured, systematic, and disciplined approach to examining and evaluating software artifacts, such as code, design documents, or requirements specifications, with the primary goal of identifying and addressing defects, inconsistencies, or areas for improvement.
- FTRs are conducted by a team of peers, consisting of the artifact's author and other software professionals, who analyze the work product and provide constructive feedback to ensure high-quality software development.
- Formal Technical Reviews play a crucial role in improving software quality, detecting issues early in the development lifecycle, promoting knowledge sharing, and fostering collaboration within software engineering teams.
**Type Peer Reviews:**
- Code Review
- Walkthroughs
- Inspections
- Pair Programming

**Formal Technical Review Process**
The Formal Technical Review Process
- **A. Planning**
  1. Establish objectives
  2. Select participants
  3. Set schedule
- **B. Preparation**
  1. Distribute materials
  2. Review guidelines
  3. Allocate time for individual review
**C. Conducting the review**
- 1. Discuss objectives
- 2. Review findings
- 3. Make decisions on action items
**D. Post-review activities**
- 1. Document review results 
- 2. Implement action items
- 3. Mointor follow-up actions


- **Roles in Formal Technical Reviews**
  - A. Review leader
  - B. Author
  - C. Reviewers
  - D. Recorder
- **Benefits of Formal Technical Reviews**
  - A. Improved code quality
  - B. Early defect detection
  - C. Knowledge sharing
  - D. Increased team collaboration
- **Challenges and Best Practices in Formal Technical Reviews**
  - A. Time management
  - B. Maintaining a constructive environment
  - C. Addressing bias
  - D. Ensuring consistency in review standards


##  Walk Through
- In software engineering, a walkthrough is a type of informal review process in which the author of a software artifact, such as code, design documents, or requirements specifications, presents their work to a group of peers.
- The main purpose of a walkthrough is to identify defects, inconsistencies, or areas for improvement through a collaborative discussion.
- Walkthroughs are typically less formal than other review methods, such as inspections, and focus on knowledge sharing, collaboration, and training among team members.

**Walk Through Process**
- **A. Planning**
  - 1. Define objectives
  - 2. Select participants
  - 3. Schedule the walkthrough
- **B. Preparation**
  - 1. Distribute materials
  - 2. Review guidelines
  - 3. Allocate time for individual review
- **C. Conducting the walkthrough**
  - 1. Present the work product
  - 2. Discuss findings
  - 3. Record issues and suggestions
- **D. Post-walkthrough activities**
  - 1. Summarize findings
  - 2. Assign action items
  - 3. Mointor follow-up actions


- **Roles in Walkthroughs** 
  - A. Presenter
  - B. Reviewers
  - C. Recorder
- **Benefits of Walkthroughs** 
  - A. Early defect detection 
  - B. Knowledge sharing 
  - C. Team collaboration 
  - D. Training and mentoring


## Code Inspection
- `Definition:` Code inspection is a systematic review process in which a team of developers evaluates a software product's source code for potential issues, such as errors, vulnerabilities, and deviations from coding standards.
- **Objectives:**
  - Improve code quality
  - Detect and fix defects early in the development cycle.
  - Share knowledge and best practices among team members.
  - Enforce coding standards and guidelines.

- **Process:**
  - `Planning:` Select the code to be inspected, define goals, and assemble the inspection team.
  - `Preparation:` Team members review the code individually to identify potential issues Inspection.
  - `Meeting:` The team discusses the identified issues, and the moderator notes down agreed-upon action items.
  - `Rework:` The original developer addresses the identified issues and submits the revised code.
  - `Follow-up:` The moderator verifies that all action items have been addressed and closes the inspection.

- **Inspection Team Roles:**
  - `Author:` The developer who wrote the code being inspected.
  - `Moderator:` The person who leads the inspection process and ensures it runs smoothly.
  - `Reviewers:` Other developers who provide insights and suggestions for improvements.
  - `Recorder:` The person responsible for documenting the issues found and decisions made during the inspection.

- **Benefits:**
  - Enhanced code quality and maintainability.
  - Reduced development costs and project risks.
  - Faster time-to-market due to early detection of defects Improved team collaboration and learning.
- **Limitations:**
  - Time-consuming process.
  - Possibility of human errors or oversights.
  - Potential for conflict among team members.
  - May not catch all types of defects, such as performance or concurrency issues.

  