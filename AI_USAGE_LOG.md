# AI Usage Log

## Entry 01 - Requirements Definition
Stage: Requirements
Prompt/goal: Define functional requirements, non-functional requirements, open questions, and constraints/assumptions for a Customer Search CLI feature in REQUIREMENTS.md without writing code.
AI contribution: Structured and drafted comprehensive functional requirements (partial search by name/email, input validation, formatted result display, error handling, CLI options), non-functional requirements (zero external runtime dependencies, pytest support, performance), open design questions, and constraints/assumptions in REQUIREMENTS.md.
Student decision: I added more specific error messages to the requirements that addressed them and separated a requirement into 2 separate ones (NFR-02 & NFR-03) as the original requirement addressed to separate conditions.
Impact: REQUIREMENTS.md was created and edited.

## Entry 02 - Feature Specification
Stage: Specification
Prompt/goal: Edit SPEC.md to define the verifiable behavior of the Customer Search feature with full requirement traceability to validation rules, error handling, acceptance criteria, and test scenarios, including acceptance criteria for performance requirement NFR-04.
AI contribution: Drafted the complete specification in SPEC.md covering scope, domain model, search rules, validation rules, error handling, acceptance criteria (AC-01 through AC-08, including NFR-04 performance), and mapped all criteria and validation rules to test scenarios (TS-01 through TS-11).
Student decision: After receiving the modified SPEC.md document, I read all of it and made sure that all validation rules, error handling, acceptance criteria, etc., were mapped to the correct requirements. I also noticed that the agent added an unnecesary "--help" feature due to the description of one requirement (FR-06) so I had to go back and edit it. It also skipped the acceptance criteria for the requirement NFR-04 so I requested the agent to add it.
Impact: REQUIREMENTS.md was edited and checked again, SPEC.md was modified and corrected due to tracebility problems.

## Entry 03 - System Architecture
Stage: Architecture
Prompt/goal: Read REQUIREMENTS.md and SPEC.md to document the system architecture in ARCHITECTURE.md across three designated layers (CLI, Customer Service, Storage) and follow the example given to fill out some of the sections.
AI contribution: Structured ARCHITECTURE.md with a three-tier architecture (CLI, Customer Service, Storage/customers.json), defining component responsibilities, step-by-step data flow, concrete method interfaces, error handling boundaries, pytest testing strategy, and design decisions/trade-offs.
Student decision: Reviewing with the REQUIREMENTS.md and SPEC.md files, there were some minor corrections made to ARQUITECTURE.md, mostly related to simplyfing the way some parts were written in order to make them more understandable. There was also not a single mention of a "--help" feature so it is assumed that REQUIREMENTS.md and SPEC.md was correctly edited to omit the feature.
Impact: The changes made to ARQUITECTURE.md were accepted.

## Entry 04 - Task Definition
Stage: Tasks
Prompt/goal: Read REQUIREMENTS.md, SPEC.md, and ARCHITECTURE.md to populate TASKS.md with short, observable, and verifiable tasks without introducing new requirements.
AI contribution: Established tasks T-01 through T-06 in TASKS.md with concise goals, affected files, verifiable acceptance criteria mapped directly to requirements and specifications (AC, VR, EH, SR, NFR, C), and concrete verification procedures (e.g., pytest commands, persistence/validation runs).
Student decision: I checked if all requirements, acceptance criteria and other aspects covered in REQUIREMENTS.md and SPEC.md were covered in TASKS.md, from what I saw every task had at least one direct or indirect reference to one of the requirements. The agent commited a mistake when defining the "Documentation" task since it established that it had to update REQUIREMENTS.md and SPEC.md which is unnecessary, it also omitted some documents like tracebility.md and AI_USAGE_LOG.md.
Impact: Accepted all tasks in TASKS.md and redefined T-06.

## Entry 05 - Implementation, Testing, and Traceability
Stage: Implementation & Tests
Prompt/goal: Implement tasks T-01 through T-06 sequentially, adhering to the specifications, architecture, and agent instructions from the prompt, without modifying requirements or inventing new business rules.
AI contribution: Implemented project setup (T-01), Customer model and storage layer with schema validation (T-02), CustomerService and CLI table presentation (T-03), validation rules and graceful error messaging (T-04), automated test suite covering TS-01 through TS-11 (T-05), and updated documentation and traceability matrix (T-06).
Student decision: Maintained customers.json in the project root per specification and architecture, verified incremental implementation at each task step with pytest, and confirmed complete test coverage across 49 tests.
Impact: Completed fully functional, tested, and documented Customer Search CLI feature with zero external production dependencies and 100% test pass rate. Project documentation (README.md, TASKS.md and tracebility.md) was updated.