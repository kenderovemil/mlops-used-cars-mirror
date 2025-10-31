# Contributing to MLOps Used Cars Mirror

Thank you for your interest in contributing to the MLOps Used Cars Mirror project! We welcome contributions from the community and appreciate your efforts to improve this project.

## Table of Contents
- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Branching Strategy](#branching-strategy)
- [Commit Message Format](#commit-message-format)
- [Pull Request Guidelines](#pull-request-guidelines)
- [Coding Standards](#coding-standards)
- [Testing Requirements](#testing-requirements)
- [Documentation](#documentation)

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment for everyone. Please be professional and courteous in all interactions.

## Getting Started

### Prerequisites

Before you begin, ensure you have:
- Python 3.8 or higher installed
- Git installed and configured
- A GitHub account
- (Optional) Azure account for testing Azure ML integrations

### Setting Up Your Development Environment

1. **Fork the repository** on GitHub

2. **Clone your fork locally:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/mlops-used-cars-mirror.git
   cd mlops-used-cars-mirror
   ```

3. **Add the upstream repository:**
   ```bash
   git remote add upstream https://github.com/kenderovemil/mlops-used-cars-mirror.git
   ```

4. **Create a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

5. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   pip install -r requirements-dev.txt  # If available
   ```

## Development Workflow

1. **Sync your fork with upstream:**
   ```bash
   git fetch upstream
   git checkout main
   git merge upstream/main
   ```

2. **Create a new branch** for your feature or fix (see [Branching Strategy](#branching-strategy))

3. **Make your changes** following our coding standards

4. **Test your changes** thoroughly

5. **Commit your changes** using our commit message format

6. **Push to your fork** and create a pull request

## Branching Strategy

We follow a simplified Git flow strategy:

### Branch Naming Convention

Use descriptive branch names with the following prefixes:

- `feature/` - New features or enhancements
  - Example: `feature/add-xgboost-model`
  
- `bugfix/` - Bug fixes
  - Example: `bugfix/fix-data-preprocessing`
  
- `hotfix/` - Critical fixes for production
  - Example: `hotfix/fix-azure-credentials`
  
- `docs/` - Documentation updates
  - Example: `docs/update-installation-guide`
  
- `refactor/` - Code refactoring without changing functionality
  - Example: `refactor/reorganize-preprocessing-pipeline`
  
- `test/` - Adding or updating tests
  - Example: `test/add-model-evaluation-tests`

- `mlops/` - MLOps pipeline improvements
  - Example: `mlops/add-model-monitoring`

### Branch Lifecycle

1. **Create your branch from `main`:**
   ```bash
   git checkout main
   git pull upstream main
   git checkout -b feature/your-feature-name
   ```

2. **Keep your branch updated:**
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

3. **Delete branch after merge:**
   Once your PR is merged, delete your local and remote branches:
   ```bash
   git branch -d feature/your-feature-name
   git push origin --delete feature/your-feature-name
   ```

## Commit Message Format

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification for clear and structured commit messages.

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat` - A new feature
- `fix` - A bug fix
- `docs` - Documentation changes
- `style` - Code style changes (formatting, missing semicolons, etc.)
- `refactor` - Code refactoring without changing functionality
- `perf` - Performance improvements
- `test` - Adding or updating tests
- `chore` - Maintenance tasks, dependency updates
- `ci` - CI/CD pipeline changes
- `build` - Build system or external dependencies

### Scope (Optional)

The scope specifies the area of the codebase affected:
- `data` - Data ingestion or preprocessing
- `model` - Model training or evaluation
- `pipeline` - ML pipeline
- `azure` - Azure ML integration
- `api` - API endpoints
- `config` - Configuration files
- `deps` - Dependencies

### Examples

```
feat(model): add XGBoost model training pipeline

Implement XGBoost regressor with hyperparameter tuning using 
RandomizedSearchCV. Includes cross-validation and metric logging
to Azure ML Studio.
```

```
fix(data): handle missing values in categorical features

Previously, categorical features with missing values caused the
preprocessing pipeline to fail. Now using 'unknown' category for
missing values before encoding.

Fixes #123
```

```
docs: update README with Azure ML setup instructions

Add detailed steps for configuring Azure ML workspace and
authentication. Include troubleshooting section for common issues.
```

```
chore(deps): update scikit-learn to 1.3.0

Update scikit-learn to latest stable version for improved
performance and new features.
```

### Guidelines

- Use the imperative mood ("add feature" not "added feature")
- Keep the subject line under 50 characters
- Capitalize the subject line
- Don't end the subject line with a period
- Separate subject from body with a blank line
- Wrap the body at 72 characters
- Use the body to explain **what** and **why**, not **how**
- Reference issues and PRs in the footer

## Pull Request Guidelines

### Before Submitting a PR

- [ ] Ensure your code follows the project's coding standards
- [ ] Run all tests and ensure they pass
- [ ] Update documentation if needed
- [ ] Add tests for new features
- [ ] Ensure your branch is up-to-date with `main`
- [ ] Run linters and formatters (e.g., `black`, `flake8`, `pylint`)

### PR Title Format

Follow the same format as commit messages:
```
<type>(<scope>): <description>
```

Example: `feat(model): add Random Forest model with hyperparameter tuning`

### PR Description Template

```markdown
## Description
Brief description of the changes and their purpose.

## Type of Change
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update
- [ ] MLOps pipeline improvement

## Related Issues
Fixes #(issue number)
Related to #(issue number)

## Changes Made
- Change 1
- Change 2
- Change 3

## Testing
Describe the tests you ran to verify your changes:
- [ ] Unit tests
- [ ] Integration tests
- [ ] Manual testing

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review of my code
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation
- [ ] My changes generate no new warnings
- [ ] I have added tests that prove my fix is effective or that my feature works
- [ ] New and existing unit tests pass locally with my changes
- [ ] Any dependent changes have been merged and published

## Screenshots (if applicable)
Add screenshots to demonstrate UI changes or results.

## Additional Notes
Any additional information that reviewers should know.
```

### PR Review Process

1. **Automated checks:** CI/CD pipeline runs automatically
2. **Code review:** At least one maintainer will review your PR
3. **Address feedback:** Make requested changes if needed
4. **Approval:** Once approved, a maintainer will merge your PR
5. **Clean up:** Delete your branch after merge

### PR Best Practices

- Keep PRs focused and small (ideally < 400 lines of code)
- One feature/fix per PR
- Provide clear descriptions and context
- Respond to feedback promptly
- Be open to suggestions and constructive criticism
- Update your PR based on review comments

## Coding Standards

### Python Style Guide

We follow [PEP 8](https://pep8.org/) with some modifications:

- **Line length:** Maximum 100 characters (not 79)
- **Indentation:** 4 spaces (no tabs)
- **Quotes:** Use double quotes for strings
- **Imports:** Group and sort imports (use `isort`)

### Code Formatting

Use automated formatters:

```bash
# Format code with black
black .

# Sort imports
isort .

# Check style with flake8
flake8 .

# Type checking with mypy (if configured)
mypy .
```

### Naming Conventions

- **Variables and functions:** `snake_case`
- **Classes:** `PascalCase`
- **Constants:** `UPPER_SNAKE_CASE`
- **Private methods:** Prefix with single underscore `_method_name`
- **Module-level private:** Prefix with single underscore `_variable`

### Code Quality

- Write self-documenting code with clear variable names
- Add docstrings to all public functions, classes, and modules
- Keep functions small and focused (single responsibility)
- Avoid deep nesting (max 3-4 levels)
- Handle exceptions appropriately
- Use type hints where applicable

### Docstring Format

Use Google-style docstrings:

```python
def train_model(X_train, y_train, model_type="random_forest"):
    """Train a machine learning model on the provided data.
    
    Args:
        X_train: Training features as numpy array or pandas DataFrame
        y_train: Training labels as numpy array or pandas Series
        model_type: Type of model to train (default: "random_forest")
        
    Returns:
        Trained model object
        
    Raises:
        ValueError: If model_type is not supported
        
    Example:
        >>> model = train_model(X_train, y_train, model_type="xgboost")
    """
    # Implementation
```

## Testing Requirements

### Test Coverage

- Aim for at least 80% code coverage
- All new features must include tests
- Bug fixes should include regression tests

### Running Tests

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=src --cov-report=html

# Run specific test file
pytest tests/test_preprocessing.py

# Run tests matching pattern
pytest -k "test_model"
```

### Test Structure

```python
import pytest
from src.preprocessing import preprocess_data

def test_preprocess_handles_missing_values():
    """Test that preprocessing correctly handles missing values."""
    # Arrange
    raw_data = create_test_data_with_missing_values()
    
    # Act
    processed_data = preprocess_data(raw_data)
    
    # Assert
    assert processed_data.isnull().sum().sum() == 0
```

### Test Categories

- **Unit tests:** Test individual functions and classes
- **Integration tests:** Test component interactions
- **End-to-end tests:** Test complete workflows
- **Performance tests:** Test training and inference speed

## Documentation

### What to Document

- **README:** Project overview and setup instructions
- **Code comments:** Complex logic and non-obvious decisions
- **Docstrings:** All public APIs
- **Architecture docs:** High-level system design
- **API docs:** Endpoint specifications
- **Deployment guides:** How to deploy models

### Documentation Style

- Write clear, concise documentation
- Use examples to illustrate concepts
- Keep documentation up-to-date with code changes
- Include diagrams where helpful
- Provide troubleshooting guides

## Questions or Need Help?

- Open an issue with the `question` label
- Reach out to maintainers
- Check existing issues and discussions
- Review the project wiki (if available)

## Recognition

Contributors will be recognized in:
- Project README
- Release notes
- GitHub contributors page

Thank you for contributing to MLOps Used Cars Mirror! 🚀
