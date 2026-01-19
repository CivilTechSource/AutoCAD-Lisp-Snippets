# AutoCAD Lisp Snippets

A lightweight VS Code extension providing useful AutoCAD Lisp code snippets for faster development. Includes header templates, comment blocks, and common function patterns to streamline your AutoCAD Lisp programming workflow.

## ✨ Features

- **Header Templates**: Professional function headers with author, version, and description fields
- **Comment Blocks**: Formatted comment sections for better code organization  
- **Version Control**: Standardized version section templates
- **Layer Functions**: Complete layer search and create functionality
- **Tab Navigation**: Easy placeholder navigation using Tab key
- **Lightweight**: Snippet-based approach for fast performance

## 🚀 Available Snippets

| Trigger | Description | Output |
|---------|-------------|--------|
| `lisph` | Function Header Template | Professional header with author, version, date |
| `lispc` | Comment Block | Formatted comment section |
| `lispv` | Version Section | Version tracking template |
| `fun-layersearch&add` | Layer Search & Create Function | Complete layer management function |

## 📖 Usage

1. **Install the extension** from VS Code Marketplace or GitHub
2. **Open any `.lsp`, `.lisp`, or `.fas` file** in VS Code
3. **Type a snippet trigger** (e.g., `lisph`)
4. **Press Tab** to expand the snippet
5. **Use Tab** to navigate between placeholders
6. **Customize** the placeholders as needed

### Example Usage

Type `lisph` and press Tab to get:
```lisp
;;------------------=={ Function Name }==------------------;;
;;                                                                      ;;
;;  Brief description of what this function does                   ;;
;;                                                                      ;;
;;----------------------------------------------------------------------;;
;;  Author:  Ferdi Jafar - Civil Tech Source                           ;;
;;----------------------------------------------------------------------;;
;;  Version 1.0    -    Date                                       ;;
;;                                                                      ;;
;;  Release notes                                                  ;;
;;----------------------------------------------------------------------;;
```

Type `fun-layersearch&add` and press Tab to get a complete layer management function with customizable parameters.

## 🔧 Requirements

- **VS Code**: Version 1.108.1 or higher
- **AutoCAD**: For testing the generated Lisp code (optional)
- **File Extensions**: Works with `.lsp`, `.lisp`, and `.fas` files

## 🤝 Contributing

We welcome contributions! This is an open source project hosted on GitHub.

### How to Contribute
1. **Fork** this repository
2. **Create** a new branch for your feature
3. **Add** your snippets to `snippets/snippets.code-snippets`
4. **Test** your changes
5. **Submit** a pull request

### Adding New Snippets
Edit the `snippets/snippets.code-snippets` file and add your snippet following this format:
```json
"Your Snippet Name": {
  "prefix": "trigger-word",
  "body": [
    "Line 1 with ${1:placeholder}",
    "Line 2 with ${2:another-placeholder}",
    "$0"
  ],
  "description": "Description of your snippet"
}
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🐛 Issues & Support

- **Report Bugs**: [GitHub Issues](https://github.com/CivilTechSource/AutoCAD-Lisp-Snippets/issues)
- **Request Features**: [GitHub Issues](https://github.com/CivilTechSource/AutoCAD-Lisp-Snippets/issues)
- **Documentation**: [GitHub Repository](https://github.com/CivilTechSource/AutoCAD-Lisp-Snippets)

## 👨‍💻 Author

**Ferdi Jafar - Civil Tech Source**
- GitHub: [@CivilTechSource](https://github.com/CivilTechSource)

## 🙏 Acknowledgments

- AutoCAD Lisp community for inspiration
- VS Code extension development community
- All contributors to this project

---

**Happy AutoCAD Lisp coding!** 🎉
