# Bash Script Functions and Best Practices

## 📋 Overview
Essential patterns for writing maintainable and robust bash scripts, including function definitions, error handling, and common best practices.

## 🎯 Purpose
Create reusable, reliable bash scripts for automation, system administration, and development workflows.

## 💡 Implementation

### Function Definition and Usage
```bash
#!/bin/bash

# Basic function definition
function greet() {
    echo "Hello, $1!"
}

# Alternative syntax (preferred)
greet() {
    local name="$1"
    echo "Hello, $name!"
}

# Function with return value
check_file() {
    local file="$1"
    if [[ -f "$file" ]]; then
        return 0  # Success
    else
        return 1  # Failure
    fi
}

# Using functions
greet "World"
if check_file "/etc/passwd"; then
    echo "File exists"
fi
```

### Error Handling and Best Practices
```bash
#!/bin/bash
set -euo pipefail  # Exit on error, undefined vars, pipe failures

# Script header with metadata
readonly SCRIPT_NAME="${0##*/}"
readonly SCRIPT_DIR="$(cd "$(dirname "${0}")" && pwd)"

# Logging function
log() {
    echo "[$(date +'%Y-%m-%d %H:%M:%S')] $*" >&2
}

# Error handling function
error() {
    log "ERROR: $*"
    exit 1
}

# Cleanup function
cleanup() {
    log "Cleaning up temporary files..."
    rm -f "$temp_file"
}
trap cleanup EXIT

# Argument validation
usage() {
    cat << EOF
Usage: $SCRIPT_NAME [OPTIONS] <input_file>

Options:
    -h, --help      Show this help message
    -v, --verbose   Enable verbose output
    -o, --output    Specify output file

Example:
    $SCRIPT_NAME -v -o result.txt input.txt
EOF
}

# Parse command line arguments
parse_args() {
    while [[ $# -gt 0 ]]; do
        case $1 in
            -h|--help)
                usage
                exit 0
                ;;
            -v|--verbose)
                VERBOSE=1
                shift
                ;;
            -o|--output)
                OUTPUT_FILE="$2"
                shift 2
                ;;
            -*)
                error "Unknown option: $1"
                ;;
            *)
                INPUT_FILE="$1"
                shift
                ;;
        esac
    done
}
```

### Useful Utility Functions
```bash
# Check if command exists
command_exists() {
    command -v "$1" >/dev/null 2>&1
}

# Retry function
retry() {
    local retries=$1
    shift
    
    for ((i=1; i<=retries; i++)); do
        if "$@"; then
            return 0
        fi
        log "Attempt $i failed. Retrying..."
        sleep 1
    done
    
    error "Command failed after $retries attempts: $*"
}

# Confirm prompt
confirm() {
    local prompt="${1:-Are you sure?}"
    read -p "$prompt [y/N]: " -n 1 -r
    echo
    [[ $REPLY =~ ^[Yy]$ ]]
}

# Create backup
backup_file() {
    local file="$1"
    if [[ -f "$file" ]]; then
        cp "$file" "${file}.backup.$(date +%Y%m%d_%H%M%S)"
        log "Created backup of $file"
    fi
}
```

## 🔍 Key Points
- Always use `set -euo pipefail` for robust scripts
- Use local variables in functions
- Validate inputs and provide helpful error messages
- Use meaningful function and variable names
- Add proper logging and error handling
- Include usage/help information
- Use trap for cleanup operations

## ⚠️ Warnings/Gotchas
- Quote variables to prevent word splitting: `"$var"`
- Use `[[ ]]` instead of `[ ]` for tests
- Be careful with file paths containing spaces
- Always check exit codes of important commands
- Use `readonly` for constants

## 🔗 Related Topics
- [[Programming/Bash/Command Line Arguments]]
- [[Programming/Bash/Error Handling]]
- [[Linux/Commands/grep]]

## 📚 References
- [Bash Manual](https://www.gnu.org/software/bash/manual/)
- [ShellCheck](https://www.shellcheck.net/) - Script analysis tool

## 🏷️ Tags
`#bash` `#scripting` `#functions` `#best-practices` `#automation`

---
*Created: 2024-01-15 | Last Updated: 2024-01-15*