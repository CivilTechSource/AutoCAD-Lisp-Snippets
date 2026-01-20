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
4. **Choose the appropriate snippet file** based on category (see file structure below)
5. **Edit** the relevant `.code-snippets` file
6. **Update package.json** if adding a new category file
7. **Test** your snippet thoroughly
8. **Submit** a pull request

## 📝 Snippet Guidelines

### Naming Convention
- **Snippet Names**: Use descriptive names (e.g., "AutoCAD Lisp Function Template")
- **Category-Based Prefixes**: Use consistent category prefixes:
  - `doc-` for documentation (headers, comments, version blocks)
  - `fun-` for function templates and implementations
  - `sec-` for section headers and dividers
  - `lay-` for layer management functions
  - `draw-` for drawing commands (lines, circles, text, etc.)
  - `io-` for input/output operations (user input, entity selection)
  - `util-` for utility functions (math, string manipulation, error handling)
  - `dcl-` for Dialog Control Language (DCL) components

### File Organization
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

### Choosing the Right File
When adding a new snippet, choose the appropriate file based on functionality:
- **Documentation elements** → `documentation.code-snippets`
- **Function templates or implementations** → `functions.code-snippets`
- **Section dividers** → `sections.code-snippets`
- **Layer operations** → `layers.code-snippets`
- **Drawing commands** → `drawing.code-snippets`
- **User input/entity selection** → `input-output.code-snippets`
- **Utility functions (math, strings, etc.)** → `utilities.code-snippets`
- **DCL dialog components** → `dcl.code-snippets`

If your snippet doesn't fit any existing category, propose a new category in your pull request.

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
3. **Create a test `.lsp` or `.lisp` file**
4. **Type your snippet prefix** (e.g., `doc-header`, `fun-template`) and press Tab
5. **Verify**:
   - Snippet expands correctly with category prefix
   - Placeholders work properly
   - Tab navigation works
   - Generated code is valid AutoCAD Lisp
   - Snippet appears in both autolisp and lisp language modes

### Testing Categories
Test snippets from different categories to ensure:
- **Documentation**: Headers and comments format correctly
- **Functions**: Function templates compile without errors
- **Layers**: Layer operations use proper AutoCAD Lisp syntax
- **Drawing**: Drawing commands generate valid geometry
- **Input/Output**: User input validation works as expected
- **Utilities**: Math and string functions return correct results
- **DCL**: Dialog components follow DCL syntax standards

## 📋 Pull Request Checklist

Before submitting a pull request:

- [ ] Snippet uses correct category-based prefix (`doc-`, `fun-`, `lay-`, etc.)
- [ ] Snippet is added to the appropriate category file
- [ ] Code is properly formatted and commented
- [ ] Placeholders are meaningful and helpful
- [ ] Snippet has been tested in VS Code with both autolisp and lisp files
- [ ] Description clearly explains the snippet's purpose
- [ ] No duplicate functionality with existing snippets
- [ ] If creating new category, updated package.json contributions
- [ ] Updated SNIPPET-CREATION-GUIDE.md if introducing new patterns

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