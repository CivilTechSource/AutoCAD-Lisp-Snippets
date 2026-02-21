# VS Code Extension Update & Publishing Guide

A comprehensive step-by-step guide for updating and publishing your VS Code extension to the marketplace.

---

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Making Changes to Snippets](#making-changes-to-snippets)
3. [Updating Version Numbers](#updating-version-numbers)
4. [Updating the Changelog](#updating-the-changelog)
5. [Creating the VSIX Package](#creating-the-vsix-package)
6. [Testing the Extension Locally](#testing-the-extension-locally)
7. [Committing to Git](#committing-to-git)
8. [Publishing to VS Code Marketplace](#publishing-to-vs-code-marketplace)
9. [Troubleshooting](#troubleshooting)

---

## Prerequisites

### Required Tools

1. **Node.js and npm**: Install from [nodejs.org](https://nodejs.org/)
   ```powershell
   node --version
   npm --version
   ```

2. **vsce (Visual Studio Code Extension CLI)**:
   ```powershell
   npm install -g @vscode/vsce
   ```

3. **Git**: For version control
   ```powershell
   git --version
   ```

4. **VS Code**: The editor itself
   ```powershell
   code --version
   ```

### Publisher Account Setup

1. Create a Microsoft account if you don't have one
2. Go to [Visual Studio Marketplace Publisher Portal](https://marketplace.visualstudio.com/manage)
3. Create a publisher profile (this is your unique publisher ID)
4. Generate a Personal Access Token (PAT) from [Azure DevOps](https://dev.azure.com/)
   - Click on User Settings (top right) → Personal Access Tokens
   - Click "New Token"
   - Name: `VSCode Extension Publishing`
   - Organization: All accessible organizations
   - Expiration: Custom defined (recommend 1 year)
   - Scopes: Select **Marketplace** → Check **Manage**
   - Click "Create" and **SAVE THE TOKEN** (you won't see it again!)

---

## Making Changes to Snippets

### 1. Locate the Correct Snippet File

Our extension uses category-based organization:

```
snippets/
├── documentation.code-snippets    # doc-* prefixes
├── functions.code-snippets        # fun-* prefixes
├── sections.code-snippets         # sec-* prefixes
├── layers.code-snippets           # lay-* prefixes
├── drawing.code-snippets          # draw-* prefixes
├── input-output.code-snippets     # io-* prefixes
├── utilities.code-snippets        # util-* prefixes
└── dcl.code-snippets             # dcl-* prefixes
```

### 2. Edit the Snippet File

Open the appropriate `.code-snippets` file and add/edit snippets:

```json
{
  "Snippet Display Name": {
    "prefix": "snippet-prefix",
    "body": [
      "Line 1 with ${1:placeholder}",
      "Line 2 with ${2:another_placeholder}",
      "${0}"
    ],
    "description": "What this snippet does",
    "scope": "autolisp"
  }
}
```

**Key Points:**
- `prefix`: What you type to trigger the snippet (use category prefixes!)
- `body`: Array of code lines
- `${1:name}`: Tab-navigable placeholders (numbers indicate tab order)
- `${0}`: Final cursor position
- `scope`: Set to `"autolisp"` for AutoLisp files
- `description`: Brief explanation shown in autocomplete

### 3. Save Your Changes

Save the file in VS Code (`Ctrl + S`).

---

## Updating Version Numbers

### Understanding Semantic Versioning

Version format: **MAJOR.MINOR.PATCH** (e.g., 1.2.0)

- **MAJOR** (1.x.x): Breaking changes that require users to modify their workflow
- **MINOR** (x.2.x): New features added (backwards compatible)
- **PATCH** (x.x.1): Bug fixes and small improvements

**For our extension:**
- Adding new snippets = **MINOR** version bump (1.1.0 → 1.2.0)
- Fixing snippet bugs = **PATCH** version bump (1.1.0 → 1.1.1)
- Changing all snippet prefixes = **MAJOR** version bump (1.0.0 → 2.0.0)

### Update package.json

1. Open `package.json`
2. Find the `"version"` field (usually line 5)
3. Update the version number:

```json
{
  "name": "autocad-lisp-snippets",
  "displayName": "AutoCAD Lisp Snippets",
  "description": "...",
  "version": "1.2.0",  // ← Update this
  "engines": {
    "vscode": "^1.108.1"
  }
}
```

4. Save the file

---

## Updating the Changelog

### 1. Open CHANGELOG.md

### 2. Add New Version Entry at the Top

Follow the [Keep a Changelog](https://keepachangelog.com/) format:

```markdown
# Change Log

## [1.2.0] - 2026-02-21

### Added
- New snippet: `fun-LoopSel` - Loop through selection set
- New snippet: `doc-section` - Section header for code organization

### Changed
- Improved documentation for layer functions

### Fixed
- Fixed placeholder in `draw-circle` snippet

### Removed
- Removed deprecated `old-snippet` (use `new-snippet` instead)

## [1.1.0] - 2026-01-20
...previous versions below...
```

**Categories to use:**
- **Added**: New features/snippets
- **Changed**: Modifications to existing functionality
- **Fixed**: Bug fixes
- **Removed**: Deleted features
- **Deprecated**: Features being phased out
- **Security**: Security improvements

### 3. Save the File

---

## Creating the VSIX Package

### 1. Open Terminal in Project Directory

In VS Code, open a PowerShell terminal:
- **Menu**: Terminal → New Terminal
- **Shortcut**: `` Ctrl + ` `` (backtick)

### 2. Navigate to Project Folder (if needed)

```powershell
cd "d:\CTS\Projects - Documents\P26002 VS AutoLisp"
```

### 3. Verify VSCE is Installed

```powershell
vsce --version
```

If not installed:
```powershell
npm install -g @vscode/vsce
```

### 4. Create the VSIX Package

```powershell
vsce package
```

**Expected Output:**
```
INFO  Files included in the VSIX:
autocad-lisp-snippets-1.2.0.vsix
├─ [Content_Types].xml 
├─ extension.vsixmanifest 
└─ extension/
   ├─ LICENSE.txt
   ├─ changelog.md
   ├─ package.json
   ├─ readme.md
   └─ snippets/
      └─ ...

DONE  Packaged: D:\...\autocad-lisp-snippets-1.2.0.vsix (16 files, 18.13 KB)
```

### 5. Verify VSIX File Created

```powershell
Get-ChildItem -Filter "*.vsix" | Select-Object Name, Length, LastWriteTime
```

You should see your new `.vsix` file with today's date.

### Optional: List Package Contents

```powershell
vsce ls
```

This shows all files included in the package.

---

## Testing the Extension Locally

### Method 1: Install from VSIX (Recommended)

1. **Install the VSIX**:
   ```powershell
   code --install-extension autocad-lisp-snippets-1.2.0.vsix
   ```

2. **Reload VS Code**: Press `Ctrl + Shift + P` → Type "Reload Window" → Enter

3. **Test Snippets**:
   - Create a new `.lsp` or `.lisp` file
   - Type a snippet prefix (e.g., `fun-LoopSel`)
   - Press `Tab` to expand
   - Verify placeholders and formatting

4. **Uninstall After Testing** (if needed):
   - `Ctrl + Shift + X` to open Extensions
   - Find "AutoCAD Lisp Snippets"
   - Click gear icon → Uninstall

### Method 2: Debug Mode (For Development)

1. Open the extension project in VS Code
2. Press `F5` to launch Extension Development Host
3. A new VS Code window opens with your extension loaded
4. Test your snippets in `.lsp` files

---

## Committing to Git

### 1. Check Git Status

```powershell
git status
```

### 2. Stage All Changes

```powershell
git add .
```

Or stage specific files:
```powershell
git add package.json CHANGELOG.md snippets/functions.code-snippets
```

### 3. Commit with Descriptive Message

```powershell
git commit -m "v1.2.0: Added selection loop and section header snippets

- Added fun-LoopSel: Loop through selection set with VLA objects
- Added doc-section: Standard section header
- Updated CHANGELOG.md with v1.2.0 notes
- Bumped version to 1.2.0"
```

**Good Commit Message Format:**
```
Short summary (50 chars or less)

- Bullet point of change 1
- Bullet point of change 2
- Bullet point of change 3
```

### 4. Create Version Tag

Tags mark specific release points in your Git history:

```powershell
git tag v1.2.0
```

To add a description:
```powershell
git tag -a v1.2.0 -m "Release version 1.2.0 with new snippets"
```

### 5. Push to GitHub

Push both commits and tags:

```powershell
git push origin master
git push origin v1.2.0
```

Or push both in one command:
```powershell
git push origin master; git push origin v1.2.0
```

### 6. Verify on GitHub

1. Go to your repository: https://github.com/CivilTechSource/AutoCAD-Lisp-Snippets
2. Check the commits page
3. Check the "Releases" or "Tags" section to see your version tag

---

## Publishing to VS Code Marketplace

### Method 1: Web Portal (Easiest)

1. **Go to Publisher Portal**:
   - Visit [Visual Studio Marketplace Publisher Portal](https://marketplace.visualstudio.com/manage)
   - Sign in with your Microsoft account

2. **Navigate to Your Extension**:
   - Click on your publisher name (e.g., "CivilTechSource")
   - Find "AutoCAD Lisp Snippets" in your extensions list
   - Click on it

3. **Upload New Version**:
   - Click the **"Update"** button (or "..." menu → Update)
   - Click "Upload Extension"
   - Browse to your `.vsix` file: `autocad-lisp-snippets-1.2.0.vsix`
   - Click "Upload"

4. **Wait for Validation**:
   - The marketplace validates your extension (usually 2-5 minutes)
   - You'll see status: "Validating" → "Publishing" → "Published"

5. **Verify Publication**:
   - Go to your extension's marketplace page
   - Verify the new version number is displayed
   - Check that the CHANGELOG shows your latest changes

### Method 2: Command Line with vsce

#### First Time Setup (One-time)

```powershell
vsce login CivilTechSource
```

Enter your Personal Access Token (PAT) when prompted.

#### Publish Command

```powershell
vsce publish
```

This will:
1. Automatically bump the version based on your `package.json`
2. Create the VSIX package
3. Upload to the marketplace

**Or publish specific version:**
```powershell
vsce publish minor  # Bumps 1.1.0 → 1.2.0
vsce publish patch  # Bumps 1.1.0 → 1.1.1
vsce publish major  # Bumps 1.0.0 → 2.0.0
```

### What Happens After Publishing?

1. **Validation** (~2-5 minutes): Microsoft validates your extension
2. **Availability** (~1-2 hours): Extension appears in VS Code search
3. **Auto-Updates** (~24 hours): Users with auto-update enabled receive the update
4. **Manual Updates**: Users can immediately update via Extensions panel

---

## Troubleshooting

### Common Issues and Solutions

#### "Command not found: vsce"

**Problem**: vsce is not installed or not in PATH

**Solution**:
```powershell
npm install -g @vscode/vsce
```

#### "Error: Extension not found"

**Problem**: Not logged into vsce

**Solution**:
```powershell
vsce login YourPublisherName
```

#### "Package validation failed"

**Problem**: Missing required files or invalid package.json

**Solution**:
1. Ensure `README.md`, `LICENSE`, and `CHANGELOG.md` exist
2. Check `package.json` for required fields:
   - `name`, `displayName`, `description`, `version`
   - `publisher`, `categories`, `engines`
   - `repository`, `license`

#### "Version already exists"

**Problem**: Trying to upload the same version twice

**Solution**:
1. Bump the version in `package.json`
2. Update `CHANGELOG.md`
3. Recreate VSIX with `vsce package`

#### VSIX file is too large

**Problem**: Package exceeds size limits

**Solution**:
1. Create `.vscodeignore` file to exclude unnecessary files:
   ```
   .vscode/**
   .git/**
   .gitignore
   **/*.vsix
   **/node_modules/**
   **/.DS_Store
   **/Thumbs.db
   ```

2. Check what's included:
   ```powershell
   vsce ls
   ```

#### Git push rejected

**Problem**: Remote has changes you don't have locally

**Solution**:
```powershell
git pull origin master
git push origin master
```

#### Snippets not working after update

**Problem**: VS Code cached old extension

**Solution**:
1. Reload VS Code: `Ctrl + Shift + P` → "Reload Window"
2. Or restart VS Code completely
3. Check extension version: Extensions → AutoCAD Lisp Snippets → Check version number

---

## Quick Reference Checklist

Use this checklist for every update:

- [ ] **1. Edit snippet files** in appropriate category folder
- [ ] **2. Update version** in `package.json` (bump MINOR for new features)
- [ ] **3. Update CHANGELOG.md** with version, date, and changes
- [ ] **4. Test locally** by pressing `F5` in VS Code
- [ ] **5. Create VSIX**: `vsce package`
- [ ] **6. Test VSIX**: `code --install-extension *.vsix`
- [ ] **7. Stage changes**: `git add .`
- [ ] **8. Commit**: `git commit -m "v1.x.x: Description"`
- [ ] **9. Tag version**: `git tag v1.x.x`
- [ ] **10. Push to GitHub**: `git push origin master; git push origin v1.x.x`
- [ ] **11. Upload to marketplace** via web portal or `vsce publish`
- [ ] **12. Verify** extension appears with new version on marketplace

---

## Useful Commands Reference

### Package Management
```powershell
# Create VSIX package
vsce package

# List files in package
vsce ls

# Show package version
vsce show YourPublisherName.extension-name
```

### Publishing
```powershell
# Login to publisher account
vsce login YourPublisherName

# Publish extension
vsce publish

# Publish with version bump
vsce publish minor   # 1.1.0 → 1.2.0
vsce publish patch   # 1.1.0 → 1.1.1
vsce publish major   # 1.0.0 → 2.0.0
```

### Testing
```powershell
# Install locally
code --install-extension extension-name-1.2.0.vsix

# Uninstall
code --uninstall-extension PublisherName.extension-name

# List installed extensions
code --list-extensions
```

### Git Commands
```powershell
# Check status
git status

# Stage all changes
git add .

# Commit
git commit -m "Message"

# Create tag
git tag v1.2.0

# Push commits and tags
git push origin master
git push origin v1.2.0

# View tags
git tag -l
```

---

## Additional Resources

### Official Documentation
- [VS Code Extension API](https://code.visualstudio.com/api)
- [Publishing Extensions](https://code.visualstudio.com/api/working-with-extensions/publishing-extension)
- [vsce Documentation](https://github.com/microsoft/vsce)
- [Snippet Syntax](https://code.visualstudio.com/docs/editor/userdefinedsnippets)

### Our Project
- [GitHub Repository](https://github.com/CivilTechSource/AutoCAD-Lisp-Snippets)
- [VS Code Marketplace Page](https://marketplace.visualstudio.com/items?itemName=CivilTechSource.autocad-lisp-snippets)
- [SNIPPET-CREATION-GUIDE.md](SNIPPET-CREATION-GUIDE.md) - Detailed snippet writing guide
- [CONTRIBUTING.md](CONTRIBUTING.md) - Contribution guidelines

### Semantic Versioning
- [Semantic Versioning Specification](https://semver.org/)
- [Keep a Changelog](https://keepachangelog.com/)

---

## Need Help?

If you encounter issues not covered in this guide:

1. **Check existing issues**: [GitHub Issues](https://github.com/CivilTechSource/AutoCAD-Lisp-Snippets/issues)
2. **Create new issue**: Include error messages, VS Code version, and steps to reproduce
3. **Contact**: [@CivilTechSource](https://github.com/CivilTechSource)

---

**Happy Coding! 🚀**

*Last Updated: February 21, 2026*
