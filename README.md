# FundLens

Backend for tracking Indian mutual fund NAVs and portfolios, with an AI assistant that answers questions from fund documents.

> **Status: work in progress.** Started November 2026.

## What it will do

- Ingest daily and historical NAV data for Indian mutual fund schemes
- Let users create portfolios and record SIP and lump-sum transactions
- Calculate portfolio value and returns
- Send alerts when a fund's NAV moves sharply
- Answer questions about funds using RAG over public fund documents, with citations

## Planned stack

| Area | Technology |
|---|---|
| API | Python, FastAPI |
| Database | PostgreSQL, Alembic migrations, pgvector |
| Cache and rate limiting | Redis |
| Background jobs | Celery and Celery beat |
| Containers | Docker, Docker Compose |
| CI/CD | GitHub Actions |
| Hosting | AWS |

## Architecture

Layered structure. Each layer talks only to the layer below it.

```text
app/
├── api/            routers: request and response handling only
├── services/       business logic
├── repositories/   all database queries
├── models/         database tables
├── core/           configuration
└── workers/        Celery tasks
```

## Design rules

- Money is stored as `Decimal`, never `float`
- The LLM only explains numbers computed by code, and never gives investment advice
- Every change goes through a pull request

## Roadmap

Built in the open, one milestone at a time. Details will be added as each milestone ships.

## Author

Chaitany Mishra · [GitHub](https://github.com/ChaitanyMishra) · [LinkedIn](https://www.linkedin.com/in/chaitanymishra/)
