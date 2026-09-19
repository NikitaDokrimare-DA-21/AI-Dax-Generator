# 📊 AI DAX Generator

An AI-powered tool that generates **paste-ready Power BI DAX code** — Measures, Calculated Columns, and Calculated Tables — grounded strictly in your own Power BI model schema. Built with **Streamlit** and **Google Gemini**, it turns a plain-English business requirement into validated, filter-context-aware DAX, complete with an explanation, assumptions, and validation steps.

## 🚀 Live Demo

[View Deployed App on Streamlit Cloud](https://nikitadokrimare-da-21-ai-dax-generator-app-sdx1sl.streamlit.app/)

## ✨ Features

- **📐 Schema-Grounded Generation** — Loads your actual Power BI model schema (`powerbi_schema.txt`) and only uses the tables, columns, and relationships defined there — no invented objects.
- **🧮 Multiple DAX Object Types** — Generate a **Measure**, **Calculated Column**, or **Calculated Table** from a single form.
- **📝 Plain-English Requirements** — Describe what the DAX should calculate in natural language (e.g. *"Calculate total sales after discount, including shipping cost"*).
- **✅ Optional Test Case Input** — Provide an expected result to help guide and validate the generated logic.
- **📋 Paste-Ready Output** — Automatically extracts clean DAX code from the AI response into a dedicated, copyable code block.
- **📖 Explanation & Validation** — Every generation includes a breakdown of the logic, filter-context behavior, assumptions made, and how to verify the result inside Power BI.
- **⬇️ Download DAX** — Export the generated DAX as a `.txt` file.
- **🛡️ Best-Practice Rules Enforced** — The AI is prompted to follow DAX best practices: `DIVIDE()` instead of `/`, `COALESCE()` over blank handling, readable `VAR` blocks, and preserved filter context.

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Frontend / App Framework | [Streamlit](https://streamlit.io/) |
| AI / LLM | [Google Gemini](https://ai.google.dev/) (`google-genai`) |
| Config / Secrets | [python-dotenv](https://pypi.org/project/python-dotenv/) |
| Language | Python |

## 📁 Project Structure

```
AI-Dax-Generator/
├── app.py                  # Main Streamlit application
├── gemini_service.py        # Gemini API wrapper/service layer
├── geminimodels.py          # Gemini model configuration
├── powerbi_schema.txt        # Your Power BI model schema (tables, columns, relationships, rules)
├── ecommerce (1).xlsx         # Sample dataset used to build/test the schema
├── requirements.txt           # Python dependencies
└── .gitignore
```

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/NikitaDokrimare-DA-21/AI-Dax-Generator.git
cd AI-Dax-Generator
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv venv
source  venv\Scripts\activate   
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up your Gemini API Key

Create a `.env` file in the project root and add your [Google Gemini API key](https://ai.google.dev/):

```
GEMINI_API_KEY=your_api_key_here
```

### 5. Add your Power BI schema

Edit `powerbi_schema.txt` with your own model's tables, columns, relationships, and business rules. The AI will only reference objects defined in this file — this is what keeps the generated DAX accurate and hallucination-free.

### 6. Run the app

```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`.

## 📖 Usage

1. Launch the app — it loads your `powerbi_schema.txt` automatically and displays it in an expandable panel for reference.
2. Choose the object type to create: **Measure**, **Calculated Column**, or **Calculated Table**.
3. Enter a name for the object (e.g. *"Total Sales"*).
4. Describe the business requirement in plain English.
5. *(Optional)* Add an expected result or test case to guide validation.
6. Click **Generate DAX**.
7. Review the generated, paste-ready DAX code, read the explanation/assumptions/validation notes, and download the result if needed.

## 📋 Requirements

- Python 3.9+
- A valid Google Gemini API key

See `requirements.txt` for the full list of Python packages:

```
streamlit>=1.40,<2.0
google-genai>=1.0,<2.0
python-dotenv>=1.0,<2.0
```

## 🔒 Notes

- Your `GEMINI_API_KEY` should **never** be committed to the repository — keep it in a local `.env` file (or your deployment platform's secrets manager), which is excluded via `.gitignore`.
- The quality of generated DAX depends directly on how complete and accurate `powerbi_schema.txt` is — keep it up to date with your actual Power BI model.
- The app will show an error and stop if `powerbi_schema.txt` is missing or empty.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/NikitaDokrimare-DA-21/AI-Dax-Generator/issues).


## 👤 Author

**Nikita Dokrimare**
[GitHub Profile](https://github.com/NikitaDokrimare-DA-21)
