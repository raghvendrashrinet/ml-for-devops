Hard tab rule
Note:  use a literal Tab character to indent the command lines underneath a target. You cannot use spaces
```makefile
# fraud-detection Makefile

# Declare all targets as .PHONY to avoid file conflicts
.PHONY: all setup data train test clean

setup:
        python3 -m venv mlops-venv && mlops-venv/bin/pip install -r requirements.txt

data:
        python src/data/process_data.py

train:
        python src/models/train.py

test:
        pytest tests/

clean:
        find . -type d -name "__pycache__" -exec rm -rf {} +
        rm -rf .pytest_cache
        rm -rf models/*

all: setup data  train test
~                           

```

Run
- `make all`
- `make setup`

`find . -type d -name "__pycache__" -exec rm -rf {} +` "recursively search from your current directory downwards, find all folders named __pycache__, and delete them all at once"
