# Fullstack PDF Application

This application allows users to upload PDF files, extract text from them, and ask questions about the content using OpenAI's language model.

## Table of Contents

- [Setup Instructions](#setup-instructions)
- [API Documentation](#api-documentation)
- [Application Architecture](#application-architecture)

## Setup Instructions

### Prerequisites

- Python 3.8+
- Node.js 14+
- npm or yarn
- OpenAI API Key

### Backend Setup

1. **Clone the repository:**

    ```bash
    git clone https://github.com/yourusername/fullstack-pdf.git
    cd fullstack-pdf
    ```

2. **Create and activate a virtual environment:**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. **Install the dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4. **Set up environment variables:**

    Create a `.env` file in the root directory and add your OpenAI API key:

    ```env
    OPENAI_API_KEY=your_openai_api_key_here
    ```

5. **Run the backend server:**

    ```bash
    uvicorn main:app --reload
    ```

### Frontend Setup

1. **Navigate to the frontend directory:**

    ```bash
    cd frontend
    ```

2. **Install the dependencies:**

    ```bash
    npm install
    ```

3. **Run the frontend server:**

    ```bash
    npm start
    ```

The application should now be running on `http://localhost:3000` with the backend server running on `http://localhost:8000`.

## API Documentation

### Upload PDF

- **URL:** `/upload/`
- **Method:** `POST`
- **Request:**
  - `file`: PDF file to upload
- **Response:**
  - `filename`: Name of the uploaded file
  - `text`: Extracted text from the PDF

### Ask Question

- **URL:** `/question/`
- **Method:** `POST`
- **Request:**
  - `document_id`: ID of the document
  - `question`: Question to ask about the document content
- **Response:**
  - `answer`: Answer generated by OpenAI

## Application Architecture

### Backend (FastAPI)

- **Main Libraries:**
  - FastAPI: Web framework for building APIs
  - PyMuPDF (fitz): Library to extract text from PDFs
  - OpenAI: API to interact with OpenAI's language models
  - dotenv: To load environment variables from a .env file
  - UUID: To generate unique document IDs

- **Structure:**
  - `main.py`: Contains API endpoints and business logic
  - `requirements.txt`: Lists Python dependencies

### Frontend (React)

- **Main Libraries:**
  - React: JavaScript library for building user interfaces
  - Tailwind CSS: Utility-first CSS framework for styling
  - Fetch API: To make HTTP requests to the backend

- **Structure:**
  - `src/components`: Contains React components (`Header`, `FileUpload`, `QuestionForm`)
  - `src/App.js`: Main application component
  - `src/index.css`: Global styles, including Tailwind CSS imports

### Workflow

1. User uploads a PDF file via the frontend.
2. The backend extracts text from the PDF and returns it to the frontend along with a document ID.
3. User submits a question about the document content.
4. The backend processes the question using OpenAI's language model and returns the answer.
5. The frontend displays the answer to the user.
