Local LLM Spreadsheet Assistant

A local tool that helps people work with Excel files by asking questions in plain language. The language model runs on the user's own computer through Ollama, so the spreadsheet never goes to a cloud service.

Why we are doing this
Many companies keep important data in Excel, for example salaries, accounting and customer lists. Tools like ChatGPT or Copilot can analyse these files, but only if the file is uploaded to someone else's servers, and many organisations cannot do that. Local chat tools exist, but they usually read the table as plain text, make mistakes with numbers and keep no record of what was asked. We want to build something that works fully offline, shows how it got every number and keeps a log.

Who it is for
Accountants, analysts and office staff in finance or administration who work with confidential Excel files every day.

What we want to get
A working prototype with a web page, a backend and Ollama.
Answers about an Excel file together with the code or Excel formula that produced them.
A check that the numbers were really calculated and not guessed by the model.
Simple login and an activity log.
A test report with accuracy and speed numbers.

Team
Rassul Aidarbek, group SE-2411. Backend, Ollama integration, API and security.
Damir Zarkesh, group SE-2411. Reading and cleaning Excel files, web interface, test files and testing.
Supervisor: Abzal Kyzyrkanov.

Scope and current status
Included: xlsx files with several sheets, formulas, merged cells and messy headers. CSV as a simple import. Questions in natural language. Excel formula generation. Cleaning suggestions. Saving results to a new sheet or a new file. Ollama. Login and activity log.
Not included: training our own models, cloud hosting, macros, old xls files, many users editing at the same time.
Status on 24 October 2026: research, design and planning are done. We have mockups and API examples. Coding of the backend and the Excel module starts next.

Technologies
Python, Ollama, FastAPI, openpyxl, pandas, Streamlit, Docker for running generated code safely, SQLite, pytest and Git. The reasons are in docs/technology_comparison.md.

Links
YouTrack: paste the link here
Prototype: prototype/mockups.md

Documents
Proposal and scope: docs/proposal.md
Evidence that the problem is real: docs/evidence_of_relevance.md
Literature review: docs/literature_review.md
Existing systems: docs/system_comparison.md
Technology choices: docs/technology_comparison.md
Requirements: docs/requirements.md
Architecture and diagrams: docs/architecture.md and the diagrams folder
Testing and evaluation plan: docs/verification_plan.md
Management and risks: docs/project_management.md
Supervisor feedback: docs/supervisor_feedback.md

How to run and test
Not available yet. We will add it as soon as there is code that runs. A config example is in config/config.example.env.
