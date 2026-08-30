# AIOps Module 1 – Assignment 1

This repository contains the implementation, experiments, evidence, and documentation for **AIOps Module 1 – Assignment 1**.

aiops-assignment1-q4/
│
├── .dvc/
├── q2-mlflow-images/
├── q3_terminal_ss/
├── q4_mlflow_logs/
│
├── .dvcignore
├── .gitignore
├── data.csv.dvc
│
├── q3_proof_rollback.png
├── aiops-assignment1-q1234.mp4
├── AIOps - Module 1 Assignment_report.pdf
│
├── README.md
└── AI_DISCLOSURE.md

# Important Files and Folders
* .dvc/ – DVC configuration and metadata.
* data.csv.dvc – DVC metadata used to track the dataset.
* q2-mlflow-images/ – MLflow screenshots and supporting evidence for Q2.
* q3_terminal_ss/ – Terminal screenshots for Q3.
* q3_proof_rollback.png – Evidence of dataset rollback.
* q4_mlflow_logs/ – MLflow-related evidence for Q4.
* AIOps - Module 1 Assignment_report.pdf – Final assignment documentation.
* aiops-assignment1-q1234.mp4 – Demonstration video.
* AI_DISCLOSURE.md – Disclosure regarding the use of generative AI

# Prerequisites
The following tools are required for the workflows:
- Git
- Conda / Anaconda / Miniconda
- Python
- DVC
- MLflow

# Q4 – Reproducible MLflow Experiment
Person A
Name: Shivarchitha
Roll Number: DA24B052

Person A performed the original Q4 workflow, including:

* Setting up the required environment.
* Obtaining the required dataset using DVC.
* Running the training code.
* Tracking the experiment using MLflow.
* Recording the resulting metric.
* Registering the trained model.
* Providing the information required for Person B to reproduce the experiment.

Person B
Name: Vallem Keerthi Reddy
Roll Number: DA24B051

Person B performs the reproduction workflow by:

* Cloning the repository.
* Recreating the required environment.
* Pulling the dataset using DVC.
* Running the same training code.
* Checking the MLflow run.
* Comparing the reproduced metric with Person A's metric.
* Recording the comparison in MLflow.
  
# Q4 – Environment Note

* Important: Person A completed Part A of Q4 on a Windows environment.

* The environment.yml committed to this repository was exported from Person A's Windows environment.

* Therefore, the environment file contains Windows-specific dependencies such as:

pywin32
vc
vc14_runtime
vs2015_runtime
win_inet_pton
getopt-win32

* It also contains a Windows-specific Conda environment prefix.
* Because of these Windows-specific dependencies:
*Windows is recommended for reproducing Q4 using the provided environment.yml.
* Attempting to recreate the exact environment directly on Linux may result in Conda dependency-resolution errors because some of the packages in the exported environment are Windows-specific.

# Q4 – Environment Setup
1. Install Conda

* Install either: Miniconda/Anaconda on the Windows system.

* After installation, open: Anaconda Prompt or Miniconda Prompt

Verify Conda:
conda --version

2. Clone the Repository
git clone https://github.com/shivaarchithavudutha/aiops-assignment1-q4.git
Move into the repository:
cd aiops-assignment1-q4

3. Create the Environment

Create the environment using the provided environment file:

conda env create -f environment.yml

Activate the environment:

conda activate aiops-q4-env

Verify Python:

python --version
If the Environment Already Exists

If Conda displays:

CondaValueError: prefix already exists

the environment has already been created.

Activate the existing environment instead:

conda activate aiops-q4-env

There is no need to create the environment again.

Q4 – Configure DVC

* The dataset is retrieved through the configured DVC remote.

* After activating the environment, configure the DVC remote credentials locally:

dvc config --local remote.b2remote.access_key_id <ACCESS_KEY>
dvc config --local remote.b2remote.secret_access_key <SECRET_KEY>

* Security: Replace the placeholders with the credentials provided in the actual repository. Do not commit the actual credentials to GitHub.

* Check the configured DVC remote:

dvc remote list

* Pull the dataset:

dvc pull

* If dvc pull displays an error stating that S3 support is required, install the DVC S3 extension:

pip install "dvc[s3]"

* Then retry:

dvc pull

* Q4 – Run the Training

* Once the environment has been activated and the dataset has been retrieved:

python train.py

Q4 - MLflow server 

* In other terminal start MLflow server with the same port as mentioned in the training script .
* Start ML flow server in the same environment .
* 
