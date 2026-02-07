# 🌥️ Running SBS Mapping System on GitHub (Cloud-Based)
## No Local Installation Required!

---

## 🎯 Overview

You can run the **entire SBS Mapping System directly on GitHub** without installing anything on your PC. This guide covers three methods:

1. **🚀 GitHub Codespaces** - Full cloud IDE (recommended)
2. **⚡ GitHub Actions** - Automated cloud execution
3. **📓 Binder** - Cloud Jupyter notebooks

---

## Method 1: GitHub Codespaces (Recommended)

### What is Codespaces?
- Full Visual Studio Code in your browser
- Pre-configured Python environment
- All dependencies auto-installed
- 60 hours/month FREE for personal accounts

### Step-by-Step Setup

#### 1. Upload Files to GitHub
First, upload your project to GitHub (see GITHUB_DEPLOYMENT_GUIDE.md)

#### 2. Launch Codespace
1. Go to your repository on GitHub
2. Click the **"Code"** button (green button)
3. Click the **"Codespaces"** tab
4. Click **"Create codespace on main"**

![Codespace Launch](https://docs.github.com/assets/cb-77061/images/help/codespaces/new-codespace-button.png)

Wait 2-3 minutes while GitHub:
- Creates your cloud environment
- Installs Python 3.11
- Installs all dependencies from requirements.txt
- Sets up VS Code

#### 3. Upload Your Data Files

**Option A: Upload via UI**
1. In Codespace, click the **Explorer** icon (left sidebar)
2. Right-click → **New Folder** → Name it `data/input`
3. Right-click `data/input` → **Upload**
4. Select your files:
   - `SBS_V2_to_V3_Map.xlsx`
   - `your_pricelist.xlsx`

**Option B: Upload via GitHub**
1. In your GitHub repository, navigate to `data/input/`
2. Click **"Add file" → "Upload files"**
3. Drag and drop your data files
4. Commit the upload
5. Codespace will auto-sync

#### 4. Run the Mapping

**Using Terminal:**
```bash
python sbs_mapping_cli.py \
    --v2v3-file data/input/SBS_V2_to_V3_Map.xlsx \
    --pricelist data/input/your_pricelist.xlsx \
    --output-dir data/output
```

**Using Jupyter Notebook:**
1. Open `sbs_mapping_notebook.ipynb`
2. Click **"Run All"** or run cells step-by-step
3. Follow the interactive guide

#### 5. Download Results

**Method A: Via UI**
1. Navigate to `data/output/` in Explorer
2. Right-click the result files
3. Click **"Download"**

**Method B: Via Terminal**
```bash
# Zip all results
zip -r results.zip data/output/

# Download will appear in Downloads panel
```

#### 6. Stop Codespace
When done:
1. Click **"Codespaces"** menu (bottom left)
2. Click **"Stop Current Codespace"**

**Important**: Codespaces auto-stop after 30 min of inactivity.

---

## Method 2: GitHub Actions (Automated Execution)

### What is GitHub Actions?
- Run code automatically on GitHub servers
- No manual setup needed
- Trigger with a button click
- Download results as artifacts

### Step-by-Step Setup

#### 1. Prepare Your Repository

Ensure you have these files uploaded:
```
your-repo/
├── .github/workflows/run-mapping.yml  ← We created this
├── sbs_mapping_cli.py
├── sbs_ai_mapping_system.py
├── requirements.txt
└── data/
    └── input/
        ├── SBS_V2_to_V3_Map.xlsx
        └── your_pricelist.xlsx
```

#### 2. Upload Data Files
1. Go to your repository on GitHub
2. Navigate to `data/input/` (create folder if needed)
3. Click **"Add file" → "Upload files"**
4. Upload:
   - Your SBS V2-V3 mapping file
   - Your price list file
5. Commit the files

⚠️ **Security Note**: If your data is sensitive, use a **private repository**.

#### 3. Run the Workflow

1. Go to your repository
2. Click **"Actions"** tab
3. Click **"Run SBS Mapping (Cloud Execution)"** workflow
4. Click **"Run workflow"** button (right side)
5. Fill in parameters:

| Parameter | Description | Example |
|-----------|-------------|---------|
| Threshold | Similarity threshold | `0.60` |
| V2-V3 File | Path to mapping file | `data/input/SBS_V2_to_V3_Map.xlsx` |
| Price List | Path to price list | `data/input/pricelist.xlsx` |
| Code Column | Code column name | `Code` |
| Desc Column | Description column | `Description` |
| Price Column | Price column name | `Price` |

6. Click **"Run workflow"** (green button)

#### 4. Monitor Progress

1. The workflow will appear in the list
2. Click on it to see live progress
3. Wait 5-30 minutes (depending on data size)
4. ✅ Green checkmark = Success
5. ❌ Red X = Failed (check logs)

#### 5. Download Results

1. Scroll down to **"Artifacts"** section
2. Click **"mapping-results-[number]"**
3. A zip file will download containing:
   - `mapping_results.xlsx` - All mappings
   - `high_confidence_mappings.xlsx` - Ready to use
   - `items_for_review.xlsx` - Needs review
   - `mapping_report.json` - Statistics
   - `mapping_visualization.png` - Charts

#### 6. View Summary

Click the workflow run to see:
- 📊 Statistics summary
- Input/output file info
- Processing time
- Success/failure status

---

## Method 3: Binder (Jupyter Notebooks Only)

### What is Binder?
- Free cloud Jupyter notebooks
- No account needed
- Best for learning/testing
- Limited to notebook interface

### Step-by-Step Setup

#### 1. Add Binder Badge

Add this to your `README.md`:

```markdown
[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/YOUR_USERNAME/sbs-mapping-system/HEAD?filepath=sbs_mapping_notebook.ipynb)
```

Replace `YOUR_USERNAME` with your GitHub username.

#### 2. Launch Binder

1. Click the Binder badge in your README
2. Wait 5-10 minutes for environment setup (first time)
3. Jupyter notebook will open in browser

#### 3. Upload Data

In Jupyter:
1. Click **"Upload"** button
2. Select your data files
3. Click **"Upload"** to confirm

#### 4. Run Notebook

1. Update file paths in notebook cells
2. Run cells in order
3. Results appear inline

#### 5. Download Results

1. Check boxes next to result files
2. Click **"Download"** button

⚠️ **Note**: Binder sessions are temporary. Download results immediately.

---

## 📊 Comparison Table

| Feature | Codespaces | GitHub Actions | Binder |
|---------|------------|----------------|--------|
| **Cost** | 60 hrs/month free | 2000 min/month free | Unlimited free |
| **Setup Time** | 2-3 minutes | Instant | 5-10 minutes |
| **Best For** | Development | Automation | Learning |
| **Interface** | Full VS Code | Button click | Jupyter only |
| **File Size Limit** | 100 GB | 2 GB per file | 100 MB |
| **Session Duration** | Hours | 6 hours max | 10 minutes idle |
| **Data Privacy** | Private repos ok | Private repos ok | Public only |
| **Recommended** | ✅ Yes | ✅ Yes | Testing only |

---

## 🎯 Which Method Should You Use?

### Use **GitHub Codespaces** if:
- ✅ You want full control and flexibility
- ✅ You need to edit code
- ✅ You have large data files
- ✅ You want the best experience

### Use **GitHub Actions** if:
- ✅ You just want to run mapping automatically
- ✅ You want scheduled/automated processing
- ✅ You don't need to see the process
- ✅ You want hands-off execution

### Use **Binder** if:
- ✅ You want to try the notebook quickly
- ✅ You're learning/testing
- ✅ Data is small (<100 MB)
- ✅ Data is not sensitive (public repo)

---

## 🔐 Security Best Practices

### For Sensitive Data:

1. **Use Private Repository**
   - Settings → Change visibility → Private
   - Only you can access

2. **Don't Commit Sensitive Files**
   - Add to `.gitignore`
   - Upload only when needed
   - Delete after use

3. **Use GitHub Secrets** (for automation)
   ```yaml
   # In workflow file
   - name: Download data from secure source
     env:
       DATA_URL: ${{ secrets.DATA_URL }}
   ```

4. **Enable Branch Protection**
   - Require reviews for merges
   - Prevent force pushes

---

## 💰 Cost Breakdown

### GitHub Codespaces (Personal Account)
- **Free Tier**: 120 core-hours/month
- **2-core machine**: 60 hours/month FREE
- **4-core machine**: 30 hours/month FREE
- **Overage**: $0.18/hour (2-core)

**Example Usage:**
- 1 hour/day mapping = **FREE** ✅
- 3 hours/day mapping = **FREE** ✅
- 5 hours/day mapping = Some overage

### GitHub Actions (Personal Account)
- **Free Tier**: 2,000 minutes/month
- **Linux runner**: FREE minutes
- **Windows/Mac**: 2x/10x multiplier

**Example Usage:**
- Daily 30-min mapping = **~15 hours/month = FREE** ✅
- 3x/week 1-hour mapping = **~12 hours/month = FREE** ✅

### Binder
- **Always FREE** ✅
- Funded by donations
- No limits on usage

---

## 📋 Setup Checklist

### Pre-Deployment:
- [ ] Upload project to GitHub
- [ ] Add `.devcontainer/devcontainer.json`
- [ ] Add `.github/workflows/run-mapping.yml`
- [ ] Create `data/input/` folder structure
- [ ] Update `.gitignore` for data files

### For Codespaces:
- [ ] Enable Codespaces in repo settings
- [ ] Upload data files
- [ ] Launch Codespace
- [ ] Run mapping
- [ ] Download results
- [ ] Stop Codespace

### For GitHub Actions:
- [ ] Upload data to `data/input/`
- [ ] Enable Actions in repo settings
- [ ] Configure workflow parameters
- [ ] Run workflow
- [ ] Download artifacts

---

## 🐛 Troubleshooting

### Codespace Won't Start
**Solution**: 
- Check billing settings
- Verify free hours remaining
- Try again in a few minutes

### GitHub Actions Fails
**Solution**:
- Check workflow logs
- Verify file paths are correct
- Ensure data files are uploaded
- Check file size limits

### Binder Times Out
**Solution**:
- Reduce data file size
- Simplify processing
- Download partial results
- Use Codespaces instead

### Out of Free Hours
**Solution**:
- Stop unused Codespaces
- Use GitHub Actions instead
- Upgrade to paid plan
- Wait for next month's quota

---

## 📞 Getting Help

### Codespaces Issues:
- [GitHub Codespaces Docs](https://docs.github.com/en/codespaces)
- [Codespaces Troubleshooting](https://docs.github.com/en/codespaces/troubleshooting)

### Actions Issues:
- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [Workflow Syntax](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)

### Binder Issues:
- [Binder Documentation](https://mybinder.readthedocs.io)
- [Binder Discourse](https://discourse.jupyter.org/c/binder)

---

## 🎓 Video Tutorials (Links)

1. **GitHub Codespaces**: https://www.youtube.com/watch?v=ozuDPmcC1io
2. **GitHub Actions**: https://www.youtube.com/watch?v=R8_veQiYBjI
3. **Binder Tutorial**: https://www.youtube.com/watch?v=owSGVOov9pQ

---

## 🚀 Quick Start Commands

### In Codespace Terminal:
```bash
# Quick run with defaults
python sbs_mapping_cli.py \
    --v2v3-file data/input/SBS_V2_to_V3_Map.xlsx \
    --pricelist data/input/pricelist.xlsx

# Custom threshold
python sbs_mapping_cli.py \
    --v2v3-file data/input/SBS_V2_to_V3_Map.xlsx \
    --pricelist data/input/pricelist.xlsx \
    --threshold 0.70

# Full customization
python sbs_mapping_cli.py \
    --v2v3-file data/input/SBS_V2_to_V3_Map.xlsx \
    --pricelist data/input/pricelist.xlsx \
    --code-col "Service Code" \
    --desc-col "Description" \
    --threshold 0.65 \
    --output-dir results
```

### Open Jupyter Notebook:
```bash
jupyter notebook sbs_mapping_notebook.ipynb
```

---

## ✅ Success Checklist

Your cloud setup is successful when:
- [ ] Codespace launches without errors
- [ ] Dependencies install automatically
- [ ] Sample mapping runs successfully
- [ ] Results files are created
- [ ] Results can be downloaded
- [ ] Workflow completes with green checkmark

---

## 🌟 Pro Tips

1. **Save Money**: Stop Codespaces when not in use
2. **Speed Up**: Use Actions for batch processing
3. **Stay Organized**: Use dated output prefixes
4. **Stay Secure**: Keep sensitive data in private repos
5. **Collaborate**: Share Codespace link with team
6. **Automate**: Schedule Actions to run weekly/monthly

---

## 📈 Next Steps

1. ✅ Choose your preferred method (Codespaces recommended)
2. ✅ Follow the step-by-step guide
3. ✅ Upload your first data files
4. ✅ Run your first cloud mapping
5. ✅ Download and verify results
6. ✅ Set up automation if needed

---

**🎉 You're now running the SBS Mapping System entirely in the cloud!**

*No PC installation required • Works on any device with a browser • Professional cloud infrastructure*

---

## 📝 Additional Resources

- [GitHub Codespaces Quickstart](https://docs.github.com/en/codespaces/getting-started/quickstart)
- [GitHub Actions Quickstart](https://docs.github.com/en/actions/quickstart)
- [Project Documentation](SBS_MAPPING_DOCUMENTATION.md)
- [Quick Start Guide](QUICK_START_GUIDE.md)

---

*Last Updated: February 2026*
