Literature Review

Important: these are candidate sources. Before submitting, open each one, read the abstract and the method part, check the authors, venue and year, and write in your own words what we use. Remove any source that you did not really use. The requirement is at least 12 sources, at least 8 of them scientific, and mostly from the last five years. Hyphens were removed from the titles below, so check the exact titles when you cite.

1. List of sources and analysis
For each source: what it does, what we use, and what limits it has.

1. Pasupat and Liang. Compositional Semantic Parsing on Semi Structured Tables. ACL 2015. Foundational paper. Treats table questions as semantic parsing. We use the idea of table question answering as a task. Limits: small tables, before LLMs, no messy spreadsheets.

2. Yu et al. Spider, a Large Scale Human Labeled Dataset for Text to SQL. EMNLP 2018. Foundational paper. Benchmark for turning questions into SQL. We use its way of measuring execution accuracy. Limits: clean databases, not user spreadsheets.

3. Herzig et al. TAPAS, Weakly Supervised Table Parsing via Pre training. ACL 2020. Table aware transformer that answers without writing code. We use it as a contrast to code generation. Limits: limited table size and weak on complex arithmetic.

4. Chen et al. Evaluating Large Language Models Trained on Code. 2021, arXiv 2107.03374. Shows models writing code and how to test whether the code is correct. Basis for our idea that the model writes code and we run it. Limits: generated code can be wrong or unsafe.

5. Gao et al. PAL, Program aided Language Models. ICML 2023, arXiv 2211.10435. The model writes a program and an interpreter computes the answer. Supports giving arithmetic to an interpreter. Limits: needs a safe place to run code.

6. Chen et al. Program of Thoughts Prompting. TMLR 2023, arXiv 2211.12588. Separates reasoning from calculation. We use it for prompt design for number questions. Limits: depends on the prompt and the model size.

7. Sui et al. Table Meets LLM, Can Large Language Models Understand Structured Table Data. WSDM 2024, arXiv 2305.13062. Compares ways of writing a table into a prompt. We use it to decide how to describe an Excel sheet to the model. Limits: results depend on the model and format.

8. Zhang et al. TableLlama, Towards Open Large Language Models for Tables. NAACL 2024, arXiv 2311.09206. An open model tuned for table tasks. A possible candidate for local use. Limits: needs fine tuning and may not generalise.

9. Li et al. Can LLM Already Serve as a Database Interface, BIRD. NeurIPS 2023, arXiv 2305.03111. A large, realistic benchmark with dirty values. Shows that messy data lowers accuracy. Limits: SQL only.

10. Pourreza and Rafiei. DIN SQL, Decomposed In Context Learning of Text to SQL. NeurIPS 2023, arXiv 2304.11015. Splits the task into steps with self correction. We use the idea of multi step generation and correction. Limits: relies on large proprietary models.

11. Carlini et al. Extracting Training Data from Large Language Models. USENIX Security 2021, arXiv 2012.07805. Shows that models can leak memorised data. Motivation for our privacy goal. Limits: shown on specific models.

12. Greshake et al. Not What You've Signed Up For, Indirect Prompt Injection. AISec 2023, arXiv 2302.12173. Attacks that come through data the model reads. Our threat model for malicious text in cells. Limits: the attack landscape keeps changing.

13. Dettmers et al. QLoRA, Efficient Finetuning of Quantized LLMs. NeurIPS 2023, arXiv 2305.14314. Four bit quantisation and low memory use of models. Supports running models on limited hardware. Limits: some quality loss.

14. Frantar et al. GPTQ, Accurate Post Training Quantization for Generative Pre trained Transformers. ICLR 2023, arXiv 2210.17323. Post training quantisation. Shows the trade between memory, speed and accuracy. Limits: accuracy drops on some tasks.

15. Touvron et al. LLaMA, Open and Efficient Foundation Language Models. 2023, arXiv 2302.13971. Open weight model family. Shows that locally deployable models exist. Limits: smaller models reason worse.

16. OWASP. Top 10 for LLM Applications. Industry guide, check the current version. A list of risks of LLM applications that we use as a security checklist. Limits: not peer reviewed.

17. Ollama documentation and llama.cpp repository. Technical documents, write the access date. Describe local model runtimes and their API. Limits: features change quickly.

Count: 15 scientific papers and 2 practical sources, 17 in total. Twelve of the papers are from 2021 or later, and three are foundational.

2. What we learned from these sources
Where the field is. Early work treated table questions as a parsing problem (sources 1 and 3). With large language models the picture changed. The most reliable idea for number questions is not to ask the model to calculate. Instead the model writes a program or a SQL query and an interpreter computes the answer (sources 4, 5 and 6). This is the approach we picked. The papers also show that the way a table is written into the prompt matters (source 7), and that real messy data lowers accuracy compared with clean benchmarks (source 9). Most benchmarks are about databases or clean tables, not about real Excel files with merged cells and formulas, so we have to handle that ourselves.

Privacy and security. Sending data to a third party model has a real leakage risk (source 11). Any system that puts cell text into a prompt can be attacked through that text (sources 12 and 16), and running generated code needs isolation.

Hardware. Quantisation lets models of a few billion parameters run on ordinary machines (sources 13, 14 and 15), but they are weaker than large cloud models. That is why we send only the structure and a few rows, and let code do the calculation.

What is missing and what we do. The papers deal with accuracy or with privacy, not both together, and they do not look at Excel as such. We try to combine a fully local setup, checked calculation, login and logging, with a focus on Excel, and we measure the result on our own test set.