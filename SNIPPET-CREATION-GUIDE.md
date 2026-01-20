# AutoCAD Lisp Snippet Creation Guide

A comprehensive guide for contributors to create useful AutoCAD Lisp snippets for the VS Code extension.

## 🎯 What Makes a Good AutoCAD Lisp Snippet?

### **✅ Good Snippets:**
- **Solve common problems** (layer management, entity selection, user input)
- **Save significant typing** (headers, repetitive code patterns)
- **Include meaningful placeholders** with descriptive names
- **Follow AutoCAD Lisp conventions** and best practices
- **Are well-documented** with clear descriptions

### **❌ Avoid:**
- **Single line shortcuts** (not worth a snippet)
- **Overly specific code** (too narrow use case)
- **Complex, project-specific logic**
- **Poor placeholder names** (`${1:name}` instead of `${1:layer_name}`)

## 📝 Snippet Format Structure

### **Basic Template:**
```json
{
  "Snippet Display Name": {
    "prefix": ["trigger1", "trigger2"],
    "body": [
      "Line 1 with ${1:placeholder_name}",
      "Line 2 with ${2:another_placeholder}",
      "${3:optional_with_default|default_value}",
      "$0"
    ],
    "description": "Clear explanation of what this snippet does"
  }
}
```

### **Key Components:**
- **`prefix`**: What user types to trigger (can be array for multiple triggers)
- **`body`**: Array of code lines
- **`description`**: Helpful explanation for users
- **`$0`**: Final cursor position
- **`${n:name}`**: Tab-navigable placeholders

## � File Organization

### **Snippet File Structure:**
```
snippets/
├── documentation.code-snippets    # doc-* prefixes (headers, comments)
├── functions.code-snippets        # fun-* prefixes (function templates)
├── sections.code-snippets         # sec-* prefixes (section headers)
├── layers.code-snippets           # lay-* prefixes (layer management)
├── drawing.code-snippets          # draw-* prefixes (drawing commands)
├── input-output.code-snippets     # io-* prefixes (user input/output)
├── utilities.code-snippets        # util-* prefixes (utility functions)
└── dcl.code-snippets             # dcl-* prefixes (dialog controls)
```

### **Adding New Snippets:**

1. **Choose the appropriate file** based on prefix category
2. **Follow naming conventions** for your prefix
3. **Add to package.json** if creating a new category file
4. **Update this guide** if introducing new prefix patterns

### **Creating New Categories:**
When adding a new category:
1. Create new `.code-snippets` file in `/snippets/` folder
2. Add entries to `package.json` contributes section for both `autolisp` and `lisp` languages
3. Document the new prefix pattern in this guide


### **Naming Conventions**

### **Naming Conventions**

#### **Category-Based Prefixes:**
Our snippets are organized into categories with specific prefix patterns:

- **`doc-`**: Documentation templates (headers, comments, version blocks)
- **`fun-`**: Function templates and complete functions  
- **`sec-`**: Section headers and dividers
- **`lay-`**: Layer management functions
- **`draw-`**: Drawing creation functions (lines, circles, text, etc.)
- **`io-`**: Input/Output operations (user input, entity selection)
- **`util-`**: Utility functions (math, string manipulation, error handling)
- **`dcl-`**: Dialog Control Language (DCL) components and dialogs

#### **Current Available Snippets:**

**Documentation (`doc-*`):**
- **`doc-header`**: Standard AutoCAD Lisp header with function template
- **`doc-version`**: Version section for documentation
- **`doc-comment`**: Formatted comment block

**Functions (`fun-*`):**
- **`fun-template`**: Basic function template
- **`fun-layer-check`**: Layer existence check and creation function

**Sections (`sec-*`):**
- **`sec-header`**: Section divider header

**Layers (`lay-*`):**
- **`lay-create`**: Create layer with properties
- **`lay-set-current`**: Set current drawing layer
- **`lay-freeze`**: Freeze a layer
- **`lay-list`**: Get all layer names

**Drawing (`draw-*`):**
- **`draw-line`**: Draw line between two points
- **`draw-circle`**: Draw circle with center and radius
- **`draw-rect`**: Draw rectangle with corner points
- **`draw-text`**: Draw single-line text
- **`draw-pline`**: Draw polyline through points

**Input/Output (`io-*`):**
- **`io-point`**: Get point input with validation
- **`io-string`**: Get string input with validation
- **`io-int`**: Get integer input
- **`io-real`**: Get real number input
- **`io-distance`**: Get distance input
- **`io-angle`**: Get angle input
- **`io-entity`**: Get entity selection

**Utilities (`util-*`):**
- **`util-distance`**: Calculate distance between points
- **`util-deg2rad`**: Convert degrees to radians
- **`util-rad2deg`**: Convert radians to degrees
- **`util-string`**: String utility functions
- **`util-list`**: List utility functions
- **`util-error`**: Error handler template

**DCL (`dcl-*`):**
- **`dcl-dialog`**: Basic DCL dialog template
- **`dcl-edit`**: Edit box control
- **`dcl-button`**: Button control
- **`dcl-list`**: List box control
- **`dcl-radio`**: Radio button control
- **`dcl-check`**: Checkbox control
- **`dcl-load`**: Load and show dialog function
- **`dcl-row`**: Row layout container
- **`dcl-column`**: Column layout container

#### **Examples:**
```json
"prefix": "doc-header"           // Documentation header template
"prefix": "fun-template"         // Basic function structure
"prefix": "lay-create"           // Layer creation function
"prefix": "ent-modify"           // Entity modification snippet
"prefix": "util-radians"         // Utility function for angle conversion
```

### **Code Structure Standards**

#### **Indentation:**
Use **2 spaces** for consistency:
```json
"body": [
  "(defun my-function (param1 param2 / local-vars)",
  "  \"Function description\"",
  "  (if condition",
  "    (progn",
  "      ;; True condition code",
  "      (dosomething)",
  "    )",
  "    (progn", 
  "      ;; False condition code",
  "      (dosomethingelse)",
  "    )",
  "  )",
  ")"
]
```

#### **Variable Naming:**
Use descriptive AutoCAD Lisp conventions:
```json
"body": [
  "(setq ${1:entity_name} (entsel \"Select entity: \"))",
  "(setq ${2:layer_name} \"${3:DEFAULT-LAYER}\")",
  "(setq ${4:point_list} '((0 0 0) (10 10 0)))"
]
```

### **Placeholder Best Practices**

#### **Meaningful Names:**
```json
// ✅ Good
"${1:layer_name}"
"${2:color_number}" 
"${3:linetype_name}"
"${4:function_description}"

// ❌ Poor
"${1:name}"
"${2:value}"
"${3:thing}"
"${4:text}"
```

#### **Default Values:**
```json
"body": [
  "(setq ${1:layer_name} \"${2:NEWLAYER}\")",
  "(setq ${3:color} ${4:7})",
  "(setq ${5:linetype} \"${6:CONTINUOUS}\")"
]
```

#### **Logical Tab Order:**
```json
"body": [
  "(defun ${1:function_name} (${2:parameters} / ${3:local_variables})",
  "  \"${4:Function description}\"",
  "  ${5:;; Function body}",
  "  ${6:(princ)}",
  "  $0",  // Final cursor position
  ")"
]
```

## 🎨 Common Snippet Patterns

### **1. Function Templates**

#### **Basic Function:**
```json
"Basic Function": {
  "prefix": ["fun-basic", "defun-template"],
  "body": [
    "(defun ${1:function_name} (${2:parameters} / ${3:local_variables})",
    "  \"${4:Function description}\"",
    "  ${5:;; Function implementation}",
    "  ${6:(princ)}",
    "  $0",
    ")"
  ],
  "description": "Basic AutoCAD Lisp function template"
}
```

#### **Command Function:**
```json
"Command Function": {
  "prefix": ["cmd-template", "c-function"],
  "body": [
    "(defun C:${1:COMMAND_NAME} ( / ${2:local_variables})",
    "  \"${3:Command description}\"",
    "  (setq ${4:old_cmdecho} (getvar \"CMDECHO\"))",
    "  (setvar \"CMDECHO\" 0)",
    "  ",
    "  ${5:;; Command implementation}",
    "  ",
    "  (setvar \"CMDECHO\" ${4:old_cmdecho})",
    "  (princ)",
    "  $0",
    ")"
  ],
  "description": "AutoCAD command function template"
}
```

### **2. User Input Patterns**

#### **Point Input:**
```json
"Get Point Input": {
  "prefix": ["input-point", "get-point"],
  "body": [
    "(setq ${1:point_var} (getpoint \"${2:Specify point}: \"))",
    "(if ${1:point_var}",
    "  (progn",
    "    ${3:;; Process the point}",
    "    $0",
    "  )",
    "  (princ \"\\nNo point selected.\")",
    ")"
  ],
  "description": "Get point input from user with error checking"
}
```

#### **String Input:**
```json
"Get String Input": {
  "prefix": ["input-string", "get-string"],
  "body": [
    "(setq ${1:string_var} (getstring ${2:t} \"${3:Enter text}: \"))",
    "(if (and ${1:string_var} (/= ${1:string_var} \"\"))",
    "  (progn",
    "    ${4:;; Process the string}",
    "    $0",
    "  )",
    "  (princ \"\\nNo text entered.\")",
    ")"
  ],
  "description": "Get string input with validation"
}
```

### **3. Entity Operations**

#### **Entity Selection:**
```json
"Select Entity": {
  "prefix": ["ent-select", "select-entity"],
  "body": [
    "(setq ${1:entity_selection} (entsel \"${2:Select entity}: \"))",
    "(if ${1:entity_selection}",
    "  (progn",
    "    (setq ${3:entity_name} (car ${1:entity_selection}))",
    "    (setq ${4:entity_data} (entget ${3:entity_name}))",
    "    ${5:;; Process entity}",
    "    $0",
    "  )",
    "  (princ \"\\nNo entity selected.\")",
    ")"
  ],
  "description": "Select and process a single entity"
}
```

### **4. Layer Management**

#### **Create Layer:**
```json
"Create Layer": {
  "prefix": ["layer-create", "new-layer"],
  "body": [
    "(defun create-layer (${1:layer_name} ${2:color} ${3:linetype} / )",
    "  \"Create a new layer with specified properties\"",
    "  (if (not (tblsearch \"LAYER\" ${1:layer_name}))",
    "    (progn",
    "      (command \"_LAYER\" \"_NEW\" ${1:layer_name}",
    "               \"_COLOR\" ${2:color} ${1:layer_name}",
    "               \"_LTYPE\" ${3:linetype} ${1:layer_name} \"\")",
    "      (princ (strcat \"\\nLayer '\" ${1:layer_name} \"' created.\"))",
    "      ${1:layer_name}",
    "    )",
    "    (progn",
    "      (princ (strcat \"\\nLayer '\" ${1:layer_name} \"' already exists.\"))",
    "      nil",
    "    )",
    "  )",
    ")",
    "$0"
  ],
  "description": "Create a new layer with color and linetype properties"
}
```

## 📚 AutoCAD Lisp Specific Tips

### **Common Functions to Include:**
- **User Input**: `getpoint`, `getstring`, `getint`, `getreal`, `getdist`, `getangle`
- **Entity Operations**: `entsel`, `entget`, `entmod`, `entdel`, `entnext`
- **Selection Sets**: `ssget`, `ssadd`, `ssdel`, `sslength`, `ssname`
- **System Variables**: `getvar`, `setvar`
- **Table Search**: `tblsearch`, `tblnext`
- **Commands**: `command`

### **Error Handling Patterns:**
```json
"Error Handler": {
  "prefix": ["error-handler", "lisp-error"],
  "body": [
    "(defun *error* (${1:msg})",
    "  \"Standard error handling function\"",
    "  (if (not (member ${1:msg} '(\"Function cancelled\" \"quit / exit abort\")))",
    "    (princ (strcat \"\\nError: \" ${1:msg}))",
    "  )",
    "  ${2:;; Restore system variables}",
    "  ${3:(setvar \"CMDECHO\" old_cmdecho)}",
    "  (princ)",
    ")",
    "$0"
  ],
  "description": "Standard error handling function template"
}
```

### **Local Variables Pattern:**
```json
"body": [
  "(defun ${1:function_name} (${2:parameters} / ${3:temp_var} ${4:old_cmdecho} ${5:result})",
  "  ;; Local variables: ${3:temp_var}, ${4:old_cmdecho}, ${5:result}",
  "  $0"
]
```

## ✅ Testing Your Snippets

### **1. Syntax Validation**
- **JSON Validator**: Use online tool to check syntax
- **VS Code**: Open snippet file and check for error indicators

### **2. Functional Testing**
1. **Install locally** using development guide
2. **Create test `.lsp` file**
3. **Test each trigger** and tab navigation
4. **Verify placeholder logic**
5. **Check final cursor position**

### **3. AutoCAD Testing**
- **Copy generated code** to AutoCAD
- **Load and test** the function
- **Verify syntax** is valid AutoCAD Lisp

## 📤 Contributing Your Snippets

### **1. File Location**
Add snippets to: `snippets/snippets.code-snippets`

### **2. JSON Format**
```json
{
  "existing_snippets": { ... },
  
  "Your New Snippet": {
    "prefix": ["your-trigger", "alt-trigger"],
    "body": [
      "your code here",
      "with ${1:placeholders}",
      "$0"
    ],
    "description": "Clear description of functionality"
  }
}
```

### **3. Documentation**
Update `README.md` with new snippet information:
```markdown
| `your-trigger` | Your Description | Brief explanation |
```

## 🎯 Snippet Ideas for Contributors

### **High-Priority Needs:**
- **Drawing Functions**: Line, circle, polyline creation
- **Text Functions**: Single line text, multiline text
- **Block Operations**: Insert, explode, redefine
- **Dimension Functions**: Linear, angular, radial dims
- **Math Utilities**: Distance, angle, point calculations
- **File Operations**: Open, save, export functions
- **Plot Functions**: Print setup, plot configuration

### **Medium Priority:**
- **Array Functions**: Rectangular, polar arrays
- **Modify Commands**: Move, copy, rotate, scale
- **Query Functions**: Object properties, system info
- **Conversion Utilities**: Units, coordinate systems

## 🏆 Best Snippet Examples

### **Documentation Header:**
```json
"File Header": {
  "prefix": ["header-file", "lisp-header"],
  "body": [
    ";;; ${1:filename}.lsp",
    ";;; ${2:Brief description}",
    ";;;",
    ";;; Author: ${3:Your Name}",
    ";;; Date: ${4:CURRENT_DATE}",
    ";;; Version: ${5:1.0}",
    ";;;",
    ";;; Description:",
    ";;; ${6:Detailed description of the file purpose}",
    ";;;",
    ";;; Usage:",
    ";;; ${7:How to use this file}",
    ";;;",
    "",
    "$0"
  ],
  "description": "Complete file header template"
}
```

## 📋 Contribution Checklist

Before submitting your snippet:

- [ ] **Prefix follows naming convention**
- [ ] **Code uses consistent indentation (2 spaces)**
- [ ] **Placeholders have descriptive names**
- [ ] **Tab order makes logical sense**
- [ ] **Description clearly explains functionality**
- [ ] **Code tested in VS Code and AutoCAD**
- [ ] **JSON syntax is valid**
- [ ] **No duplicate functionality with existing snippets**
- [ ] **Follows AutoCAD Lisp best practices**

---

**Start contributing and help make AutoCAD Lisp development faster for everyone!** 🚀

## 📞 Need Help?

- **Questions**: Open an issue on GitHub
- **Examples**: Check existing snippets in the codebase
- **AutoCAD Lisp Help**: [Autodesk Developer Documentation](https://help.autodesk.com/view/OARX/2024/ENU/)

**Happy snippet creation!** 🎉