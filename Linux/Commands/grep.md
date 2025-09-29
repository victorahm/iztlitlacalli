# grep Command

## 📋 Overview
grep (Global Regular Expression Print) is a command-line utility for searching text patterns in files or input streams using regular expressions.

## 🎯 Purpose
Search for specific patterns, strings, or regular expressions in files, making it essential for log analysis, code searching, and text processing.

## 💻 Command/Configuration

### Basic Syntax
```bash
grep [options] pattern [file(s)]
```

### Common Usage Examples
```bash
# Basic pattern search
grep "error" logfile.txt

# Case-insensitive search
grep -i "ERROR" logfile.txt

# Search recursively in directories
grep -r "function" /path/to/code/

# Show line numbers
grep -n "TODO" *.py

# Search for whole words only
grep -w "test" file.txt

# Invert match (show lines that don't match)
grep -v "debug" logfile.txt

# Count matching lines
grep -c "warning" logfile.txt

# Show context around matches
grep -A 3 -B 3 "error" logfile.txt  # 3 lines after and before

# Multiple patterns
grep -E "error|warning|critical" logfile.txt
```

## ⚙️ Options & Parameters
- `-i, --ignore-case`: Ignore case distinctions
- `-r, --recursive`: Search directories recursively
- `-n, --line-number`: Show line numbers
- `-w, --word-regexp`: Match whole words only
- `-v, --invert-match`: Invert the match (show non-matching lines)
- `-c, --count`: Count matching lines
- `-A, --after-context=NUM`: Show NUM lines after match
- `-B, --before-context=NUM`: Show NUM lines before match
- `-C, --context=NUM`: Show NUM lines before and after match

## 🔍 Key Points
- Supports basic and extended regular expressions
- Can search multiple files simultaneously
- Extremely fast for large files
- Pipe-friendly - works great with other commands
- Essential for log analysis and debugging

## ⚠️ Warnings/Gotchas
- Special regex characters need escaping in basic mode
- Use `-E` for extended regex to avoid escaping
- Large binary files can cause unexpected output

## 🔗 Related Topics
- [[Linux/Commands/awk]]
- [[Linux/Commands/sed]]
- [[Linux/Text-Processing/Regular Expressions]]

## 📚 References
- `man grep` - Manual page
- [GNU Grep Manual](https://www.gnu.org/software/grep/manual/)

## 🏷️ Tags
`#command` `#text-processing` `#search` `#regex`

---
*Created: 2024-01-15 | Last Updated: 2024-01-15*