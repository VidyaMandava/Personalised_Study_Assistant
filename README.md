# Personalised Study Assistant with Adaptive MCQs

This repository contains a **Study Assistant** application built using [LangChain](https://github.com/hwchase17/langchain) with **LCEL** (LangChain Expression Language), an **open-source Gemini model**, and **PyPDF2**. The system performs the following tasks:

1. **PDF Parsing**: Extracts text from a PDF in Google Drive.  
2. **Summary Generation**: Produces a concise summary of a user-provided topic, strictly from the extracted study material.  
3. **Adaptive MCQs**: Presents 10 multiple-choice questions that adapt in difficulty based on the student’s answers—starting with a medium difficulty question and adjusting up or down after each response.

## Table of Contents
- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [License](#license)

---

## Features

- **PDF Extraction**: Uses `PyPDF2` to read and extract text from PDF files stored in Google Drive.  
- **Open-Source Gemini Model**: Loads Gemini model .  
- **Adaptive Quiz**: The difficulty of MCQs (easy, medium, hard) increases or decreases based on whether the user answers correctly.  
- **Interactive Prompts**: Users can interact in a console-like environment, inputting answers and receiving immediate feedback.

---

## Architecture

```
 ┌─────────────────┐      ┌────────────────────────┐
 │     Google      │      │                        │
 │     Drive       │      │    Gemini Model        │
 └────────┬────────┘      └──────────┬─────────────┘
          │                          │
          │                          │
 ┌────────▼────────┐  Extract   ┌────▼─────┐  Summaries/MCQs
 │   PyPDF2        ├────────────►  LangChain ├─────────────►  User
 └─────────────────┘             └───────────┘
     PDF to text             (LCEL + Gemini)
```

---

## Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/Personalised_Study_Assistant.git
   cd Personalised_Study_Assistant
   ```
2. **Install Dependencies**:  
   Ensure you have Python 3.8+ installed. Then install the required packages:
   ```bash
   pip install -r requirements.txt
   ```
   Or manually:
   ```bash
   pip install langchain PyPDF2 ipython
   ```

3. **Mount Google Drive (if using Colab)**:  
   In a Google Colab notebook, run:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
   Make sure your PDF is in `/content/drive/MyDrive/` or another accessible path.

---

## Usage

1. **Open the Notebook**:  
   - `Personalised_Study_Assistant.ipynb` in Google Colab or Jupyter.

2. **Set PDF Path & Topic**:  
   - Update `pdf_path` with the location of your PDF on Google Drive.  
   - Set `topic` to whatever you’d like to summarize and generate MCQs for.

3. **Run the Pipeline**:  
   - The pipeline will extract text from the PDF, generate a summary, and then ask you 10 MCQs.  
   - Answer each MCQ by typing A, B, C, or D in the console prompt.

4. **Adaptive Difficulty**:  
   - Each correct answer increases difficulty (up to `hard`), and each incorrect answer decreases difficulty (down to `easy`).

5. **Review Results**:  
   - At the end, you’ll see your **Final Score** out of 10.

---

## Project Structure

```
study-assistant/
├── Personalised_Study_Assistant.ipynb    # Example Colab/Jupyter notebook
├── README.md                # Project documentation
├── requirements.txt         # Dependencies
└── ...
```

- **`study_assistant.ipynb`**: Main notebook demonstrating the entire pipeline (PDF extraction, summary chain, MCQ chain).  
- **`requirements.txt`**: Lists required libraries (LangChain, PyPDF2, etc.).  
- **`README.md`**: This file, providing an overview and usage instructions.

---

## License

This project is licensed under the [MIT License](LICENSE). You’re free to use, modify, and distribute it as per the license terms.

---

### Acknowledgments
- [LangChain](https://github.com/hwchase17/langchain) for the flexible prompt/chaining interface.
- [PyPDF2](https://pypi.org/project/PyPDF2/) for PDF parsing.

Feel free to reach out via [GitHub Issues](https://github.com/your-username/Personalised_Study_Assistant/issues) if you have questions or suggestions!

---

**Happy Learning!**
