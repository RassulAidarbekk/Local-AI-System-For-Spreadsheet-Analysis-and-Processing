Project Proposal

Title: Development of a local AI system for secure analysis and processing of Excel spreadsheets based on large language models
Team: Rassul Aidarbek and Damir Zarkesh, SE-2411
Supervisor: Abzal Kyzyrkanov

1. Problem
Excel files often contain confidential data such as payroll, accounting and client lists. People would like to use AI to analyse them, but cloud tools need the file to be uploaded to an outside company. For many organisations this is not allowed or not safe. Local alternatives exist, but they are mostly plain chats. They do not check calculations, they do not control who sees which file and they keep no log.

2. Users
Accountants, analysts and staff of finance and administration departments. They know Excel well, but spend a lot of time on repeated work like cleaning data, writing formulas and making summaries.

3. Aim
Build a prototype of a local system that answers questions about Excel files in natural language, writes Excel formulas and cleaned data, and checks its own results, while everything stays on the organisation's own machines.

4. Objectives
1. Study the domain, existing tools and research.
2. Write requirements that can really be tested.
3. Design the architecture and the interface.
4. Build the backend with Ollama, the Excel processing module, a safe place to run generated code, login and logging.
5. Build a web interface for upload, questions and results.
6. Test on prepared Excel files, measure accuracy and speed, and describe the limits honestly.

5. Expected results
A working prototype with web interface, API and local model.
A set of test Excel files with correct answers.
Automated tests and an evaluation report.
A description of the architecture and security.

6. Scope
Inside: xlsx files with several sheets, formulas, merged cells and messy headers. CSV import for raw exports from other systems. Combining sheets by a key column. Cleaning of dates, currencies and text in number columns. Questions like totals, filters, grouping, ranking and dates. Excel formula generation. Data cleaning suggestions. Results saved to a new sheet or a new file, and the original file is never changed. Login with tokens. Activity log.
Outside: training models, cloud deployment, macros, the old xls format, charts and pivot tables as output, many users editing at once.

7. Why it is not trivial
Small local models make more mistakes than big cloud ones, so we cannot just ask the model for a number. The model writes code and the code is executed.
Running code written by a model is dangerous, so it has to run in an isolated place without network.
Real Excel files are messy. They have titles above the table, merged cells, several tables on one sheet and formulas without stored values. This needs its own processing.
Text inside cells can contain instructions meant for the model, called prompt injection, so cell content must be treated as untrusted.
It has to run on ordinary hardware.

8. Who does what
Rassul Aidarbek: backend, Ollama, code execution, security and API.
Damir Zarkesh: Excel reading and cleaning, interface, test files and testing.