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
