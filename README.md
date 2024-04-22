
# Python Code Quality and Security Setup

This guide outlines how to set up and maintain high standards for code quality and security in your Python codebase using automated tools and workflows.

## Setup Instructions

### 1. Pyproject.toml

Start by creating a `pyproject.toml` file in the root of your repository. This configuration file is used by various tools to maintain consistent code style and quality standards across your project.

Reference to `pyproject.toml` in this repository: [pyproject.toml](./pyproject.toml)

### 2. GitHub Actions Workflow (CI/CD)

Set up a Continuous Integration (CI) workflow by creating a file at `.github/workflows/python-ci.yml`. This will define actions that automatically lint, format, and check your code for security vulnerabilities upon each push or pull request.

```bash
mkdir .github/workflows # create this dir in your root path of code repository
cp python-ci.yml .github/workflows # copy this python-ci.yml in this dir
```

Reference to GitHub Actions workflow: [python-ci.yml](./python-ci.yml)

### 3. Pre-commit Configuration

For setting up pre-commit hooks in your repository, you will use a `.pre-commit-config.yaml` file. These hooks help to ensure that your code is automatically checked and formatted before each commit.

Reference to pre-commit config: [.pre-commit-config.yaml](./.pre-commit-config.yaml)

## Detailed Tool Descriptions

### isort

`isort` is a Python utility to sort imports alphabetically and automatically separate them into sections. It makes imports more readable and avoids conflicts.

### black

`black` is a code formatter that reformats entire files in place. It makes code review faster by producing the smallest diffs possible.

### flake8

`flake8` is a command-line utility for enforcing style consistency across Python projects

### autoflake

`autoflake` removes unused imports and unused variables from Python code

### pyproject-autoflake

`pyproject-autoflake` provides autoflake support for `pyproject.toml`, allowing you to define autoflake settings in a centralized project configuration file.

### bandit

`bandit` is a tool designed to find common security issues in Python code. It statically analyzes the code to search for potentially dangerous operations.

### pre-commit

`pre-commit` manages and configures pre-commit hooks that are run prior to each commit to ensure the quality of the code being committed.

## Install tools and hooks in your repo

```bash
pip install isort black flake8 autoflake pyproject-autoflake bandit pre-commit
pre-commit install
```

## Usage of Pre-commit Without Committing

To run all pre-commit hooks on your staged files without committing:

```bash
pre-commit run --all-files
```

This is useful for manually triggering the hooks to clean up your repository or to check your changes before committing them.

## To check security vunrebalities in your code run below command 

```bash
bandit -r . -ll -i -f html -o bandit-report.html
```

This will generate a html report of security issues in your code, check html report for more details
