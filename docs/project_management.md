Project Management and Risks

Links
Git repository: this repository.
YouTrack: paste the link here.

1. Responsibilities
Rassul Aidarbek: backend, LLM integration, sandbox, security, API, architecture and security text.
Damir Zarkesh: Excel processing, interface, test data, testing, evaluation report.
Both: proposal, splitting the literature review, reviewing each other's pull requests.
Supervisor Abzal Kyzyrkanov: reviews deliverables at meetings, feedback goes in supervisor_feedback.md.

2. YouTrack tasks
Each task needs a responsible student, expected outcome, acceptance criteria and deadline.
DIP-1. Repository, README and folder structure. Rassul. High. 24 October.
DIP-2. Project proposal and scope. Rassul. High. 24 October.
DIP-3. Evidence of relevance from 3 to 5 conversations. Damir. High. 24 October.
DIP-4. Literature review. Both. High. 24 October.
DIP-5. Existing systems comparison. Damir. High. 24 October.
DIP-6. Technology comparison. Rassul. High. 24 October.
DIP-7. Requirements and acceptance criteria. Both. High. 24 October.
DIP-8. Architecture diagrams. Rassul. High. 24 October.
DIP-9. Interface prototype. Damir. High. 24 October.
DIP-10. Testing and evaluation plan. Damir. High. 24 October.
DIP-11. Project management and risks. Rassul. Medium. 24 October.
DIP-12. Supervisor feedback and follow up. Both. High. 24 October.
DIP-13. Backend skeleton with FastAPI and Ollama hello world. Rassul. High. Next milestone.
DIP-14. Excel reader and cleaner module. Damir. High. Next milestone.
DIP-15. Test Excel files and questions with correct answers. Damir. High. Next milestone.
DIP-16. Sandbox design spike with Docker and no network. Rassul. High. Next milestone.

3. Milestones
Milestone 1, pre defense 1, 24 October 2026: analysis, design, planning and prototype mockups.
Milestone 2, pre defense 2: backend, Excel module and basic interface, first benchmark. Date to agree with the supervisor.
Milestone 3, final pre defense: complete prototype, evaluation report and security tests. Date to agree with the supervisor.

4. Dependencies
Hardware that can run a quantised model of 7 to 8 billion parameters. To be confirmed.
Availability of open model weights through Ollama.
The API contract is needed by the interface and is described in prototype/mockups.md.
Test files are needed before benchmarking.

5. Risks
R1. Local model accuracy is too low. Likelihood medium, impact high. Mitigation: code generation and execution instead of direct answers, benchmark several models, keep the scope narrow.
R2. Not enough hardware or slow answers. Likelihood medium, impact medium. Mitigation: quantised models, limit sample size, llama.cpp as a fallback.
R3. Prompt injection through cell contents. Likelihood high, impact high. Mitigation: treat cells as data, use the sandbox, check outputs, keep an injection test set.
R4. Unsafe generated code. Likelihood medium, impact high. Mitigation: Docker sandbox, no network, time limits, allowed libraries only.
R5. Messy Excel files break parsing, for example merged cells, several tables on one sheet or formulas without stored values. Likelihood high, impact medium. Mitigation: a dedicated Excel module and test files for each of these cases.
R6. Not enough evidence from users. Likelihood medium, impact medium. Mitigation: book conversations early and mark assumptions clearly.
R7. Team availability or uneven workload. Likelihood medium, impact medium. Mitigation: meetings with the supervisor every two weeks, YouTrack tracking, reviewing each other's pull requests.
R8. Scope grows. Likelihood medium, impact medium. Mitigation: fixed scope list in the proposal and priorities in the requirements.

6. Supervision plan
Meetings with the supervisor every two weeks on Saturday mornings, where we show intermediate results.