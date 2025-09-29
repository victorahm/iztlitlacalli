# Async/Await in JavaScript

## 📋 Overview
Modern JavaScript syntax for handling asynchronous operations using async functions and the await keyword, providing a cleaner alternative to Promises and callbacks.

## 🎯 Purpose
- Handle asynchronous operations with synchronous-looking code
- Avoid callback hell and complex Promise chains
- Improve code readability and error handling
- Work with APIs, file operations, and database queries

## 💡 Implementation

### Basic Syntax
```javascript
async function functionName() {
    try {
        const result = await asyncOperation();
        return result;
    } catch (error) {
        console.error('Error:', error);
    }
}
```

### Code Examples
```javascript
// Basic async function
async function fetchUserData(userId) {
    try {
        const response = await fetch(`/api/users/${userId}`);
        const userData = await response.json();
        return userData;
    } catch (error) {
        throw new Error(`Failed to fetch user: ${error.message}`);
    }
}

// Multiple async operations
async function processData() {
    try {
        const [users, posts, comments] = await Promise.all([
            fetchUsers(),
            fetchPosts(),
            fetchComments()
        ]);
        
        return { users, posts, comments };
    } catch (error) {
        console.error('Failed to process data:', error);
    }
}

// Async arrow function
const getData = async (id) => {
    const data = await api.get(`/data/${id}`);
    return data.json();
};

// Sequential vs Parallel execution
async function sequentialExample() {
    const result1 = await operation1(); // Wait for this
    const result2 = await operation2(); // Then wait for this
    return [result1, result2];
}

async function parallelExample() {
    const [result1, result2] = await Promise.all([
        operation1(), // Start both simultaneously
        operation2()
    ]);
    return [result1, result2];
}
```

### Error Handling
```javascript
async function robustAsyncFunction() {
    try {
        const result = await riskyOperation();
        return result;
    } catch (error) {
        if (error.name === 'NetworkError') {
            return await retryOperation();
        }
        throw error; // Re-throw if can't handle
    } finally {
        // Cleanup code
        cleanup();
    }
}
```

## 🔍 Key Points
- async functions always return a Promise
- await can only be used inside async functions
- Use Promise.all() for parallel operations
- Always handle errors with try/catch
- Prefer async/await over .then() chains for readability
- Be careful with loops - await in forEach doesn't work as expected

## 🔗 Related Topics
- [[Programming/JavaScript/Promises]]
- [[Programming/JavaScript/Fetch API]]
- [[Programming/JavaScript/Error Handling]]

## 📚 References
- [MDN - async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [MDN - await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)

## 🏷️ Tags
`#javascript` `#async` `#promises` `#es2017` `#asynchronous`

---
*Created: 2024-01-15 | Last Updated: 2024-01-15*