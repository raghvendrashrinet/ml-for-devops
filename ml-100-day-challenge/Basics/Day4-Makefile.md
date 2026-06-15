Hard tab rule
Note:  use a literal Tab character to indent the command lines underneath a target. You cannot use spaces
```makefile
# fraud-detection Makefile

# Declare all six target names as phony to prevent file conflicts
.PHONY: setup data train test clean all

setup:
        python3 -m venv mlops-venv && mlops-venv/bin/pip install -r requirements.txt

data:
         python src/data/process_data.py

train:
        python src/models/train.py

test:
        pytest tests/

clean:
        rm -rf __pycache__

all: setup train test
```

Run
- `make all`
- `make setup`
