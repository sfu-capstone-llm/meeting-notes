# SFU Capstone Meeting Notes

## 3 - Oct 3, 2024

- Try to avoid old software
- Reach out ASAP
- Gradle not really great
- Maven is bettera
- Ekstazi RTS - simpler design
- Data Exploration problem
	- Find things similar in cite
- Compiler
	- text -> token -> Abstract syntax tree -> program -> flow of info
	- parsing source code - abstract syntax tree
	- flow of information/ analyze how program behaves - program dependence graph/ control flow graph
- clang-tidy - find bugs

What needed:
1. Richer information
	- Program dependence graph - tools to do this analysis
	- Python scalpel
2. What to use
	1. Cutting edge - not popular
	2. Python - pytest-testmon

What then:
1. RTS first step for patch validation
	1. Sanity check you do not break anything
	2. Even if bugs are not there, does not mean we fix new things
		1. Oracle problem - knowing what's correct is hard
	3. Functional correctness: doesn't break and fix things
	4. Non-Functional correctness: performance, clean code
2. Quality of Performance
3. Long lasting - Ship of athesi
	1. Idea lasts, even if original LOC no more
	2. Tool lasts, even if idea differs

Approach:
1. Something like Ekstazi to C/C++ or Python (LLM code)
	1. Python - more popular (LLM stuff)
		1. more meaningful semantics
		2. more training data
	2. C/ C++ - used to generate patches for vulnerable C program
2. Look at some other RTS techniques
	1. Some more semantic-based info - meaning of program
	2. Or information-based workflow
		1. Tracing how values passed and influence in other place
	3. More complicated than C/ C++
	4. Reason: Ekstazi not as popular
		1. Larger companies have in-house solutions

## 4 - Oct 10, 2024

**Implementing Ekstazi**

Required
- Infrastructure needed
- How to evaluate

What to think:
- Language
	- Python - Guest and Host
		- python type hints
- Tools to support language
	- scalpel https://github.com/SMAT-Lab/Scalpel
		- dep graph
		- checksum stored in some file
	- Profiling python - https://github.com/plasma-umass/scalene
	- Automated program repair - https://program-repair.org/benchmarks.html
	- Ruff: A Modern Python Linter for Error-Free and Maintainable Code
		- pylint replacement
	- UV - https://github.com/astral-sh/uv
	- cmake projects - cmake-init
	- pipx install
- Risk/ mitigation factors to incorporate to minimize pain
- Identify key tasks for Ekstazi to happen


## 5 - Oct 17, 2024

1. Code with not good documentation
    - Need to reverse Engineering
    - Think about sunk-cost fallacy
2. Observe and manipulate Python Program
    - Allow to construct dynamic analysis
    - Ex: Coverage tool in Python - dynamic analysis
        - Big array containing flag for each code block
        - Extra instruction - observability
    - Not much static reasoning tool in Python
    - Other tools for dynamic analysis
    - Can be Good enough for now if good enough
3. DevOps
    - Skills to instrument and reason about program tooling
4. Careful about time spent on project management structure
5. Identify high-level objectives bit-by-biy
    - Does the tool support what Ekstazi need to do
    - If the tool does not fullfil? change tools or add more tools?
    - Finding least bad set of tools that you might need
    - File hashing
        - To see if it changes
        - Get reasonable hashing


### Next steps:
1. Play around with pycg - usage in fully_qualified_name_inference.py
2. Get high-level objectives

### High-level objectives:
Bigger picture - patch validation

Core piece - regression test selection. Reasonable implementation of Ekstazi.
- Call graph makes sense - through the lens of patch validation. Focus on value-centre rather than cost-centre.
    - Value - decide whether patch is good or not
        - Get patch from LLM
        - Regression test selection/ validation from LLM - select subset of tests to run and validate it
- Identif


1. Check Portion of code that changes
2. Check influence flow of calls
3. How it impacts different unit tests
4. Selectively run the unit tests
5. Determine the result has changed before or after patch

Clear? Clarity? Ambiguous?