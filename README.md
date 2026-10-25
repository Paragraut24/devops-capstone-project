# DevOps Capstone

[![Build Status](https://github.com/Paragraut24/devops-capstone-project/actions/workflows/ci-build.yaml/badge.svg)](https://github.com/Paragraut24/devops-capstone-project/actions/workflows/ci-build.yaml)

## Project Overview

The **DevOps Capstone** project is a cloud-native RESTful microservice for managing customer accounts in an e-commerce platform. Built with Python and Flask, it features full CRUD capabilities backed by a PostgreSQL database and adheres to DevOps engineering best practices.

### Key Capabilities
- **RESTful API Service:** Provides endpoints to create, list, read, update, and delete accounts.
- **TDD & Code Quality:** Thorough unit testing suite with `nosetests` achieving >=95% test coverage, validated with `flake8` and `pylint`.
- **Application Security:** Protected using `Flask-Talisman` for HTTP security headers (CSP, HSTS, X-Frame-Options) and `Flask-CORS` for cross-origin policies.
- **Continuous Integration (CI):** Automated GitHub Actions workflow testing and linting every push and pull request against a live PostgreSQL service container.
- **Containerization:** Production-ready `Dockerfile` running with a non-root security context on `gunicorn`.
- **Kubernetes Deployment & CD:** Automated continuous delivery pipeline using Tekton tasks to clone, lint, test, build, and deploy onto Kubernetes / OpenShift.

## REST API Endpoints

| Method | Endpoint | Description | Status Code |
|---|---|---|---|
| GET | `/` | Service root and metadata | 200 OK |
| GET | `/health` | Service health status check | 200 OK |
| POST | `/accounts` | Create a new customer account | 201 Created |
| GET | `/accounts` | List all existing accounts | 200 OK |
| GET | `/accounts/<id>` | Retrieve an account by ID | 200 OK |
| PUT | `/accounts/<id>` | Update an existing account by ID | 200 OK |
| DELETE | `/accounts/<id>` | Delete an account by ID | 204 No Content |

## Running Tests and Linting

```bash
# Install dependencies
pip install -r requirements.txt

# Run linter
flake8 service tests --count --max-complexity=10 --max-line-length=127 --statistics

# Run test suite with coverage
nosetests -v --with-spec --spec-color
```

## Running the Application Locally

```bash
gunicorn --bind=0.0.0.0:8080 --log-level=info service:app
```
