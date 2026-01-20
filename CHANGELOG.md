# Change Log

All notable changes to the AutoCAD Lisp Snippets extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.5] - 2026-01-20

### Fixed
- **LANGUAGE DETECTION FIX**: Added support for "autolisp" language in addition to "lisp"
- Snippets now work automatically in AutoCAD Lisp files without manual language mode setting
- Fixed issue where .lsp files detected as "autolisp" wouldn't trigger snippets

### Added
- Dual language support: snippets work for both "autolisp" and "lisp" language modes
- Improved compatibility with different VS Code AutoCAD Lisp extensions

### Technical
- Added "autolisp" language contribution to package.json
- Maintained backward compatibility with "lisp" language detection
- Automatic snippet activation in AutoCAD Lisp files

## [1.0.4] - 2026-01-20

### Fixed
- **SYNTAX HIGHLIGHTING FIX**: Removed language definition to prevent conflicts with other Lisp extensions
- Extension now focuses purely on snippets without interfering with existing syntax highlighting
- Eliminates potential conflicts with specialized AutoCAD Lisp syntax extensions

### Changed
- Removed file extension associations (.lsp, .lisp, .fas) from extension
- Users can manually set language mode to "lisp" when needed for snippet activation
- Cleaner, more focused extension architecture

### Technical
- Simplified package.json by removing language contributions
- Extension now works alongside any existing Lisp syntax highlighting extensions
- Reduced potential for conflicts and improved compatibility

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