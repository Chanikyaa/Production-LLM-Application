# Production LLM Application

A production-oriented LLM application that exposes language-model functionality through a REST API, with features for request validation, authentication, caching, rate limiting, and monitoring.

## Overview

This project demonstrates how to build an API layer around a Large Language Model (LLM).

Rather than using an LLM only through a notebook or command-line interface, this application provides an API-based architecture designed around practical backend engineering concerns.

It includes a mock provider for predictable local development and testing, along with an optional OpenAI-compatible provider adapter.

## Key Features

- REST API for LLM requests.
- Request and response validation.
- Configurable LLM provider interface.
- Mock provider for local testing.
- Optional OpenAI-compatible provider adapter.
- Bearer-token authentication.
- Rate limiting.
- Response caching.
- Application metrics.
- Automated test coverage.

## Architecture

```text
             API Client
                 |
                 v
            FastAPI App
                 |
                 v
        Authentication Layer
                 |
                 v
         Request Validation
                 |
                 v
          Rate Limiter
                 |
                 v
           Cache Check
                 |
          +------+------+
          |             |
        Cache Hit     Cache Miss
          |             |
          |             v
          |        LLM Provider
          |             |
          |             v
          |        Model Response
          |             |
          +------+------+
                 |
                 v
          API Response
                 |
                 v
          Metrics / Logs
```

## Technology Stack

- Python
- FastAPI
- Pydantic
- REST API
- LLM provider abstraction
- Pytest
- Docker configuration
- Git and GitHub

## Project Structure

```text
llm-production-api/
│
├── app/
│   ├── main.py
│   ├── api/
│   ├── providers/
│   ├── services/
│   └── config.py
│
├── tests/
│
├── requirements.txt
├── Dockerfile
├── docker-compose.yml
├── .env.example
├── .gitignore
├── LICENSE
└── README.md
```

*This is a representative structure. Use the actual project files as the source of truth.*

## Installation

Clone the repository:

```bash
git clone https://github.com/Chanikyaa/llm-production-api.git
cd llm-production-api
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it:

**Windows**

```bash
.venv\Scripts\activate
```

**Linux/macOS**

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Configuration

Create a `.env` file using the provided `.env.example`.

Configure the required application settings and authentication token. If using the optional external LLM provider, configure its API credentials too.

Do not commit secrets or API keys to GitHub.

## Running the Application

Start the FastAPI application using the project's configured entry point.

For example, if the application entry point is `app.main:app`:

```bash
uvicorn app.main:app --reload
```

Open the API documentation in your browser:

```text
http://127.0.0.1:8000/docs
```

## API Capabilities

The application provides an API interface for submitting LLM requests and receiving generated responses.

The exact endpoint paths and request schema should be taken from the implemented API documentation at `/docs`.

## Testing

Run the automated test suite:

```bash
pytest
```

## Engineering Concepts Demonstrated

- LLM application architecture
- REST API development
- Provider abstraction
- Request validation
- Authentication
- Rate limiting
- Response caching
- Metrics and observability
- Automated testing
- Backend service design

## Current Validation

The automated test suite reported **11 passing tests**.

The project also passed Python compilation checks.

The default mock provider supports deterministic local testing. The optional OpenAI-compatible provider has not been live-verified.

## Known Limitations

- The current bearer-token authentication is a basic MVP implementation.
- Rate limiting, caching, and metrics use process-local state.
- The SSE endpoint emits completed response chunks; it is not true upstream model-token streaming.
- Docker execution, hosted CI, live provider integration, and load testing have not been verified.

## Future Improvements

- Add persistent caching.
- Implement distributed rate limiting.
- Integrate production authentication and authorization.
- Support genuine upstream token streaming.
- Add centralized logging and monitoring.
- Add load and performance testing.
- Deploy using Docker and a cloud platform.

## Author

**Palli Chanikya Paidi Balaji**

B.Tech – VIT Chennai (2025)  
M.Tech CSE – AI & Data Science, Mahindra University (2026–2028)

GitHub: [@Chanikyaa](https://github.com/Chanikyaa)

---

*Part of an AI/ML Engineering Portfolio focused on practical AI systems and production-oriented development.*
