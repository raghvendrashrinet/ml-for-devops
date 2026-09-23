Hard tab rule
Note:  use a literal Tab character to indent the command lines underneath a target. You cannot use spaces  
`requirements.txt`
```requirements.txt
pytest
pandas
scikit-learn
numpy
```

`Makefile`
```makefile
# fraud-detection Makefile
# Declare all targets as .PHONY to avoid file conflicts
.PHONY: all setup data train test clean help

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

help:
	@echo "Available commands:"
	@echo "  make setup   - Set up virtual environment and install dependencies"
	@echo "  make data    - Process raw data"
	@echo "  make train   - Train the ML model"
	@echo "  make test    - Run tests with pytest"
	@echo "  make clean   - Remove cache files and artifacts"
	@echo "  make all     - Run setup, data processing, training, and testing"

all: setup data train test  

```

Run
- `make all`
- `make setup`

`find . -type d -name "__pycache__" -exec rm -rf {} +` "recursively search from your current directory downwards, find all folders named __pycache__, and delete them all at once"
