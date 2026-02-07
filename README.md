# GitHub Configuration Files

This folder contains GitHub-specific configuration for cloud execution and automation.

## 📁 Structure

```
.github/
├── workflows/
│   ├── ci.yml              # Continuous Integration (auto-runs on push)
│   └── run-mapping.yml     # Manual workflow (click to run)
├── ISSUE_TEMPLATE/
│   ├── bug_report.md       # Bug report template
│   └── feature_request.md  # Feature request template
└── PULL_REQUEST_TEMPLATE.md # Pull request template
```

## 🚀 Workflows

### ci.yml - Continuous Integration
**Triggers**: Automatically on every push/PR
**Purpose**: Test code quality and compatibility
**Actions**:
- Tests on Python 3.7-3.11
- Tests on Windows, macOS, Linux
- Runs code formatting checks
- Runs security scans

### run-mapping.yml - Cloud Execution
**Triggers**: Manual (click button in Actions tab)
**Purpose**: Run mapping process in the cloud
**Actions**:
- Loads your data files from repository
- Runs the mapping process
- Uploads results as downloadable artifacts
- Shows statistics in summary

**How to Use**:
1. Upload data files to `data/input/`
2. Go to Actions tab
3. Click "Run SBS Mapping (Cloud Execution)"
4. Click "Run workflow"
5. Fill in parameters
6. Download results from Artifacts

## 🐛 Issue Templates

### bug_report.md
Used when users report bugs. Provides structured format for:
- Bug description
- Steps to reproduce
- Environment details
- Error messages

### feature_request.md
Used when users suggest new features. Includes:
- Feature description
- Use case
- Expected impact
- Implementation ideas

## 🔄 Pull Request Template

Used when contributors submit code changes. Ensures:
- Clear description
- Testing completed
- Documentation updated
- Code quality checks passed

## ⚙️ Configuration Tips

### Enabling Workflows
1. Go to repository Settings
2. Click "Actions" in left sidebar
3. Select "Allow all actions and reusable workflows"
4. Click "Save"

### Customizing Workflows
Edit `.yml` files to:
- Change Python versions
- Add more tests
- Modify parameters
- Adjust retention periods

### Security
- Workflows only access files in your repository
- No secrets are exposed in logs
- Use private repository for sensitive data
- Add secrets in Settings → Secrets and variables

## 📊 Usage Statistics

Workflows consume GitHub Actions minutes:
- **Free tier**: 2,000 minutes/month
- **Linux runners**: No multiplier
- **Windows runners**: 2x multiplier
- **macOS runners**: 10x multiplier

**Recommendation**: Use Linux runners (default) to maximize free tier.

## 🔒 Security Notes

- Never commit API keys or passwords
- Use GitHub Secrets for sensitive data
- Keep workflows in `.github/workflows/`
- Review workflow permissions regularly

## 📚 Learn More

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow Syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
- [GitHub Templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests)

---

*These configurations enable cloud execution without local installation!*
