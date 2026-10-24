Requirements

Priority: M means must have, S means should have, C means could have. Every must have has a way to check it.

Functional requirements

FR1 (M). The user uploads an xlsx file or a CSV file. CSV matters because users get raw exports from other systems. Check: valid files are accepted and other types give a clear error.
FR2 (M). The system reads all sheets, finds the real header row, handles merged cells, finds text inside number columns, and shows a schema and a preview. Check: on our test files the detected columns match the expected ones.
FR3 (S). The system reads both formulas and their values. Check: on a test file with formulas both are shown correctly.
FR4 (M). The user asks a question in natural language. Check: the question gives an answer or a readable error.
FR5 (M). The model writes code and the system runs it in the sandbox. Check: generated code runs in the sandbox and the result is returned.
FR6 (M). Every answer shows the code that produced it. Check: the answer always contains the code.
FR7 (S). The system writes an Excel formula for a requested calculation. Check: the formula gives the expected value on test cases.
FR8 (S). The system checks numeric results with a second calculation or a LibreOffice recalculation and warns when they differ. Check: planted errors in test files are flagged.
FR9 (S). The system suggests cleaning, such as duplicates, empty cells, wrong types, and different date and currency formats in one column, and saves a cleaned copy. Check: the cleaned file has the expected changes.
FR10 (M). Results can be written to a new sheet or a new file, and the original is never modified. Check: the original file hash is the same before and after.
FR11 (M). Login with a token, and each user sees only their own files. Check: no token gives error 401, and user A cannot open user B's file.
FR12 (M). Every query is logged with user, time, file, question, code and outcome. Check: one complete log entry for each query.
FR13 (S). The system can combine two sheets or files by a key column such as an ID and show the rows that do not match. Check: on test files with a known set of differences, all differences are found.

Non functional requirements

NFR1 (M). Everything runs locally and no user data leaves the machine. Check: network capture during a full test run shows no external connections.
NFR2 (M). The sandbox has no network, a time limit and a memory limit. Check: code that opens a connection or loops forever gets stopped.
NFR3 (M). Instructions hidden in cells do not change the system behaviour. Check: with the injection test files there are zero successful attacks.
NFR4 (M). Answer accuracy on our test set. Check: at least 70 percent correct to start, final target after we measure the baseline.
NFR5 (S). Speed. Check: median 30 seconds or less and 95th percentile 60 seconds or less, for files up to 10000 rows.
NFR6 (M). Runs on one ordinary machine with documented hardware. Check: the setup guide works on a clean machine.
NFR7 (M). No passwords, keys or personal data in the repository. Check: a repository scan finds none.
NFR8 (M). The API is documented. Check: the docs page lists all endpoints.
NFR9 (S). Automated tests run with one command. Check: pytest passes.
NFR10 (S). The interface is simple enough for staff who are not technical. Check: two people who did not build the system upload a file and get an answer without help, and we write down where they got stuck.

Some of these numbers are guesses for now. We will check them with real users, see evidence_of_relevance.md, and with our first measurements.