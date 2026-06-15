## Ruff and Black 
Automation tools used in Python development to keep code clean, readable, and error-free

#### 🖤 What is Black?  
Black is known as the "uncompromising Python code formatter".Role: It is strictly a formatter. It does not check for bugs; it only rewrites the physical layout of your code (e.g., fixing indentation, line wrapping, changing single quotes to double quotes, and adjusting spacing)

#### 🦀 What is Ruff?  
Ruff is a modern, all-in-one linter and formatter built by Astral,Role: It does two things at once. It lints your code (checks for actual programming errors, dead code, unused imports, or security flaws), and it formats your code  

In modern Python pipelines, Ruff has largely become the industry favorite because it combines multiple utilities into a single, lightning-fast execution block

1. Add to your `requirements.txt`:  
   ```requirements.txt
   ruff  
   black
   ```
2. Update your Makefile to include a lint target:
   ```makefile
   .PHONY: all setup lint data train test clean

   all: setup lint data train test

   setup:
	    python3 -m venv mlops-venv
	    mlops-venv/bin/pip install -r requirements.txt

   lint:
	    # Ruff checks for bugs/errors, Black fixes layout spacing
	    mlops-venv/bin/ruff check src/
	    mlops-venv/bin/black --check src/

   Your remaining data, train, test, and clean targets go here...
   ```


---

PYPROJECT.TOML

`pyproject.toml : `file is the modern, standardized configuration file used for Python projects. It replaces old legacy files like `setup.py`, `requirements.txt`, `setup.cfg`, and tool-specific configuration files (like .flake8).By creating this single file in your project root, you can configure your packaging, dependencies, and code quality tools like Ruff and Black all in one place.
```pyproject.toml
[tool.black]
line-length = 88
target-version = ['py310']

[tool.ruff]
target-version = "py310"
line-length = 88

[tool.ruff.lint]
select = ["E", "F", "I"]  # Enforce basic style rules, error checks, and import sorting
```



---
### Excercise day6: 
The project at /root/code/fraud-detection/ contains a pyproject.toml and sample sources under src/.

The corrected project must meet the following requirements:

-`ruff` and `black` are both configured with a line length of 120.
- `ruff` lint rule selection includes E, F, W, and I, and is declared under [tool.ruff.lint] – The schema required by ruff 0.1 and later.
- Running ruff check src/ from the project directory exits with status 0.
- Running black --check src/ from the project directory exits with status 0.

```pyproject.toml
[project]
name = "fraud-detection"
version = "0.1.0"

[tool.black]
line-length = 120

[tool.ruff]
line-length = 120

[tool.ruff.lint]
select = ["E", "F", "W", "I"]
```  

Formatting the Code to Exit with Status 0  
```bash
# 1. Automatically sort imports and auto-fix style errors/warnings
ruff check src/ --fix

# 2. Automatically reformat files to the exact 120 line length standard
black src/
```

Verifying Success  
```bash
ruff check src/
black --check src/
```
