<<<<<<< HEAD
=======
---
title: LLM Analysis Quiz
emoji: 🧠
colorFrom: blue
colorTo: yellow
sdk: docker
app_port: 7860
license: mit
pinned: false
---

>>>>>>> 7a51db6b8add7e31fcf399ab5854886cc01b56c5
# LLM Analysis Quiz Solver

A complete backend system for solving LLM analysis quizzes automatically. The system uses FastAPI for the server, Playwright for JS-rendered pages, and intelligent heuristics to extract, analyze, and submit quiz answers.

## Features

<<<<<<< HEAD
- ✅ **FastAPI Backend**: Async REST API with `/solve` endpoint
- ✅ **Playwright Integration**: Handles JavaScript-rendered quiz pages
- ✅ **Multi-format Support**: CSV, PDF, Excel, JSON, images, and text files
- ✅ **Automatic Chain Solving**: Automatically progresses through quiz chains
- ✅ **Intelligent Answer Extraction**: Multiple strategies for finding answers
- ✅ **Error Handling & Retries**: Robust error handling with retry logic
- ✅ **Comprehensive Logging**: Detailed logging for debugging
- ✅ **Secret Validation**: Secure authentication with secret keys

## Project Structure

```
llm-quiz-agent/
├── app/
│   ├── __init__.py
│   ├── main.py          # FastAPI application and endpoints
│   ├── solver.py        # Quiz solving logic
│   ├── scraper.py       # Playwright automation
│   ├── utils.py         # File downloads, decoding, analysis
│   └── config.py        # Configuration and environment variables
├── tests/               # Test files
├── requirements.txt     # Python dependencies
├── .env                # Environment variables (create from .env.example)
├── .env.example        # Example environment file
├── README.md           # This file
└── LICENSE             # MIT License
```
=======
- *FastAPI Backend* — Async REST API with /solve endpoint
- *Playwright Integration* — Handles JavaScript-rendered quiz pages
- *Multi-format Support* — CSV, PDF, Excel, JSON, images, text files
- *Automatic Chain Solving* — Solves multi-step quizzes automatically
- *Multiple Answer Strategies* — File parsing, regex, pattern matching
- *Secure Secret Validation* — Prevents unauthorized access
- *Logging & Error Handling* — Robust retries and debugging support

## Project Structure


Project-LLM-Analysis-Quiz/
├── LICENSE
├── README.md
├── .gitignore
├── requirements.txt
├── Dockerfile
├── run.py
│
├── app/
│   ├── __init__.py
│   ├── config.py      # Environment variables, settings
│   ├── main.py        # FastAPI entry point
│   ├── scraper.py     # Playwright automation & rendering
│   ├── solver.py      # Answer computation logic
│   ├── utils.py       # File parsing helpers
│
└── tests/
    ├── test_main.py
    ├── test_utils.py

>>>>>>> 7a51db6b8add7e31fcf399ab5854886cc01b56c5

## Installation

### Prerequisites

<<<<<<< HEAD
- Python 3.8+
=======
- Python 3.10+
>>>>>>> 7a51db6b8add7e31fcf399ab5854886cc01b56c5
- pip

### Setup

<<<<<<< HEAD
1. **Clone or navigate to the project directory:**
   ```bash
   cd llm-quiz-agent
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Install Playwright browsers:**
   ```bash
   playwright install
   ```

5. **Configure environment variables:**
   ```bash
   cp .env.example .env
   # Edit .env and set your SECRET and EMAIL
   ```

## Usage

### Running the Server

```bash
# From the project root
python -m app.main

# Or using uvicorn directly
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

The server will start on `http://0.0.0.0:8000`

### API Endpoints

#### POST `/solve`

Solve a quiz chain.

**Request Body:**
```json
=======
bash
cd llm-quiz-agent
python -m venv venv
venv\Scripts\activate      # Windows
# or: source venv/bin/activate (Mac/Linux)

pip install -r requirements.txt
playwright install


Create environment file:

bash
cp .env.example .env
# Edit .env and set SECRET and EMAIL


## Usage

### Run the Server

bash
python -m app.main


or

bash
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload


Server runs at:


http://0.0.0.0:8000


## API Endpoints

### POST /solve

*Request*
json
>>>>>>> 7a51db6b8add7e31fcf399ab5854886cc01b56c5
{
  "email": "your-email@example.com",
  "secret": "your-secret-key",
  "url": "https://quiz-url.com/quiz-123"
}
<<<<<<< HEAD
```

**Response:**
```json
=======


*Response*
json
>>>>>>> 7a51db6b8add7e31fcf399ab5854886cc01b56c5
{
  "success": true,
  "message": "All quizzes completed successfully",
  "result": {
    "quizzes_solved": [
      {
        "quiz_number": 1,
        "url": "https://quiz-url.com/quiz-123",
        "answer": 42.5,
        "submission_result": {
          "correct": true,
          "url": "https://quiz-url.com/quiz-456"
        }
      }
    ],
    "total_quizzes": 1,
    "success": true
  }
}
<<<<<<< HEAD
```

**Status Codes:**
- `200`: Success
- `400`: Invalid request (missing/invalid JSON or URL)
- `403`: Invalid secret
- `500`: Server error

#### GET `/health`

Health check endpoint.

**Response:**
```json
{
  "status": "healthy"
}
```

#### GET `/`

API information and available endpoints.

### Example Usage

```bash
# Using curl
curl -X POST "http://localhost:8000/solve" \
  -H "Content-Type: application/json" \
  -d '{
    "email": "your-email@example.com",
    "secret": "your-secret-key",
    "url": "https://quiz-url.com/quiz-123"
  }'

# Using Python requests
import requests

response = requests.post(
    "http://localhost:8000/solve",
    json={
        "email": "your-email@example.com",
        "secret": "your-secret-key",
        "url": "https://quiz-url.com/quiz-123"
    }
)
print(response.json())
```

## How It Works

1. **Validation**: The `/solve` endpoint validates the secret and URL
2. **Scraping**: Uses Playwright to load and render the quiz page (handles JavaScript)
3. **Extraction**: Extracts:
   - Question text
   - Instructions
   - Data file links (CSV, PDF, Excel, etc.)
   - Submission URL
   - Base64 encoded data
   - JSON data
4. **Analysis**: Downloads and analyzes data files:
   - CSV/Excel: Sums columns, finds patterns
   - PDF: Extracts text and analyzes
   - JSON: Parses and extracts values
   - Text: Uses regex patterns to find answers
5. **Answer Computation**: Uses multiple strategies:
   - Direct answer in JSON/base64 data
   - File analysis (sum, count, pattern matching)
   - Text analysis (regex patterns, number extraction)
   - Retry with different strategies if wrong
6. **Submission**: Posts answer to quiz endpoint with retry logic
7. **Chain Solving**: If response contains `"correct": true` and a new URL, automatically solves the next quiz
8. **Timeout**: Stops after 3 minutes or when no more quizzes are available

## Configuration

Edit `.env` file to configure:

- `SECRET`: Secret key for authentication
- `EMAIL`: Your email address
- `PORT`: Server port (default: 8000)
- `QUIZ_TIMEOUT`: Total timeout for quiz chain (default: 180 seconds)
- `MAX_RETRIES`: Maximum retry attempts (default: 3)
- `LOG_LEVEL`: Logging level (DEBUG, INFO, WARNING, ERROR)

## Testing

```bash
# Run tests
pytest tests/

# Run with coverage
pytest --cov=app tests/
```

## Development

### Adding New Analysis Strategies

Edit `app/solver.py` in the `_compute_answer` method to add new answer computation strategies.

### Adding New File Type Support

Edit `app/utils.py` in the `analyze_data_file` function to add support for new file types.

## Troubleshooting

### Playwright Browser Installation

If you get Playwright errors:
```bash
playwright install chromium
```

### Port Already in Use

Change the `PORT` in `.env` or kill the process using the port:
```bash
# Windows
netstat -ano | findstr :8000
taskkill /PID <PID> /F

# Linux/Mac
lsof -ti:8000 | xargs kill
```

### Import Errors

Make sure you're running from the project root and the `app` package is importable:
```bash
# From project root
python -m app.main
```

## License

MIT License - see LICENSE file for details.

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request

## Support

For issues or questions, please open an issue on the repository.

=======


### GET /health

json
{ "status": "healthy" }


### GET /

Returns API information.

## How It Works

1. Validates request secret and quiz URL  
2. Loads the quiz page using Playwright (handles JS rendering)  
3. Extracts question, data links, and submission endpoints  
4. Downloads and analyzes data files  
5. Computes answers using multiple logic strategies  
6. Submits answer and follows next quiz link  
7. Stops when chain ends or timeout is reached  

## Configuration

Modify .env:


SECRET=<your-secret>
EMAIL=<your-email>
PORT=8000
QUIZ_TIMEOUT=180
MAX_RETRIES=3
LOG_LEVEL=INFO


## Testing

bash
pytest tests/
pytest --cov=app tests/


## Troubleshooting

*Playwright missing browsers*
bash
playwright install chromium


*Port already in use*
bash
netstat -ano | findstr :8000
taskkill /PID <PID> /F


*Import issues*
bash
python -m app.main


## License

MIT License — see LICENSE file for full details.

## Contributing

1. Fork the repository  
2. Create a feature branch  
3. Make changes and add tests  
4. Open a pull request  

## Support

For help or issues, open a GitHub issue in this repository.
>>>>>>> 7a51db6b8add7e31fcf399ab5854886cc01b56c5
