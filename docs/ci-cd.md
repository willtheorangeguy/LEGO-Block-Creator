# CI/CD

The GitHub Actions workflows used for continuous integration and deployment.

## Overview

The project uses multiple GitHub Actions workflows to ensure code quality, security, and reliability:

| Workflow | Trigger | Purpose | Badge |
|----------|---------|---------|-------|
| PyTest | Push, PR | Run tests on multiple OS/Python versions | ![Pytest State](https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/pytest.yml/badge.svg) |
| Pylint | Push | Code quality and style checking | ![Pylint State](https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/pylint.yml/badge.svg) |
| CodeQL | Push, PR, Schedule | Security vulnerability scanning | ![CodeQL State](https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/codeql-analysis.yml/badge.svg) |
| Docker Publish | Release | Build and publish Docker images | ![Docker Build State](https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/docker-publish.yml/badge.svg) |
| PyPI Publish | Release | Publish package to PyPI | ![PyPI Build State](https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/push-to-pypi.yml/badge.svg) |
| Docs | Push to `master` | Build and publish this documentation site | ![Docs State](https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/docs.yml/badge.svg) |
| Docs Lint | Pull request | Markdown style, strict docs build, link check | ![Docs Lint State](https://github.com/willtheorangeguy/LEGO-Block-Creator/actions/workflows/docs-lint.yml/badge.svg) |

## Workflow details

### 1. PyTest workflow (`.github/workflows/pytest.yml`)

**Purpose**: Comprehensive automated testing across multiple platforms and Python versions.

**Trigger**: Every push and pull request

**Configuration**:
```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest, macos-latest]
    python-version: ['3.9', '3.10', '3.11', '3.12']
```

**Test Matrix**: 12 jobs (3 operating systems × 4 Python versions)

**Steps**:
1. Checkout repository
2. Set up Python environment
3. Install dependencies from `requirements.txt`
4. Run pytest with coverage
5. Upload coverage reports to Codecov (Ubuntu + Python 3.12 only)

**Coverage Reporting**:
- Terminal output with missing lines
- HTML report (in `htmlcov/`)
- XML report for external tools (Codecov)

**What Gets Tested**:
- All CLI commands (21 test cases)
- 100% code coverage of `main.py`
- Cross-platform compatibility

### 2. Pylint workflow (`.github/workflows/pylint.yml`)

**Purpose**: Enforce code quality standards and Python best practices.

**Trigger**: Every push

**Configuration**:
```yaml
python-version: ["3.9"]
```

**Steps**:
1. Checkout repository
2. Set up Python 3.9
3. Install pylint
4. Analyze all Python files

**What Gets Checked**:
- Code style (PEP 8)
- Code complexity
- Potential bugs
- Code smells
- Documentation completeness

### 3. CodeQL workflow (`.github/workflows/codeql-analysis.yml`)

**Purpose**: Automated security vulnerability detection.

**Trigger**: 
- Push to main/master branches
- Pull requests
- Weekly schedule (Mondays at 00:00 UTC)

**Language**: Python

**Steps**:
1. Checkout repository
2. Initialize CodeQL
3. Auto-build project
4. Perform CodeQL analysis

**What Gets Scanned**:
- Security vulnerabilities
- Code quality issues
- Common coding errors
- Potential injection vulnerabilities

### 4. Docker publish workflow (`.github/workflows/docker-publish.yml`)

**Purpose**: Build and publish Docker images to GitHub Container Registry.

**Trigger**: Release creation

**Steps**:
1. Checkout repository
2. Set up Docker Buildx
3. Login to GitHub Container Registry
4. Build Docker image
5. Push to `ghcr.io/willtheorangeguy/lego-block-creator`

### 5. PyPI publish workflow (`.github/workflows/push-to-pypi.yml`)

**Purpose**: Publish Python package to the Python Package Index.

**Trigger**: Release creation

**Steps**:
1. Checkout repository
2. Set up Python
3. Install build tools
4. Build distribution packages
5. Publish to PyPI

**Requirements**: `PYPI_API_TOKEN` secret must be configured

### 6. Docs workflow (`.github/workflows/docs.yml`)

**Purpose**: Build and publish this documentation site to GitHub Pages.

**Trigger**: Push to `master` touching `docs/`, `mkdocs.yml`, `overrides/`, or
any root document included in the site.

This workflow contains no build logic. It calls a reusable workflow in
[willtheorangeguy/mkdocs](https://github.com/willtheorangeguy/mkdocs), which
owns the theme, the plugin set, and the pinned toolchain for every repository.
Build changes are made once, there, rather than in each repo.

### 7. Docs lint workflow (`.github/workflows/docs-lint.yml`)

**Purpose**: Catch documentation problems before they reach `master`.

**Trigger**: Pull requests touching `docs/`, `mkdocs.yml`, or `overrides/`.

**What Gets Checked**:
- markdownlint style rules
- A strict MkDocs build, which fails on broken internal links, missing nav
  files, bad anchors, and missing snippet targets
- External links, via lychee

## Setting up CI/CD

### Required secrets

Configure the following secrets in repository settings:

1. **CODECOV_TOKEN** (Optional): For uploading coverage to Codecov
   - Get from [codecov.io](https://codecov.io/)
   - Settings → Secrets and variables → Actions → New repository secret

2. **PYPI_API_TOKEN** (Required for releases): For publishing to PyPI
   - Generate at [pypi.org](https://pypi.org/manage/account/token/)
   - Settings → Secrets and variables → Actions → New repository secret

### Workflow permissions

The workflows require the following permissions:

- **PyTest**: `contents: read`
- **Pylint**: `checks: write`, `pull-requests: write`, `contents: read`
- **CodeQL**: `actions: read`, `contents: read`, `security-events: write`
- **Docker Publish**: `contents: read`, `packages: write`
- **PyPI Publish**: `contents: read`

## Local testing

### Test workflows locally

Use [act](https://github.com/nektos/act) to run workflows locally:

```bash
# Install act
brew install act  # macOS
# or
curl https://raw.githubusercontent.com/nektos/act/master/install.sh | sudo bash  # Linux

# Run pytest workflow
act -j test

# Run specific workflow
act -W .github/workflows/pytest.yml
```

### Validate workflow syntax

Use GitHub's workflow validator:

```bash
# Install actionlint
brew install actionlint  # macOS
# or
go install github.com/rhysd/actionlint/cmd/actionlint@latest  # Go

# Validate all workflows
actionlint
```

## Monitoring CI/CD

### Check workflow status

1. **Via GitHub UI**: 
   - Go to the "Actions" tab in the repository
   - View workflow runs, logs, and artifacts

2. **Via Badges**: 
   - Badges in README.md show current status
   - Click badges to see workflow details

3. **Via API**:
   ```bash
   # Get latest workflow runs
   curl -H "Accept: application/vnd.github.v3+json" \
     https://api.github.com/repos/willtheorangeguy/LEGO-Block-Creator/actions/runs
   ```

### Debugging failed workflows

1. **View Logs**: Click on the failed job to see detailed logs
2. **Download Artifacts**: Some workflows save artifacts for debugging
3. **Re-run Jobs**: Use "Re-run jobs" button to retry failed jobs
4. **Enable Debug Logging**: 
   - Settings → Secrets → New repository secret
   - Name: `ACTIONS_STEP_DEBUG`, Value: `true`

## Best practices

### For contributors

1. **Run tests locally** before pushing:
   ```bash
   pytest
   pylint $(git ls-files '*.py')
   ```

2. **Fix failing workflows** in your PR before requesting review

3. **Check workflow status** after pushing changes

4. **Don't merge** until all checks pass

### For maintainers

1. **Review workflow logs** for failed PRs
2. **Keep workflows up to date** with latest actions versions
3. **Monitor security alerts** from CodeQL
4. **Update dependencies** regularly (Dependabot helps with this)
5. **Test workflow changes** in a separate branch first

## Troubleshooting

### Common issues

**Issue**: Tests pass locally but fail in CI
- **Solution**: Check Python version differences, ensure all dependencies are in `requirements.txt`

**Issue**: Workflow timeout
- **Solution**: Increase timeout or optimize slow tests

**Issue**: Permission denied errors
- **Solution**: Check workflow permissions in YAML file

**Issue**: Secrets not working
- **Solution**: Verify secret names match exactly (case-sensitive)

### Getting help

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Community Forum](https://github.community/)
- [Project Issues](https://github.com/willtheorangeguy/LEGO-Block-Creator/issues)

## Future enhancements

Potential improvements to CI/CD:

- [ ] Add performance benchmarking
- [ ] Add integration tests
- [ ] Add automated dependency updates
- [ ] Add automatic changelog generation
- [ ] Add release notes automation
- [ ] Add code quality metrics tracking
- [ ] Add automated security scanning for dependencies
- [ ] Add pre-commit hooks configuration

{{ support() }}
