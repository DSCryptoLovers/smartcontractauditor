# Solana-Audit: AI-Powered Smart Contract Auditor

An advanced AI-powered auditor for detecting vulnerabilities in smart contracts on both **Solana (Rust/Anchor)** and **Ethereum (Solidity)** platforms. This project leverages a fine-tuned transformer (CodeBERT) alongside static analysis to provide detailed, actionable audit reports.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
  - [Training the Model](#training-the-model)
  - [Running an Audit](#running-an-audit)
- [Project Structure](#project-structure)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [License](#license)

## Features

- **Dual-Platform Support:** Audits both Solidity (EVM) and Solana (Rust/Anchor) smart contracts.
- **ML-Based Vulnerability Detection:** Fine-tuned transformer (CodeBERT) classifier to detect vulnerabilities.
- **Hybrid Analysis:** Combines ML predictions with rule-based static analysis for comprehensive results.
- **Detailed Reporting:** Generates vulnerability scores and detailed breakdowns with actionable insights.
- **Continuous Improvement:** Designed to incorporate user feedback and active learning to update the training data.

## Installation

### Prerequisites

- Python 3.10+
- A Linux-like environment is recommended (WSL works well on Windows)
- Virtual Environment (recommended)

### Clone the Repository

```bash
git clone https://github.com/yourusername/solana-audit.git
cd solana-audit

Create and Activate a Virtual Environment

On Linux/WSL/macOS:

python3 -m venv venv
source venv/bin/activate

On Windows (Command Prompt):

python -m venv venv
venv\Scripts\activate

Install Dependencies

Ensure your requirements.txt file contains the following:

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

Then run:

pip install -r requirements.txt

Usage
Training the Model
Prepare the Dataset:
Ensure your dataset file is placed at data/vulnerabilities.csv and is formatted as follows:

"code","label"
"pragma solidity ^0.8.0;
contract ReentrancyAttack {
    // multi-line code here...
}",1
"pragma solidity ^0.8.0;
contract SafeVault {
    // multi-line code here...
}",0

Run the Training Script:

python train_codebert.py

The script will:

Load and clean the CSV data.

Create HuggingFace datasets.

Fine-tune CodeBERT.

Evaluate the model and save it to the fine_tuned_codebert directory.

Running an Audit
After training, you can run an audit on a contract through one of two methods:

Command-Line Audit
If you have a CLI audit script (e.g., audit.py), run:

python audit.py --contract path/to/your_contract.sol

Web Dashboard (Optional)
If using a Flask-based dashboard:

Set the Flask entry point:

export FLASK_APP=app.py

Run the dashboard:

flask run

Open your browser at http://127.0.0.1:5000 and upload a contract file.

Project Structure

solana-audit/
├── app.py                   # (Optional) Flask web interface
├── audit.py                 # (Optional) CLI tool for audits
├── data/
│   └── vulnerabilities.csv  # Labeled dataset of smart contracts (code, label)
├── fine_tuned_codebert/     # Directory for the saved fine-tuned model
├── requirements.txt         # Project dependencies
├── train_codebert.py        # Training script for the CodeBERT classifier
└── README.md                # This documentation file

Dependencies
Key dependencies include:

PyTorch: The backend for transformer models.

Transformers & Datasets: For model fine-tuning and data processing.

Accelerate: For efficient training hardware management.

scikit-learn: For data splitting and metric calculations.

Flask: (Optional) For providing a web dashboard.

Contributing

Contributions are welcome! Please open issues or submit pull requests with bug fixes, enhancements, or new features. See the CONTRIBUTING.md file for guidelines.

License
This project is licensed under the MIT License.

## Final Notes

- Follow the instructions above to set up your environment, train the model, and run audits.
- Ensure that your dataset (`data/vulnerabilities.csv`) follows the prescribed format.
- For further instructions, refer to this README.
