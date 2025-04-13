# Solana-Audit: AI-Powered Smart Contract Auditor

An advanced AI-powered auditor for detecting vulnerabilities in smart contracts mainly **Solana (Rust/Anchor)** and **Ethereum (Solidity)** is also available to help others out. This project leverages a fine-tuned transformer (CodeBERT) alongside static analysis to provide detailed, actionable audit reports.

## Table of Contents
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [License](#license)

## Features
- **Dual-Platform Support:** Audits both Solidity (EVM) and Solana (Rust/Anchor) smart contracts.
- **ML-Based Vulnerability Detection:** Fine-tuned transformer (CodeBERT) classifier.
- **Hybrid Analysis:** Combines ML predictions with static analysis.
- **Detailed Reporting:** Provides vulnerability scores and actionable insights.
- **Continuous Improvement:** Incorporates user feedback and active learning.

## Installation

```bash
git clone https://github.com/yourusername/solana-audit.git
cd solana-audit

# Create and Activate a Virtual Environment

# Linux/WSL/macOS
python3 -m venv venv
source venv/bin/activate

# Windows (Command Prompt)
python -m venv venv
venv\Scripts\activate

# Install Dependencies
pip install -r requirements.txt
```

Ensure your `requirements.txt` file contains:

```
blinker==1.9.0
click==8.1.8
colorama==0.4.6
Flask==3.1.0
itsdangerous==2.2.0
Jinja2==3.1.6
joblib==1.4.2
MarkupSafe==3.0.2
numpy==1.24.3
scikit-learn==1.6.1
scipy==1.15.2
threadpoolctl==3.6.0
Werkzeug==3.1.3
transformers==4.30.0
torch==2.2.2
requests==2.32.2
accelerate>=0.26.0
datasets==3.5.0
```

## Usage

### Training the Model

Place your dataset at `data/vulnerabilities.csv` formatted as:

```csv
"code","label"
"pragma solidity ^0.8.0;\ncontract ReentrancyAttack {\n    // code...\n}",1
"pragma solidity ^0.8.0;\ncontract SafeVault {\n    // code...\n}",0
```

Run the training script:

```bash
python train_codebert.py
```

### Running an Audit

#### CLI Audit

```bash
python audit.py --contract path/to/your_contract.sol
```

#### Flask Dashboard

```bash
# Activate virtual environment
source venv/bin/activate

# Set Flask app environment
# Linux/WSL
export FLASK_APP=frontend/app.py

# Windows (Command Prompt)
set FLASK_APP=frontend/app.py

# Run Flask Dashboard
flask run
```

Open [http://127.0.0.1:5000](http://127.0.0.1:5000).

## Project Structure

```
solana-audit/
├── frontend/
│   └── app.py
├── audit.py
├── data/
│   └── vulnerabilities.csv
├── fine_tuned_codebert/
├── requirements.txt
├── train_codebert.py
└── README.md
```

## Dependencies
- **PyTorch**
- **Transformers & Datasets**
- **Accelerate**
- **scikit-learn**
- **Flask**
- **joblib, numpy, pandas**

## Contributing

Open issues or submit pull requests with improvements or features.

## License

MIT License

## Final Instructions

1. Clone the repo and set up your environment.
2. Install dependencies: `pip install -r requirements.txt`
3. Prepare your dataset at `data/vulnerabilities.csv`.
4. Run the training script: `python train_codebert.py`
5. Audit contracts using CLI or Flask Dashboard.
