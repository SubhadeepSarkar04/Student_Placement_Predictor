# 🎓 Student Placement Prediction Engine (Render)

An end-to-end Machine Learning web application designed to evaluate a student's campus placement probability based on core academic performance indicators, soft skills, technical proficiency, and program dedication. The system trains a Random Forest Classifier on a feature matrix and serves real-time binary classifications through a natively deployed Flask micro-service.

---

## 👤 Student Profile
* **Name:** Subhadeep Sarkar
* **Registration Number:** 23BAI10977
* **Course:** B.Tech Computer Science and Engineering
* **Institution:** VIT Bhopal University

---

## 🔗 Live Application Gateways
* **Production Live URL:** 
* **Source Repository:** https://github.com/SubhadeepSarkar04/Student_Placement_Predictor.git

---

## 🛠️ System Architecture & Frameworks
* **Language Core:** Python 3.10
* **Platform Layer:** Render Native Runtime (PaaS)
* **Inference Pipeline:** Scikit-learn, Pandas, NumPy
* **Application Framework:** Flask Microkernel
* **Production Gateway:** Gunicorn WSGI Web Server
* **Model Serialization:** Pickle Binary Format

---

## 📂 Project Directory Structure
This deployment relies completely on container virtualization layers to stand up the web app infrastructure natively, eliminating platform-specific routing dependencies like `Procfile` or `runtime.txt`:

```text
📁 Student-Placement-Docker/
│
├── 📁 static/
│   └── 📄 style.css            # Custom UI corporate layout template
│
├── 📁 templates/
│   └── 📄 index.html           # Main interactive user submission form
│
├── 📄 app.py                   # Production server app kernel & routing logic
├── 📄 train.py                 # Feature synthesis execution pipeline and model trainer
├── 📄 placement_model.pkl      # Serialized Random Forest Classifier binary
├── 📄 requirements.txt         # Plaintext python packaging manifest
├── 📄 Dockerfile               # Main container build rule file
└── 📄 .gitignore               # Excludes python local runtime caches and datasets

```

---

## 📊 Feature Matrix Mapping

Inputs submitted via the application web form are processed strictly as high-precision floats and integers, bypassing manual threshold logic or hardcoded scripts to run mathematical classifications inside the Random Forest decision tree layout:

| Input Variable Field | Data Metric Type | Value Bounds / Constraints |
| --- | --- | --- |
| **CGPA** | Continuous Float | Scale: `0.00` to `10.00` |
| **Communication Skills** | Continuous Float | Rating: `0.0` to `10.0` |
| **Resume Score** | Continuous Float | Rating: `0.0` to `10.0` |
| **Coding Score** | Continuous Float | Rating: `0.0` to `10.0` |
| **Placement Attendance** | Continuous Float | Percentage: `0.0%` to `100.0%` |

### Output Target Matrix

* **`0` -> Not Placed 😔**: Features mapped below the trained model classification thresholds.
* **`1` -> Placed 🎉**: Features successfully satisfied the predictive boundary conditions.

---

## ⚙️ Local Verification and Testing Instructions

### 1. Traditional Workspace Activation

Initialize local testing by setting up your local conda virtual runtime environment:

```bash
# Create a brand-new Conda environment named 'placement' with Python 3.10
conda create -n placement python=3.10 -y

# Activating your workspace profile
conda activate placement

# Pull dependencies directly into the local scope
pip install -r requirements.txt

# Run the training script to generate the model pkl file
python train.py

# Spin up the development microkernel
python app.py

```

Open `http://127.0.0.1:5000` in your web browser.

### 2. Native Cloud Web Service Deployment (Render)

This production repository utilizes automated cloud hooks linked directly to Render's Native Python Runtime.

1. Deployment Configuration Properties
When provisioning the Web Service on Render, use the following structural environment parameters:

Environment/Runtime: Python

Build Command: pip install -r requirements.txt

Start Command: gunicorn app:app

2. Execution Pipeline Behavior
Version Matching: Render detects runtime.txt automatically to provision a managed Linux environment running your explicit Python 3.10 sub-version.

Continuous Integration: The pipeline tracks updates to the repository using Git version history on the main branch, triggering an automated build phase on every push.

Gateway Upkeep: The system builds your inference pipeline dependencies from requirements.txt and launches the production Gunicorn web processes cleanly bound to public web gateway interfaces.
