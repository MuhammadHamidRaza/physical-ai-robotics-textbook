# Quickstart Guide: Physical AI & Humanoid Robotics Textbook

This guide provides instructions to quickly set up and run the Physical AI & Humanoid Robotics Textbook project.

## Prerequisites

- Node.js (v18+)
- Python (v3.9+)
- npm or yarn
- pip or poetry
- Git
- Docker (optional, for local FastAPI deployment)
- Qdrant Cloud account (free tier)
- Better-Auth account (for authentication)

## Setup

1.  **Clone the repository**:

    ```bash
    git clone [YOUR_REPO_URL]
    cd 001-physical-ai-robotics-book
    ```

2.  **Docusaurus Frontend Setup**:

    ```bash
    cd docusaurus-book
    npm install # or yarn install
    npm start   # or yarn start
    ```

    This will start the Docusaurus development server. The book should be accessible at `http://localhost:3000`.

3.  **FastAPI Backend Setup**:

    ```bash
    cd fastapi-backend
    python -m venv venv
    source venv/bin/activate # On Windows: .\venv\Scripts\activate
    pip install -r requirements.txt # (assuming requirements.txt will be generated)
    uvicorn src.main:app --reload
    ```

    This will start the FastAPI development server, typically at `http://localhost:8000`.

4.  **Environment Variables**:

    Create `.env` files in `docusaurus-book/` and `fastapi-backend/` as needed for API keys (e.g., Better-Auth, Qdrant) and other configurations.

## Deployment

Deployment to GitHub Pages for the Docusaurus book will be handled via GitHub Actions. Deployment for the FastAPI backend will require a cloud hosting provider (e.g., AWS, GCP, Azure, Render).

## Usage

- Access the textbook through the Docusaurus frontend.
- Interact with the embedded RAG chatbot.
- Register/Login using the Better-Auth integration.
- Experiment with content personalization and Urdu translation features.

