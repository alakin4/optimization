# ABout
This repo is for a toy optimization problem related to an interview.

# Optimization Problem
Problem Statement
The transportation department wants help in reducing the empty miles (equipment
moved with no demand) they run on their own fleet as a goal for next year. They
currently run approximately 20% of their total miles as empty. The transportation
department revises their purchased motor agreements yearly. Purchase motor
agreements allow the transportation department to use third-party transport and their
equipment to move company demand. The demand you are given is the average
number of loads that fill one long trailer and only one trailer can be moved per trip.
Every origin location needs to get enough equipment either moved back to them or
purchased for their average demand.
Average cost per mile of own fleet is $2/mile, even if there is no demand in the
equipment. Purchased motor has a company average cost of $3/mile currently, but the
purchase department advised that the cost of purchase may be moving up per industry
news.
Goal
To provide a proof-of-concept solution for transportation to use during their bidding that
would help minimize their total operating cost while ensuring all demand is moved and
every origin has enough equipment for their demand.

# WIP
Most of the code is in the Python Notebook named `FedEx.ipynb`. It consists of modular code meant to be housed in separate scripts and imported as modules. Note that to run `FedEx.ipynb`, you would need to follow the project installation steps below and also have the `interview problem.xlsx` file in a data folder (you create) at the project root.

This modular code can also be used in dashboarding frameworks like streamlit, or even better be served in a FASTAPI endpoints. these are for the future.

## Project Structure

   ```
   .
   ├── Dockerfile
   ├── LICENSE
   ├── README.md
   ├── docker-dev.sh
   ├── pyproject.toml
   ├── src
   │   ├── __init__.py
   │   ├── main.py
   ├── tests
   │   └── test_main.py
   └── uv.lock
   ```

## Features

- **Structured Codebase**: All source code resides in the `src/` directory, promoting a clean separation between application code and configuration files.
- **Dependency Management**: Utilizes [uv](https://github.com/astral-sh/uv) for managing dependencies via `pyproject.toml` and `uv.lock`.
- **Testing Framework**: Integrated with `pytest` for writing and running tests.
- **Linting and Formatting**: Configured with `ruff` for code linting and formatting.
- **Pre-commit Hooks**: Automated code quality checks using pre-commit hooks defined in `.pre-commit-config.yaml`.
- **Docker Support**: Includes a `Dockerfile` and `docker-dev.sh` script for containerized development environments.
- **Continuous Integration**: Set up with GitHub Actions for automated testing and linting on push events.
- **VSCode Ready**: Includes a `.vscode` directory with workspace configurations for linters, formatters, and testing integration.

## Getting Started

### Prerequisites

Ensure you have the following installed:

- [Python 3.10+](https://www.python.org/downloads/)
- [uv](https://github.com/astral-sh/uv) (`brew install uv`)
- [Docker](https://www.docker.com/) (optional, for containerized development)
- [pre-commit](https://pre-commit.com/) (`pip install pre-commit` or `brew install pre-commit`)

### Installation

1. **Clone the repository**:

   ```sh
   git clone https://github.com/alakin4/python-template.git
   cd python-template

> To have a different project name, it is better to start the project from github and select this as a template.

2. **Install dependencies**:
   ```sh
   uv sync --all-groups

3. **Set up pre-commit hooks**:
   ```sh
   pre-commit install

4. **Run tests**:
   ```sh
   uv run pytest tests -v or uv run pytest -v.
   ```
   
The `-v` adds a bit more structured output

## Running the Application
Run the application from the entry point
   ```sh
    uv run src/main.py
   ```

## Virtual Environments with uv
Create and activate a virtual environment:
   ```sh
    uv venv
    source .venv/bin/activate
   ```
Run `deactivate` to Deactivate the virtual environment.

## Keeping Lock File in Sync
If you modify `pyproject.toml`  directly, make sure to verify lock file sync:
   ```sh
    uv lock --locked
   ```
## Code Quality Checks
* Check for rule violations:
    ```sh
    uvx ruff check .
    ```
* Format code:
    ```sh
    uvx ruff format .
    ```
* Format specifically rule:
    ```sh
    uvx ruff check --select I --fix .
    ```
* Check if all files are formatted correctly:
    ```sh
    uvx ruff format --check .
    ```
## Type Checking
Ruff does not catch type hint issues. Use pyright:
   ```sh
    uv run pyright
   ```
    
## Testing
* Run tests:
  ```sh
  uv run pytest -v
  ``` 
* With coverage tracking:
  ```sh
  uv run pytest -v --cov
  ```
 * Generate XML report:
      ```sh
        uv run pytest -v --cov --cov-report=xml
      ```
 ## Pre-commit Hooks
- Install `pre-commit` globally and initialize it in the repo as indicated above using `pre-commit install
- Trigger manually using: `pre-commit run --all-files`
