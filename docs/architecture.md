Architecture and Diagrams

The editable diagram sources are in the diagrams folder as Mermaid files: context.mmd, use_case.mmd and component.mmd. Open them at mermaid.live to see and edit the picture, and export PNG or SVG files into the diagrams folder.

1. System context diagram (diagrams/context.mmd)
The user, who is an analyst or an accountant, uploads an Excel file and asks a question. The system gives back an answer, the code and a cleaned file. The administrator manages users and reads the activity log. The system talks to the local model in Ollama and to local file storage. No data is sent to external cloud services.

2. Use case diagram (diagrams/use_case.mmd)
User: log in with a token, upload an Excel file, view the schema and preview, ask a question, view the answer and the code, generate a formula, clean data and export, download or save the result.
Administrator: manage users and tokens, view the activity log.

3. Component diagram, draft (diagrams/component.mmd)
Web interface in Streamlit. Backend API in FastAPI. Access control. Excel reader and writer with openpyxl and pandas. Prompt builder and response parser. Ollama as the model runtime. Sandbox executor in Docker without network. Result verifier. Activity log in SQLite. File storage.
The interface talks to the API. The API uses access control, the Excel module, the prompt builder and the log. The prompt builder talks to Ollama and passes the code to the sandbox. The sandbox result goes to the verifier and then back to the API.

4. How a question is handled
1. The user logs in with a token and uploads an Excel file. The API checks the type and size and stores the file in that user's folder (FR1, FR11).
2. The Excel module opens the workbook, finds the header rows, deals with merged cells and builds a short description with sheet names, columns, types and a few sample rows (FR2, FR3).
3. The user types a question (FR4). The prompt builder sends the question and the short description to the local model in Ollama. It never sends the whole file, and cell text is treated as untrusted data (NFR3).
4. The model answers with code. The code runs inside a Docker sandbox with no network, a time limit and a memory limit (FR5, NFR2).
5. The verifier checks the result a second way (FR8). The API returns the answer together with the code (FR6), can save the result to a new sheet of a copy of the workbook (FR10), and writes a log entry (FR12).

5. Requirements and components
FR1, FR2, FR3, FR9 and FR10: Excel reader and writer, file storage.
FR4, FR5 and FR7: prompt builder, Ollama, sandbox.
FR6 and FR8: sandbox, verifier, API.
FR11: access control.
FR12: activity log.
NFR1, NFR2 and NFR3: sandbox, prompt builder, deployment without internet access.

6. Decisions
The reasons for each technology are in technology_comparison.md.