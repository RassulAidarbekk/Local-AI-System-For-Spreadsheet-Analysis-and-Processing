Testing and Evaluation Plan

1. What we want to show
That the system gives correct and checkable answers about Excel files, works fully offline, is fast enough on ordinary hardware, and is better than the simplest local alternative.

2. Test data
5 to 8 Excel files that we create ourselves, with no real company or personal data. For example sales, payroll like data, inventory, a workbook with several sheets, a messy one with merged cells and a title above the table, one with formulas, a CSV export with mixed date formats and missing entries, a workbook with text inside number columns, and two sheets with a known set of differences for the merge feature.
At least 50 questions with correct answers that we calculate by hand in pandas. They cover totals, filters, grouping, ranking, dates and missing values.
At least 10 files with injection text inside cells, for example a cell that says ignore your instructions.
At least 5 files with deliberately wrong values, to see if the verifier notices.

3. What we measure
Answer accuracy: the share of questions where the result equals the correct answer. Goal: at least 70 percent to start, final goal after the baseline.
Formula correctness: the result of the generated formula against the expected value. Goal: at least 70 percent.
Verifier detection: wrong results flagged divided by wrong results planted. Goal: at least 80 percent.
Speed: median and 95th percentile time per question. Goal: 30 seconds and 60 seconds.
Memory: peak RAM, and video memory if there is a GPU. Goal: fits the test machine.
Network: packet capture during a full run. Goal: no external connections.
Injection: successful attacks divided by injection files. Goal: zero.
Access control: automated tests for login and file separation. Goal: all pass.
Original file safety: file hash before and after. Goal: unchanged.

4. Conditions
We will write down the exact machine, meaning CPU, RAM, GPU and operating system, in the report. We use the same questions for every model, fix the temperature at 0, run each question three times and average the result. We test several Ollama models under the same conditions and pick the best one.

5. What we compare against
Baseline 1: the same Ollama model with the table pasted straight into the prompt and no code execution. This is the simplest local solution.
Baseline 2: manual pandas, which gives the correct answers and a rough idea of how long a human needs.
Optional: a cloud model on the same synthetic files, only for reference.

6. Types of tests
Unit tests with pytest for the Excel reader and cleaner, the prompt builder and the verifier.
Integration tests with pytest for upload, question and log entry.
Security tests with scripts for the sandbox limits, the injection files and login.
Evaluation with a benchmark script, with the results written in docs/evaluation_report.md.

7. When we say it worked
The must have non functional requirements NFR1 to NFR4 pass and our system is clearly more accurate than Baseline 1 on the test set.