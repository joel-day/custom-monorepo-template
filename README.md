# Custom Project Template

This template builds a mono-repo with its own virtual environment. It configures tools to ensure the code runs, follows PEP8 guidelines, and runs on Linux, Windows, and Mac - as well as Python versions 3.10, 3.11, & 3.12. 

## Installation

```bash
# Clone the repository
git clone https://github.com/joel-day/project-template-custom-cookiecutter.git

# Remove git's connection to project-template-custom-cookiecutter.git
git remote remove origin

# Manually create new repository in Github named "new-project-repo" with no README, and rename the locally cloned template to match the name

# Move to the renamed directory
cd new-project-repo

# Connect to the new repository
git remote add origin https://github.com/joel-day/new-project-repo.git

# Ensure you are connected to the new repository
git remote -v

# --rebase keeps your history clean by replaying your commits on top of what’s already in the remote
git pull origin main --rebase 

# Create the virtual environment
uv venv .venv

# Activate the virtual environment
source .venv\bin\activate # Mac/Linux
.venv\Scripts\activate   # Windows

# Sync environment based on dependencies in top-level pyproject.toml file
uv sync

# (OPTIONAL) Sync environment based on dependencies across all packages' pyproject.toml files
uv sync --all-packages

# Use this to push changes back to github
git push --set-upstream origin main
```

## Included Tools & Packages

- **UV**: Used for package management and virtual environment creation. Configured to manage environments in a monorepo setup, ensuring consistency across the project.

- **GitHub Actions**: Ensures that the code works across multiple operating systems (Linux, Mac, and Windows) and supports Python versions 3.10, 3.11, and 3.12. It's a part the CI pipeline and is configured to run on pull requests to main.

- **Pytest**: Configured to run tests and verify the correctness of code execution. It ensures that the codebase remains functional and that new changes don’t introduce unexpected behavior.
```bash
pytest
```
- **Flake8**: Used for checking code compliance with PEP8 standards. It helps maintain a clean and consistent code style across the project by enforcing formatting and style guidelines.
```bash
flake8 .
```

