# Testing

The testing infrastructure and practices for LEGO Block Creator.

## Test suite overview

The project includes a comprehensive test suite that covers all CLI commands and functionality with **100% code coverage**.

### Test statistics

- **Total Tests**: 21
- **Code Coverage**: 100%
- **Test Framework**: pytest
- **Coverage Tool**: pytest-cov

## Running tests

### Prerequisites

Install the required testing dependencies:

```bash
pip install -r requirements.txt
```

### Run all tests

```bash
pytest
```

This will automatically:
- Run all tests in the `tests/` directory
- Generate coverage reports (terminal, HTML, and XML)
- Display missing coverage lines

### Run tests with verbose output

```bash
pytest -v
```

### Run specific tests

```bash
# Run a specific test file
pytest tests/test_main.py

# Run a specific test function
pytest tests/test_main.py::test_lego_cmd_newpiece
```

### View the coverage report

After running tests, open the HTML coverage report:

```bash
# The report is generated in the htmlcov directory
open htmlcov/index.html  # macOS
xdg-open htmlcov/index.html  # Linux
start htmlcov/index.html  # Windows
```

## Test coverage

The test suite covers all CLI commands:

### Piece management commands
- `newpiece` - Create a new piece
- `newcolour`/`newcolor` - Create a new colour
- `addpiece` - Add quantity to existing piece
- `removepiece` - Remove quantity from piece

### Piece sorting commands
- `sortparts-all` - List all pieces
- `sortparts-name` - Search pieces by name
- `sortparts-colour`/`sortparts-color` - Filter by colour

### Set management commands
- `newset` - Create a new set
- `newtheme` - Create a new theme
- `addset` - Add quantity to existing set
- `removeset` - Remove quantity from set

### Set sorting commands
- `sortsets-all` - List all sets
- `sortsets-name` - Search sets by name
- `sortsets-number` - Search sets by number
- `sortsets-theme` - Filter by theme

### Utility commands
- `help` - Display help information
- `copyright`/`license` - Display license information
- Invalid command handling

## Continuous integration

Tests run automatically on every push and pull request across three operating
systems and four Python versions. See [CI/CD](ci-cd.md) for the full workflow
breakdown.

## Test configuration

Test configuration is defined in `pyproject.toml`:

```toml
[tool.pytest.ini_options]
minversion = "7.0"
addopts = "-ra -q --strict-markers --cov=main --cov-report=term-missing --cov-report=html --cov-report=xml"
testpaths = ["tests"]
pythonpath = ["."]

[tool.coverage.run]
source = ["."]
omit = ["tests/*", "setup.py", "__main__.py"]
```

## Writing tests

### Test structure

Tests are located in the `tests/` directory and follow pytest conventions:

```python
from unittest.mock import patch, call
import main

@patch("builtins.input", side_effect=["command", "arg1", "arg2"])
@patch("builtins.print")
def test_lego_cmd_command(self, mock_print):
    """Test the command."""
    main.lego_cmd()
    mock_print.assert_has_calls([
        call("LEGO CMD: "),
        call("Expected output"),
    ])
```

### Test guidelines

1. **Use descriptive test names**: Test names should clearly indicate what is being tested
2. **Mock user input**: Use `@patch("builtins.input")` to simulate user input
3. **Mock output**: Use `@patch("builtins.print")` to capture and verify output
4. **Test one command per test**: Each test should focus on a single CLI command
5. **Verify behavior**: Use assertions to verify expected behavior

## Troubleshooting

### Tests fail locally

1. Ensure you have the latest dependencies:
   ```bash
   pip install --upgrade -r requirements.txt
   ```

2. Clear pytest cache:
   ```bash
   pytest --cache-clear
   ```

3. Check Python version:
   ```bash
   python --version  # Should be 3.9 or higher
   ```

### Coverage issues

If coverage reports show unexpected results:

1. Delete existing coverage data:
   ```bash
   rm -rf .coverage htmlcov/ coverage.xml
   ```

2. Run tests again:
   ```bash
   pytest
   ```

## Contributing tests

When contributing new features:

1. **Write tests first** (Test-Driven Development)
2. **Ensure 100% coverage** of new code
3. **Run pylint** to ensure code quality:
   ```bash
   pylint $(git ls-files '*.py')
   ```
4. **Verify tests pass** on your local machine before submitting a PR
5. **Update this documentation** if adding new test categories

## Resources

- [pytest Documentation](https://docs.pytest.org/)
- [pytest-cov Documentation](https://pytest-cov.readthedocs.io/)
- [unittest.mock Documentation](https://docs.python.org/3/library/unittest.mock.html)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

{{ support() }}
