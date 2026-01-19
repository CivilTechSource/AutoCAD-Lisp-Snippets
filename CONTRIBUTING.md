# Contributing to AutoCAD Lisp Snippets

Thank you for your interest in contributing to AutoCAD Lisp Snippets! This document provides guidelines for contributing to this open source project.

## 🤝 How to Contribute

### Reporting Bugs
1. Check if the bug has already been reported in [Issues](https://github.com/CivilTechSource/AutoCAD-Lisp-Snippets/issues)
2. Create a new issue with:
   - Clear description of the bug
   - Steps to reproduce
   - Expected vs actual behavior
   - VS Code version and extension version

### Suggesting Features
1. Check existing [Issues](https://github.com/CivilTechSource/AutoCAD-Lisp-Snippets/issues) for similar suggestions
2. Create a new issue with:
   - Clear description of the feature
   - Use case examples
   - Why it would benefit AutoCAD Lisp developers

### Adding New Snippets
1. **Fork** the repository
2. **Clone** your fork locally
3. **Create a branch** for your new snippet
4. **Edit** `snippets/snippets.code-snippets`
5. **Test** your snippet thoroughly
6. **Submit** a pull request

## 📝 Snippet Guidelines

### Naming Convention
- **Snippet Names**: Use descriptive names (e.g., "AutoCAD Lisp Function Template")
- **Prefixes**: Use consistent prefixes:
  - `lisp` for general AutoCAD Lisp snippets
  - `fun-` for function snippets
  - `cmd-` for command snippets

### Code Standards
- Use **consistent indentation** (tabs)
- Include **meaningful placeholders** with `${1:description}`
- Use **descriptive variable names**
- Add **comments** explaining complex logic
- Follow **AutoCAD Lisp best practices**

### Snippet Format
```json
"Snippet Name": {
  "prefix": ["trigger1", "trigger2"],
  "body": [
    "Line 1 with ${1:placeholder_name}",
    "Line 2 with ${2:another_placeholder}",
    "${3:optional_placeholder}",
    "$0"
  ],
  "description": "Clear description of what this snippet does"
}
```

### Placeholder Guidelines
- Use **meaningful placeholder names** (`${1:layer_name}` not `${1:name}`)
- Include **default values** where helpful (`${1:NEWLAYER}`)
- Use `$0` for **final cursor position**
- Keep **placeholders consistent** across similar snippets

## 🔄 Development Workflow

1. **Fork** the repository
2. **Clone** your fork:
   ```bash
   git clone https://github.com/your-username/AutoCAD-Lisp-Snippets.git
   ```
3. **Create a branch**:
   ```bash
   git checkout -b feature/new-snippet-name
   ```
4. **Make changes** and test
5. **Commit** with clear messages:
   ```bash
   git commit -m "Add layer manipulation snippet"
   ```
6. **Push** to your fork:
   ```bash
   git push origin feature/new-snippet-name
   ```
7. **Create Pull Request** on GitHub

## ✅ Testing Your Snippets

1. **Open VS Code** in the project folder
2. **Press F5** to launch Extension Development Host
3. **Create a test `.lsp` file**
4. **Type your snippet prefix** and press Tab
5. **Verify**:
   - Snippet expands correctly
   - Placeholders work properly
   - Tab navigation works
   - Generated code is valid AutoCAD Lisp

## 📋 Pull Request Checklist

Before submitting a pull request:

- [ ] Snippet follows naming conventions
- [ ] Code is properly formatted and commented
- [ ] Placeholders are meaningful and helpful
- [ ] Snippet has been tested in VS Code
- [ ] Description clearly explains the snippet's purpose
- [ ] No duplicate functionality with existing snippets

## 💬 Getting Help

- **Questions**: Create an issue with the "question" label
- **Discussions**: Use GitHub Discussions for general topics
- **Direct Contact**: Reach out to [@CivilTechSource](https://github.com/CivilTechSource)

## 🏆 Recognition

Contributors will be:
- Listed in the project's acknowledgments
- Credited in release notes for their contributions
- Given priority for feature requests and support

Thank you for helping make AutoCAD Lisp development easier for everyone! 🎉