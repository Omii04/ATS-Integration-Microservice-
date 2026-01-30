# ATS Integration Microservice (Greenhouse)

This service provides a unified API for managing jobs and candidates, integrated with **Greenhouse ATS**.
It is built using Python 3.9 and designed to be compatible with the Serverless Framework.

## Features

- **GET /jobs**: Fetch open jobs from Greenhouse (supports Mock Mode and Pagination).
- **POST /candidates**: Create a new candidate and apply them to a job.
- **GET /applications**: List applications for a specific job.

## Prerequisites

- Python 3.9+
- Pip (Python Package Manager)
- **Greenhouse Harvest API Key** (Optional for testing)

## Quick Start (Local Runner)

Due to Windows environment compatibility, we recommend using the included `local_runner.py` for development.

1. **Install Dependencies**:
   ```powershell
   pip install flask requests python-dotenv
   ```

2. **Configure Environment**:
   - The system automatically uses **Mock Mode** (dummy data) if no API key is provided.
   - To use real data, open `.env` and paste your key:
     ```env
     ATS_API_KEY=your_actual_api_key_here
     ```

3. **Run the Service**:
   ```powershell
   python local_runner.py
   ```
   The API will be available at `http://localhost:5000`.

## API Endpoints

### 1. Get Jobs
```bash
curl http://localhost:5000/dev/jobs
```

### 2. Create Candidate
```bash
curl -X POST http://localhost:5000/dev/candidates \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Jane Doe",
    "email": "jane.doe@example.com",
    "phone": "555-0199",
    "resume_url": "https://example.com/resume.pdf",
    "job_id": "12345"
  }'
```

### 3. Get Applications
```bash
curl "http://localhost:5000/dev/applications?job_id=12345"
```
