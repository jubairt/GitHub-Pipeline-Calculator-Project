# GitHub Pipeline Calculator Project

## Project Overview

This project is a simple Python calculator application built to demonstrate **industry-level software engineering practices** rather than just writing functional code.

The focus of this project is on:
- Proper version control using Git
- Feature-based branching and merging
- Automated testing using pytest
- Code quality analysis using Pylint
- Continuous Integration (CI) using GitHub Actions
- Clear documentation of engineering decisions

---

## Objectives

- Implement calculator operations incrementally
- Practice real-world Git workflows
- Apply automated testing
- Enforce and understand code quality standards
- Automate testing using CI pipelines
- Document the entire development process clearly

---

## Version Control Strategy (Git)

### Branching Model Used

This project follows a **feature-based branching strategy (GitHub Flow style)**.

- `main` branch always contains **stable, working code**
- Each calculator operation was developed in its **own feature branch**
- Feature branches were merged into `main` only after completion
- No direct work was done on `main`

This approach mirrors how real teams prevent unstable code from reaching production.

---

### Git Commands Used and What They Do

#### Initialize Git repository
```powershell
git init
```
- Initializes a new Git repository in the project directory.

#### Rename default branch to main
```powershell
git branch -m master main
```
- Renames the default branch from master to main, aligning with modern Git standards and CI expectations.

#### Create feature branches
```powershell
git checkout -b feature-add-operation
git checkout -b feature-subtract-operation
git checkout -b feature-multiply-operation
git checkout -b feature-divide-operation
```
- Creates isolated branches for each calculator operation so that changes are developed independently.

#### Stage and commit changes
```powershell
git add .
git commit -m "Add add() operation with tests"
```
- Stages all modified files and creates a commit representing a complete unit of work.

#### Merge feature branches into main
```powershell
git checkout main
git merge feature-add-operation
```
- Merges completed features into main.
- Fast-forward merges occurred because each branch was created from the latest main.

#### Push project to GitHub
```powershell
git remote add origin <repository-url>
git push -u origin main
```
- Connects the local repository to GitHub and pushes the main branch.

### Testing Strategy (pytest)

- Unit tests were written using pytest
- Each calculator operation has dedicated tests
- Edge cases such as division by zero are explicitly tested
- Tests validate one behavior per test case
- Tests are run locally and in CI

Example test command:
```powershell
pytest app tests
```
- Run this from the root of the project folder
- This ensures the test works before pushing into github repository

### Continuous Integration (CI) – GitHub Actions

The project uses GitHub Actions to automate testing.

#### CI Workflow Behavior

- Triggered on:
  - Push to main
  - Pull requests targeting main

- Steps performed:
  - Checkout repository
  - Set up Python environment
  - Install dependencies
  - Run pytest

This guarantees that broken or untested code cannot silently enter main.

### Code Quality with Pylint

#### Why Pylint Was Used

- Pylint was introduced to:
  - Improve code readability
  - Enforce consistent style
  - Detect potential issues early
  - Practice industry-standard static analysis

#### Generating Pylint Configuration (Do this in bash)
```bash
pylint --generate-rcfile > .pylintrc
```
- This command generated a project-level Pylint configuration file.

#### Disabled Rules (Intentional)
```bash
[MESSAGES CONTROL]
disable =
    C0114,
    C0116,
    redefined-outer-name
```
- The above rules were disabled to reduce noise and align with pytest conventions
- C0114, C0116: Docstrings are less critical for small demo/test files
- redefined-outer-name: Pylint does not fully understand pytest fixtures

#### Pylint Results
```bash
pylint app tests
```
output:
```bash
Your code has been rated at 9.13/10 (previous run: 4.35/10, +4.78)
```

### Engineering Best Practices Applied

- Feature-based Git workflow
- Incremental development
- Automated testing
- CI enforcement
- Linting with judgment
- Clean commit history
- Clear documentation

### Key Learnings

- Feature branches must always be created from the latest main
- Git merges operate on file history, not functions
- Tests prevent silent regressions
- CI pipelines enforce discipline automatically
- Linters guide developers but do not replace judgment
- Clean code is about readability, not just correctness

### Conclusion

This project demonstrates not just the ability to write Python code, but the ability to:
- Work like a professional software engineer
- Follow real-world Git workflows
- Apply automated testing and CI
- Maintain and explain code quality decisions

The project is intentionally simple in functionality but strong in engineering discipline, making it suitable for interviews and portfolio demonstration.
