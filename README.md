# AI-Powered Recruit: Intelligent Job Candidate Screening

**(Hackathon Project for Accenture Gen AI Sprint - Data and AI Week)**

This project implements a multi-agent AI system designed to automate and streamline the initial stages of the job candidate screening process, leveraging Generative AI (GenAI) and agentic principles. It aims to address the inefficiencies and potential errors associated with manual review of job descriptions and CVs.

## Problem Statement

Manual job screening is slow, inefficient, and prone to human error, hindering effective recruitment. High application volumes often overwhelm HR teams, creating a critical bottleneck that delays hiring and risks losing top talent. Automation is essential for speed and accuracy in today's fast-paced recruitment landscape.

## Proposed Solution

Our solution is an AI-powered, multi-agent system built using Python. It automates key screening tasks:

1.  **User Input (UI):** An HR user selects a Job Description CSV file, a CV folder, sets a shortlisting threshold, and chooses which job titles to process via a Tkinter-based graphical user interface.
2.  **CV Pre-processing:** The system reads all PDF CVs from the specified folder *once* and uses an Ollama LLM (e.g., Mistral) via the **CV Agent** to extract structured data (name, skills, experience, education, contact info).
3.  **JD Processing & Matching:** For each selected Job Title:
    *   The **JD Summarizer Agent** uses an Ollama LLM to summarize the corresponding Job Description, extracting key requirements.
    *   The **Shortlisting Agent** compares the summarized JD against *all* pre-processed CV data, calculating a skill-based match score for each candidate.
4.  **Shortlisting:** Candidates exceeding the user-defined threshold for the specific job title are identified.
5.  **Scheduling (Simulated):** The **Scheduler Agent** generates personalized interview request messages (printed to the UI) for shortlisted candidates.
6.  **Reporting:** A final CSV report is generated containing details (name, contact info, match score) for all processed candidates across all selected job titles.

## Features

*   **GUI:** User-friendly interface built with Tkinter for selecting files, setting parameters, and viewing results.
*   **JD Summarization:** Automatically extracts key requirements from job descriptions using Ollama LLMs.
*   **CV Data Extraction:** Parses PDF CVs and extracts structured data (including contact info) using Ollama LLMs.
*   **Skill-Based Matching:** Calculates a relevance score between candidate skills and job requirements.
*   **Automated Shortlisting:** Filters candidates based on a configurable match score threshold.
*   **Interview Request Generation:** Creates template-based interview invitation messages for shortlisted candidates.
*   **CSV Report Generation:** Exports a comprehensive report with candidate details and match scores.
*   **Efficient Processing:** Pre-processes CVs once to speed up screening against multiple job titles.
*   **Local LLM Execution:** Uses Ollama to run LLMs locally, enhancing data privacy.

## Technology Stack

*   **Python:** Main programming language.
*   **Ollama:** Framework for running LLMs locally.
    *   **Mistral (or similar):** LLM used for summarization and extraction.
*   **PyMuPDF (fitz):** For reading text from PDF files.
*   **Pandas:** For loading and handling CSV data (Job Descriptions).
*   **Tkinter:** For building the graphical user interface.
*   **CSV Module:** Python's built-in module for CSV export.
*   **Multi-Agent Design:** Implemented using Python classes.

## Setup and Installation

1.  **Clone the repository (or download the files):**
    ```bash
    # Replace with your actual repository URL if applicable
    git clone https://github.com/avinashg0y4l/AI-Powered-Recruit-Intelligent-Job-Candidate-Screening.git
    cd YOUR_REPOSITORY_NAME
    ```
2.  **Install Python:** Ensure you have Python 3.8 or higher installed ([https://www.python.org/](https://www.python.org/)).
3.  **Install Ollama:** Follow the instructions at [https://ollama.com/](https://ollama.com/) to install Ollama for your operating system.
4.  **Pull the LLM Model:** Download the model used by the agents (default is Mistral):
    ```bash
    ollama pull mistral
    ```
    *(If you used a different model, pull that one instead).*
5.  **Install Required Python Libraries:**
    *   **(Recommended) Create a virtual environment:**
        ```bash
        python -m venv venv
        # Activate the environment (Windows)
        .\venv\Scripts\activate
        # Activate the environment (macOS/Linux)
        source venv/bin/activate
        ```
    *   Install dependencies from `requirements.txt`:
        *(First, create a `requirements.txt` file with the following content):*
        ```requirements.txt
        ollama
        PyMuPDF
        pandas
        ```
        *(Then run the install command):*
        ```bash
        pip install -r requirements.txt
        ```

## How to Run

1.  **Navigate to the project directory** in your terminal (ensure your virtual environment is activated if you created one).
2.  **Run the main application:**
    ```bash
    python main.py
    ```
3.  **Use the UI:**
    *   The application window will appear.
    *   Use the "Select CSV File" button to choose your `job_description.csv` file.
    *   Use the "Select CV Folder" button to choose the folder containing your PDF CVs (e.g., `CVs1`).
    *   Adjust the "Shortlisting Threshold (%)" using the spinbox.
    *   Select/deselect the Job Titles you want to process using the checkboxes.
    *   Click "Start Job Screening".
    *   Processing results will appear in the "Results" text area.
    *   Once processing is complete, the "Generate CSV Report" button will be enabled. Click it to save the report.

## Future Enhancements

*   Improve matching algorithm beyond simple keyword matching (e.g., semantic similarity, experience weighting).
*   Implement more robust error handling and logging.
*   Enhance UI/UX design.
*   Integrate with Applicant Tracking Systems (ATS).
*   Implement actual email sending for interview requests.
*   Use a database (e.g., SQLite, PostgreSQL) for persistent storage.
*   Add more comprehensive testing.

## Team

*   **Team Name:** Raptor
*   **Team Leader:** Avinash Goyal
