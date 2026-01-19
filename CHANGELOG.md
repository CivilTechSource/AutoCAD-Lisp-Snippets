# Change Log

All notable changes to the AutoCAD Lisp Snippets extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.3] - 2026-01-19

### Added
- Comprehensive documentation for community contributions
- DEVELOPMENT-GUIDE.md with complete workflow instructions
- SNIPPET-CREATION-GUIDE.md for community snippet development
- Contributing guidelines and best practices

### Improved
- Enhanced README.md with professional formatting
- Better project documentation structure

## [1.0.2] - 2026-01-19

### Added
- New `lispf` snippet for basic function templates
- Function template with parameters, local variables, and description placeholders

### Enhanced
- Improved snippet testing workflow
- Better placeholder organization in function templates

## [1.0.1] - 2026-01-19

### Fixed
- **CRITICAL FIX**: Added language associations for .lsp, .lisp, and .fas files
- Extension now properly recognizes AutoCAD Lisp files
- Snippets now trigger correctly in Lisp files

### Added
- Language definition for AutoCAD Lisp in package.json
- File extension associations (.lsp, .lisp, .fas)

### Technical
- Fixed extension activation issues
- Improved language recognition

## [1.0.0] - 2026-01-19

### Added
- Initial release of AutoCAD Lisp Snippets extension
- Core snippet collection with 4 essential snippets:
  - `lisph` - Professional function header template
  - `lispc` - Formatted comment block
  - `lispv` - Version section template  
  - `fun-layersearch&add` - Complete layer search and create function

### Features
- Tab-navigable placeholders for all snippets
- AutoCAD Lisp specific formatting and conventions
- Professional header templates with author attribution
- Layer management utilities
- Comment formatting tools

### Documentation
- README.md with usage examples and installation instructions
- MIT License for open source distribution
- GitHub repository setup for community contributions
- VS Code Marketplace compatibility

### Technical
- VS Code engine compatibility: ^1.108.1
- Snippet-based approach for lightweight performance
- Proper extension packaging and distribution setup