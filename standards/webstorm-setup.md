# WebStorm/IntelliJ IDEA Setup Guide

This guide helps you configure WebStorm or IntelliJ IDEA to follow the project's coding standards.

## Prerequisites

1. Install the following plugins (if not already installed):
   - **Prettier** (usually built-in)
   - **ESLint** (usually built-in)
   - **EditorConfig** (usually built-in)

## Configuration Steps

### 1. EditorConfig

WebStorm automatically detects and uses the `.editorconfig` file in the project root. No additional configuration needed.

### 2. ESLint Setup

1. Go to **File → Settings** (Windows/Linux) or **WebStorm → Preferences** (macOS)
2. Navigate to **Languages & Frameworks → JavaScript → Code Quality Tools → ESLint**
3. Select **Automatic ESLint configuration**
4. Check **Run eslint --fix on save**
5. Click **OK**

### 3. Prettier Setup

1. Go to **File → Settings** (Windows/Linux) or **WebStorm → Preferences** (macOS)
2. Navigate to **Languages & Frameworks → JavaScript → Prettier**
3. Set **Prettier package** to `<project_root>/node_modules/prettier` (or install globally)
4. Check **On 'Reformat Code' action**
5. Check **On save**
6. Set **Run for files** to: `{**/*,*}.{js,ts,jsx,tsx,json,css,html}`
7. Click **OK**

### 4. Code Style Settings

#### JavaScript

1. Go to **File → Settings → Editor → Code Style → JavaScript**
2. Set **Tab size**: `4`
3. Set **Indent**: `4`
4. Check **Use tab character**: `unchecked` (use spaces)
5. In the **Punctuation** tab:
   - Select **Use single quotes**
   - Uncheck **Trailing comma**
6. In the **Wrapping and Braces** tab:
   - Set **Hard wrap at**: `120`

#### HTML

1. Go to **File → Settings → Editor → Code Style → HTML**
2. Set **Tab size**: `2`
3. Set **Indent**: `2`
4. Set **Hard wrap at**: `120`

#### CSS

1. Go to **File → Settings → Editor → Code Style → CSS**
2. Set **Tab size**: `2`
3. Set **Indent**: `2`
4. Set **Hard wrap at**: `120`

### 5. File and Code Templates

To match the naming conventions, you can create custom file templates:

1. Go to **File → Settings → Editor → File and Code Templates**
2. Create templates for:
   - JavaScript Classes (PascalCase)
   - JavaScript Utilities (camelCase)
   - Test files (with `.test.js` suffix)

### 6. Inspections

1. Go to **File → Settings → Editor → Inspections**
2. Enable JavaScript inspections:
   - **JavaScript → Code quality tools → ESLint** (check enabled)
   - **JavaScript → Potentially confusing code constructs → Confusing function expression** (enable)
   - **JavaScript → General → Equality operator may cause type coercion** (enable)

## Recommended Additional Settings

### Enable "Reformat on Save"

1. Go to **File → Settings → Tools → Actions on Save**
2. Check **Reformat code**
3. Check **Run eslint --fix**
4. Check **Run Prettier**

### Line Separator

1. Go to **File → Settings → Editor → Code Style**
2. Set **Line separator** to: `Unix and macOS (\n)`

## Installing Required npm Packages

Run the following command in your project root:

```bash
npm install --save-dev eslint prettier
```

## Verifying Setup

1. Open a JavaScript file
2. Make some changes that violate the standards (e.g., use double quotes, remove semicolons)
3. Save the file
4. The file should automatically format according to the standards

## Troubleshooting

### ESLint not working

- Make sure ESLint is installed: `npm install --save-dev eslint`
- Restart WebStorm
- Check that `.eslintrc.json` exists in project root

### Prettier not working

- Make sure Prettier is installed: `npm install --save-dev prettier`
- Restart WebStorm
- Check that `.prettierrc.json` exists in project root

### Conflicts between ESLint and Prettier

- The configurations provided are designed to work together
- ESLint handles code quality and some stylistic rules
- Prettier handles code formatting
- If conflicts occur, Prettier's formatting takes precedence

## Quick Reference

| Setting | JavaScript | HTML | CSS |
|---------|------------|------|-----|
| Indent | 4 spaces | 2 spaces | 2 spaces |
| Max Line Length | 120 | 120 | 120 |
| Quotes | Single | Double | Double |
| Semicolons | Required | N/A | Required |
| Trailing Comma | None | N/A | N/A |
