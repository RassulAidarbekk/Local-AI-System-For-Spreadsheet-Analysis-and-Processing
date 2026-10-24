Evidence of Relevance

Rule: write only what was really said or measured. Keep verified findings and assumptions separate.
The task asks for 3 to 5 conversations with user representatives. We held 3 conversations with people who work with spreadsheets as part of their job (part A). We also have 5 short discussions with fellow students, which we treat only as supporting opinions (part B).
Names, roles and employers of the interviewees are not stored in this repository because of privacy. The team keeps its own private records and can show them to the supervisor if asked.

Part A. Conversations with people who work with spreadsheets

Conversation 1. Interviewee A. Date: 20 October 2026. Interviewer: Rassul. Working professional who handles company spreadsheets every day.
What they said about their current work:
Most of the working day goes into Excel and CSV files. Reports are exported from a company system, and every week data from several branches has to be put together. The branches format their columns in different ways.
They do not use AI tools for work, because the company forbids putting company data into public AI tools. The files contain pricing and internal margins, and breaking the rule could cost them the job.
The biggest time loss is not the calculation itself. It is formatting data and writing lookup formulas such as VLOOKUP and INDEX MATCH, merging two sheets by an ID and finding the differences.
What they said about our idea: when we described a local tool, they said the whole department would use it if the data is sure not to leave the company.
Requirements affected: FR2 (columns that differ between files), FR13 (merging sheets), FR7 (formulas), NFR1 (local only).

Conversation 2. Interviewee B. Date: 21 October 2026. Interviewer: Damir. Working professional who handles employee data.
What they said about their current work:
Payroll, benefits and shift data are exported as raw CSV files from time clock devices. Staff spend hours every week cleaning them: fixing date formats, calculating overtime and checking for missing entries.
The files contain national ID numbers, home addresses and salaries. They said the data cannot legally be processed outside the internal network, so cloud AI is not an option. They looked at AI before and stopped because of compliance.
What they said about our idea: it would help most by catching errors, for example asking who worked more than 40 hours in a week without an overtime flag, instead of applying several filters by hand. They said the interface must be simple enough for staff who are not technical.
Requirements affected: FR1 (CSV import matters), FR9 (date formats), FR4 (rule based questions), NFR1, NFR10 (simple interface).

Conversation 3. Interviewee C. Date: 22 October 2026. Interviewers: Rassul and Damir. Working professional who receives spreadsheets from clients.
What they said about their current work:
Client files arrive as large workbooks with merged cells, text inside number columns and broken formulas. Cleaning takes hours before the real work can start.
They sometimes need a macro or a complex formula, but do not know VBA or Python, so they copy solutions from forums and hope they work.
Confidentiality rules with clients mean they must remove client names from a file before using any online tool.
What they said about our idea: the first things they would ask are to standardise dates and currencies in a column, and to summarise expenses by category, which they now do with pivot tables. Working offline means they would not have to remove client names first.
Requirements affected: FR2 (merged cells, text in number columns), FR3 (broken formulas), FR9 (dates and currencies), summaries by category, NFR1.
Note: macros came up here. Macros are outside our scope, but formula generation and cleaning cover part of the same need.

Questions used
1. Which spreadsheets do you work with and what takes most time?
2. Have you used AI tools for this work, and if not, why not?
3. What would you ask such a tool to do first?
Question about hardware at the workplace was not asked in these conversations. We still need to find this out.

A weakness of these conversations
In all three, the interviewer described our tool and then asked if it would be useful. People tend to say yes to that, so the sentences about wanting the tool are only a sign of interest, not proof. The stronger evidence is what they told us about their current work and their rules.

Part B. Discussions with fellow students, supporting opinions only
We asked 5 students the same 3 questions, 15 to 17 minutes each: why a local solution matters, how relevant it is for ordinary office workers, and what the novelty is. Dates and who took part are to be filled in by the team: ____
The students repeated the same themes: confidentiality, rules and regulations, natural language access for non technical users, cost and internet dependence, and the idea that small quantised models can work on normal workstations. None of them described a workplace of their own. Statements about laws and penalties such as GDPR are their opinions and were not checked. The point about small models is a technical question that we test ourselves in the evaluation.

Verified findings and assumptions

Verified, all 3 conversations: people have rules or worries about sending spreadsheets to outside services. A said the company bans it, B said the law restricts it, C said client confidentiality rules apply. Affects NFR1.
Verified, all 3 conversations: real files are messy and cleaning takes hours. A said formats differ between branches, B said date formats and missing entries, C said merged cells and text in number columns. Affects FR2, FR3, FR9.
Verified, 2 conversations (A and C): lookups, merging sheets and summaries take a lot of manual effort. Affects FR7, FR13 and summaries.
Verified, 2 conversations (B and C): CSV files are common, so CSV import is more than a side feature. Affects FR1.
Partly supported: people would use a natural language tool. All three said yes, but after a leading question, so it is interest and not proof. Affects FR4.
Assumption, still open: users want to see how a number was calculated. Nobody was asked directly. Affects FR6 and FR8.
Assumption, still open: hardware at the workplace is enough for a quantised local model. Nobody was asked. A student expressed the opinion, and we test it in the evaluation. Affects NFR5 and NFR6.
Assumption, still open: a simple interface is enough for non technical staff. B asked for it, and we test it with a small usability check. Affects NFR10.
