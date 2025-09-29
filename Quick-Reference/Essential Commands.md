# Essential Command Quick Reference

## 🐧 Linux Commands

### File Operations
```bash
ls -la                    # List files with details
cp source dest           # Copy files
mv old new              # Move/rename files
rm -rf directory        # Remove directory recursively
find . -name "*.txt"    # Find files by pattern
chmod 755 file          # Change permissions
chown user:group file   # Change ownership
```

### Text Processing
```bash
grep "pattern" file     # Search in files
grep -r "pattern" dir   # Recursive search
sed 's/old/new/g' file  # Replace text
awk '{print $1}' file   # Print first column
sort file               # Sort lines
uniq file              # Remove duplicates
head -n 10 file        # First 10 lines
tail -f file           # Follow file changes
```

### System Monitoring
```bash
ps aux                  # List processes
top                     # Real-time processes
htop                    # Better process viewer
df -h                   # Disk usage
du -sh directory        # Directory size
free -h                 # Memory usage
netstat -tulpn          # Network connections
```

## 💻 Git Commands

### Basic Operations
```bash
git status              # Check repository status
git add .               # Stage all changes
git commit -m "msg"     # Commit with message
git push origin main    # Push to remote
git pull                # Pull latest changes
git log --oneline       # Compact commit history
```

### Branching
```bash
git branch              # List branches
git checkout -b new     # Create and switch branch
git switch branch       # Switch to branch
git merge branch        # Merge branch into current
git branch -d branch    # Delete merged branch
```

### Undoing Changes
```bash
git reset HEAD~1        # Undo last commit (keep changes)
git reset --hard HEAD~1 # Undo last commit (lose changes)
git checkout -- file    # Discard file changes
git revert commit-hash  # Create revert commit
```

## 🐍 Python One-Liners

### File Operations
```python
# Read file lines
lines = open('file.txt').readlines()

# Write to file
with open('file.txt', 'w') as f: f.write('content')

# List comprehension
squares = [x**2 for x in range(10)]

# Filter and map
evens = [x for x in range(20) if x % 2 == 0]
```

### Data Processing
```python
# Sort dictionary by value
sorted(dict.items(), key=lambda x: x[1])

# Count occurrences
from collections import Counter; Counter(items)

# Flatten list
flat = [item for sublist in nested_list for item in sublist]

# Remove duplicates maintaining order
list(dict.fromkeys(original_list))
```

## 🌐 JavaScript Quick Hits

### Array Methods
```javascript
// Map, filter, reduce
arr.map(x => x * 2)
arr.filter(x => x > 0)
arr.reduce((sum, x) => sum + x, 0)

// Find and includes
arr.find(x => x.id === 1)
arr.includes(value)

// Destructuring
const [first, ...rest] = array
const {name, age} = object
```

### Async Operations
```javascript
// Fetch API
const data = await fetch('/api/data').then(r => r.json())

// Promise.all for parallel
const [users, posts] = await Promise.all([getUsers(), getPosts()])

// Try-catch async
try { const result = await operation() } catch (e) { console.error(e) }
```

## 📊 Regular Expressions

### Common Patterns
```regex
\d+                     # One or more digits
\w+                     # One or more word characters
\s+                     # One or more whitespace
^start                  # Beginning of line
end$                    # End of line
[a-zA-Z0-9]            # Alphanumeric character
(group)                 # Capture group
(?:non-capture)         # Non-capturing group
```

### Useful Examples
```regex
# Email validation (basic)
^[^\s@]+@[^\s@]+\.[^\s@]+$

# Phone number (US)
^\(\d{3}\)\s\d{3}-\d{4}$

# URL validation
^https?://[^\s/$.?#].[^\s]*$

# Extract text between quotes
"([^"]*)"
```

## 🏷️ Tags
`#quick-reference` `#cheat-sheet` `#commands` `#one-liners`

---
*Last Updated: 2024-01-15*