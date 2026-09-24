# Agent Report

## Agent / Version
Antigravity CLI / Gemini 3.8 Flash (High)

## Initial Context
The repository initially had the documents REQUIREMENTS.md, SPEC.md, ARQUITECTURE.md, TASKS.md, AGENTS.md and empty documents like tracebility.md, agent-report.md and README.md so that the agent had the necessary context to implement the feature and fill in the project documentation. It also had empty folders /src and /test so that the agent could fill them with python code and automated tests.

## Task Sequence

### T-01
What the agent did: It read through REQUIREMENTS.md, SPEC.md, ARCHITECTURE.md, TASKS.md and AGENTS.md, then checked the repository for the empty src/ and test/ folders and noticed that customers.json was not created yet. It also ran a pytest that returned exit code 1 (collected 0 items / no tests ran). Once it noticed the first missing task (T-01), it created the customers.json file, a Customer search application and Customer search test package. And also an automated test "test_setup.py" to verify that the project structure and json file were valid.
Human review: It seemed to do everything as ordered and did not create files outside of the specified, except for test_setup.py, which seems to have been necessary so that the agent could test the acceptance criteria. 
Tests: test_setup.py

### T-02
What the agent did: Created models.py with the Customer dataclass containing id, name, and email;amd created storage.py with a load_customers function that loads customer records from the local JSON file and robust error handling and validation for missing files, invalid JSON syntax, non-list root elements, and invalid customer schemas per VR-03 and EH-04. It also created automated tests in test_storage.py that covered customer model validation, JSON file loading and invalid record schema errors. 
Human review: I checked and the agent produced all documents specified in T-02 from TASKS.md without additional modifications. It also made various tests to validate the customer model parameters and the lists, though it may have been more than expected (10 test in total), but either way all test validated the acceptance requirements and were passed successfully. 
Tests: test_storage.py

### T-03
What the agent did: Implemented Customer search service(search_by_name,  search_by_email, search and validate_query) in service.py, created cli.py with command-line parsing for flags (--name, --email, --query, and --file), ASCII table renderer displaying ID, Name, and Email columns and error handling for no matches. Lastly the agent created test_service.py with tests for partial name search, partial email search, unified query search, case insensitivity, whitespace trimming, and empty search results.
Human review: I verified all the changes and tests and they all verify each of the acceptance criteria esatblished in T-03.
Tests: test_service.py

### T-04
What the agent did: Changed the file service.py adding ValidationError(ValueError) and created test_validation.py. It also verified that cli.py catches validation exceptions and gives the correct outputs (zero matches, missing search arguments and invalid inputs) but did not make any changes.
Human review: It seems it barely changed service.py and didn't edit cli.py since both already had error handling for query validation and handling of command-line arguments. Though, it did create the file test_validation.py for the testing of all the necessary errors.
Tests: test_validation.py

### T-05
What the agent did: Created test_cli.py to verify that the CLI printed the correct ASCII Table for the different search modes (--name, --email, --query), the corresponding error messages to certain actions (Missing search arguments, Empty/whitespace query, etc.), and the correct format for the customer tables. It also verified the traceability across the complete test suite (test_service.py, test_storage.py, test_cli.py) for scenarios TS-01 through TS-11.
Human review: It seems the agent did not modify test_service.py nor test_validation.py since they already covered the necesessary test scope. In test_cli.py, the agent added all missing test cases to validate the behaviour of the CLI's presentation layer (table printing and error messages) which the other test documents do not adress.
Tests: test_cli.py, test_service.py, test_setup.py, test_storage.py, test_validation.py

## Problems Encountered
The customer.json file was supposed to go into the src file, but I accidently specified that it should go into the project root while making the SPEC.md and ARCHITECTURE.md documentation, I decided that it wasn't worth solving since the user can change the json file to a custom one, so it really didn't present a problem.

## Human Interventions
- I had to stop the agent from reading documents unrelated to the specifications like the agent-report and AI usage log. 
- I had to prevent them from editing the project documentation in one of the tasks since it wasn't supposed to edit that early.
- Every document added by the agent was reviewed before it was implementes into the repository.

## Requirement / Specification Changes
None, the implementation by the agent strictly followed the REQUIREMENTS.md and SPEC.md files, without making changes to neither document.

## Final Verification
- All test cases (T-01 through T-11) were covered (100% test coverage).
- All 49 test PASSED 0.38s.
- Complete mapping of functional and non-functional requirements (FR-01 through FR-11, NFR-01 through NFR-05) in tracebility matrix.
- All requirements have the 'Completed' status.

## Lessons Learned
- Maintain consistency among specification documents to get the agent to behave a certain way and take more precise and concise decisions in a project.
- Guiding the agent through each task to make sure that they not derailing from the main original objetive and requirement specification.
