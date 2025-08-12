# 🧠 SOKE Graph: A Semantic-linked Ontological Framework for Domain-Specific Knowledge Discovery in Scientific Literature

SOKE Graph is a powerful, end-to-end pipeline designed to extract structured knowledge from scientific PDFs using ontology-driven classification and AI-assisted language models. It enables automated discovery and categorisation of domain-specific information—such as catalyst types, reaction conditions, and performance metrics—by parsing research papers, classifying concepts across multiple layers (e.g., Process, Environment, Reaction), and storing the results in a knowledge graph.

This tool can be tailored for accelerating literature analysis in any domain of research; in our case, we have focused on material science fields like green hydrogen production and water electrolysis.


## 🚀 Features

- 🔍 **Retrieve papers** from Semantic Scholar or your PDF collection
- 🤖 **Use AI (OpenAI, Gemini, ...)** to extract ontological concepts and metadata
- 📊 **Rank papers** based on query relevance and extracted metadata
- 🧱 **Build knowledge graphs** (Neo4j supported) from structured paper data

---
# 🚀 How to Run This Python Project on Windows, macOS, and Linux

This guide will walk you through running this project on your computer, regardless of your operating system or prior Python knowledge.

---

## Step 1: Install Python

Python is the programming language this project uses.

- **Download Python 3.x here:** https://www.python.org/downloads/  
- Make sure you download **Python 3** (not Python 2).

### Windows Users
- When installing Python, **make sure to check the box "Add Python to PATH"** on the installer screen!  
- If you forget this step, your computer won’t recognize Python commands.

### macOS Users
- Python 3 is often pre-installed, but it may be an older version.  
- Recommended: install the latest Python 3 via [Homebrew](https://brew.sh/):
  ```bash
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  brew install python
  ```
### Linux Users

- Most Linux distributions come with Python installed.

- To install or upgrade, use your package manager.

- For Ubuntu/Debian:

  ```bash
  sudo apt update
  sudo apt install python3 python3-venv python3-pip
  ```
## Step 2: Open the Command Line / Terminal

You'll be able to enter commands here.

- **Windows:** Press `Win + R`, type `cmd`, and press Enter to open Command Prompt.  
  Or, press `Win + X`, then select **Windows PowerShell** or **Windows Terminal** if installed.

- **macOS:** Press `Cmd + Space`, type `Terminal`, and press Enter.

- **Linux:** Look for the Terminal app in your applications menu, or press `Ctrl + Alt + T`.

---

## Step 3: Clone the Project (Download the Code)

In the command line window you opened, type:

```bash
git clone https://github.com/sanakashgouli/SOKEGraph.git
```

If you get an error saying `git` is not found:

- **Windows:** Download and install [Git for Windows](https://git-scm.com/download/win).

- **macOS:** Install via Homebrew with:

  ```bash
  brew install git
  ```

- **Linux:** Install with:

  ```bash
  sudo apt install git
  ```
  (For Ubuntu/Debian, or use your distro’s package manager.)

  After cloning, navigate into the project folder:
  ```bash
  cd SOKEGraph
  ```
---

## Step 4: Create a Virtual Environment (Isolate Dependencies)

This keeps the project’s Python packages separate from your system.

### Windows Users

In Command Prompt or PowerShell, run:

```powershell
python -m venv venv
```
If python is not recognized, try:

```powershell
py -3 -m venv venv
```
### macOS / Linux Users
Run:

```bash
python3 -m venv venv
```

---

## Step 5: Activate the Virtual Environment

You'll need to activate this environment every time before you run the project.

### Windows Users

- In Command Prompt, run:
  
```cmd
venv\Scripts\activate
```
- In PowerShell:
  
```powershell
venv\Scripts\Activate.ps1
```
> If you see an error about script execution policies in PowerShell:
Run this command once to allow scripts:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
Then activate again.
### macOS / Linux Users
Run:
```bash
source venv/bin/activate
```

---

## Step 6: Install Project Dependencies
With the virtual environment active (you should see (venv) at the start of your prompt), install packages:
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

---

## Step 7: Run the Project
You can choose the method that best fits your skills and setup. For most users, **Streamlit app is the easiest way** to get started.

---

### 1️⃣ Run with Streamlit App – `streamlit-app.py`

A simple, user-friendly graphical interface that lets you run the whole pipeline **without writing any code**.

#### How to run:

```bash
streamlit run streamlit-app.py
```
- Choose your **paper source**:  
  `Semantic Scholar`, `PDF ZIP`, or `Journal API`.

- Upload or select required files:
  - Paper queries
  - Ontology file
  - Keywords list
  - API keys (AI + Journal API)
  - Neo4j credentials (optional)

- Select an AI agent:
  - `openAI`, `gemini`, `llama`, `ollama`, or `claude`

- Choose your knowledge graph backend:
  - `neo4j` or `networkx`

- Run the full pipeline:
  - **Fetch → Enrich → Rank → Build Graph**

- View logs, ranked papers, and results directly in the UI.

---
  
## Step 8: Deactivate Virtual Environment (Optional)
When done working, you can leave the environment by running:
```bash
<<<<<<< HEAD
deactivate
```
=======
# 1. Install dependencies (if needed)
pip install -r requirements.txt

# 2. Launch the Streamlit UI
streamlit run streamlit-app.py
```
---

### 🦙 Using Ollama Locally
#### ✅ Step 1: Install Ollama
Install Ollama from the official site or using the command line:

Website (all OS): https://ollama.com/download

macOS (via Homebrew):
```bash
brew install ollama
```

Linux (via script):
```bash
curl -fsSL https://ollama.com/install.sh | sh
```


#### 🚀 Step 2: Pull and Run the Model
Once installed, pull the model you want and run the Ollama server locally:
```bash
ollama run llama3
```

### Pipeline Steps:
1. **Initialize AI agent** (OpenAI or Gemini)
2. **Fetch papers** (from Semantic Scholar or a zip of PDFs)
3. **Update ontology** with AI-based enrichment
4. **Rank papers** based on extracted metadata and keywords
5. **Build knowledge graph** (Neo4j)

---

## 📂 Output

The pipeline will generate:
- `updated_ontology.json`: AI-enriched ontology
- `ranked_papers.csv`: Paper ranking results
- Neo4j graph: If configured with valid credentials

---

## 🧠 Base Ontology: What It Is & How It Works

The base ontology is a user-defined `.json` file that provides a structured vocabulary for your domain. It acts as the conceptual backbone of the SOKEGraph pipeline, enabling semantic understanding, paper ranking, and knowledge graph construction.

### 📚 What Is an Ontology?

An ontology is a hierarchical organization of concepts relevant to a scientific or technical field. It typically includes:

- High-level layers (e.g., Environment, Process, Material, Application)
- Categories under each layer
- Keyword patterns or synonyms that help detect these categories in paper texts

This structure allows the system to semantically tag and classify papers—even when different terminology is used.

### 📁 File Format & Example Structure

The ontology must be defined as a `.json` file using this structure:

```json
{
  "CategoryName": {
    "Subconcept1": ["keyword1", "synonym1", "variant1"],
    "Subconcept2": ["keyword2", "synonym2"]
  }
}
```
---

## 🔐 API Keys & Credentials

- Place your **OpenAI** or **Gemini** API keys in a JSON file: `ai_keys.json`
- Neo4j credentials should be stored in: `neo4j_credentials.json`

Example:
```json
{
  "neo4j_uri": "bolt://localhost:7687",
  "neo4j_user": "neo4j",
  "neo4j_pass": "your_password"
}
```

---

## 🙋‍♀️ Contributions

Feel free to open issues or pull requests. Let’s improve this together!

---

## 📄 License

MIT License © 2025 [NRC]

---


>>>>>>> 2a6c623f5b26d8d6cf1fb2697f0114c1c33f6ddd
