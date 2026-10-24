Technology Comparison

We looked at six decisions. For each one we compared two or three options against what the project needs: everything local, results that can be checked, modest hardware, and a prototype we can finish in the time we have. The model runtime is already decided, but we still compared it with alternatives so the choice is justified.

Decision 1. Running the language model locally
Options: Ollama, llama.cpp server, vLLM.
Ollama is very easy to set up, works without a GPU, supports quantised models, has an HTTP API and is good for laptops.
llama.cpp is more manual to set up, works very well without a GPU, supports quantised models and has an HTTP API.
vLLM is more complex and mostly needs a GPU.
Our choice: Ollama. It is the easiest to install and use, it has a simple API and it handles quantised models, which we need for normal hardware. If a machine has no GPU we can still try llama.cpp as a backup.

Decision 2. Backend framework
Options: FastAPI, Flask, Django.
FastAPI has automatic API documentation and built in input validation, and it is light.
Flask is light but needs extra packages for documentation, and validation is manual.
Django is heavy and needs an extra package for an API.
Our choice: FastAPI, because validation and automatic documentation are built in and we need a documented API anyway.

Decision 3. How the model works with an Excel file
Option A. The model writes pandas or openpyxl code and we run it. Numbers are correct because the computer calculates. Big sheets are fine because only the structure and a few rows are sent. Messy Excel is handled well because we have full control in Python. The user can see the code. The risk is running generated code.
Option B. The whole table is pasted into the prompt. Numbers are often wrong, big sheets do not fit in the context, messy Excel is handled poorly and the user cannot see how it was done. The only risk is prompt injection.
Option C. Convert to DuckDB and let the model write SQL. Numbers are correct and the SQL is visible, but the Excel needs a clean import first and there is a risk of SQL injection.
Our choice: A. It matches what the papers recommend for number questions, and it lets the user see exactly what was done. Option C may be added later.

Decision 4. Reading and writing Excel
Options: openpyxl, pandas only, xlsxwriter.
openpyxl reads formulas, merged cells and stored values, and writes into an existing file.
pandas alone cannot see formulas or merged cells and has limited writing into existing files.
xlsxwriter can only write new files.
Our choice: openpyxl with pandas on top. We need to see formulas and merged cells and write results into a copy of the workbook. pandas is used for the analysis itself.

Decision 5. Where generated code runs
Options: Docker container without network, RestrictedPython, plain subprocess.
Docker gives strong isolation, can block the network and takes medium effort.
RestrictedPython has weak isolation and known bypasses, and cannot block the network.
A plain subprocess has weak isolation and blocking the network is difficult.
Our choice: Docker with the network disabled, a time limit and a memory limit.

Decision 6. Interface and log storage
For the interface we compared Streamlit and React. Streamlit is much faster for a team that works in Python, so we choose it for the prototype. For the activity log we compared SQLite, PostgreSQL and JSON files. SQLite needs no server and can be queried, so we choose it.

Which model
Not decided yet. We will test a few open models, for example models of 7 to 8 billion parameters that are good at code, in quantised form, on our test files. We will pick the best balance of accuracy and speed on the machine we use.

An idea we want to test
After the model writes an Excel formula, we can recalculate it with LibreOffice in headless mode and compare the result with the pandas answer. If this works well it will be a strong check for the formula feature.