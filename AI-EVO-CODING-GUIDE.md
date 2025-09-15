# 🤖 AI Assistant Guide: Coding .evo Files

> **Complete Guide for AI Assistants on EVO Programming Language**

## 📋 Table of Contents
1. [EVO Language Overview](#evo-language-overview)
2. [File Structure & Syntax](#file-structure--syntax)
3. [PHP-JavaScript Bridge](#php-javascript-bridge)
4. [Built-in Framework Support](#built-in-framework-support)
5. [Custom EVO Syntax](#custom-evo-syntax)
6. [Best Practices](#best-practices)
7. [Common Patterns](#common-patterns)
8. [Error Handling](#error-handling)
9. [Examples & Templates](#examples--templates)

## 🌟 EVO Language Overview

EVO is a hybrid programming language that seamlessly bridges PHP and JavaScript. When coding .evo files, remember:

- **File Extension**: Always use `.evo` extension
- **Mixed Content**: Can contain HTML, PHP, JavaScript, CSS in one file
- **Processing**: Files are processed by `evo_handler.php`
- **Output**: Renders as HTML with embedded PHP and JavaScript

## 📁 File Structure & Syntax

### Basic .evo File Template
```evo
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EVO Application</title>
    <!-- Frameworks are auto-included -->
</head>
<body>
    <!-- HTML Content -->
    
    <?php
    // PHP Server-side Code
    ?>
    
    <script>
        // JavaScript Client-side Code
    </script>
</body>
</html>
```

### File Processing Order
1. **HTML Structure** - Rendered first
2. **PHP Code** - Executed server-side
3. **JavaScript** - Executed client-side
4. **EVO Syntax** - Processed and converted

## 🔗 PHP-JavaScript Bridge

### Data Passing from PHP to JavaScript
```evo
<?php
// PHP: Prepare data
$userData = [
    'name' => 'John Doe',
    'email' => 'john@example.com',
    'age' => 30
];
$jsonData = json_encode($userData);
?>

<script>
// JavaScript: Receive PHP data
const userData = <?php echo $jsonData; ?>;
console.log(userData.name); // "John Doe"

// Use the data
document.getElementById('userName').textContent = userData.name;
</script>
```

### Data Passing from JavaScript to PHP
```evo
<script>
// JavaScript: Send data to PHP
function sendDataToPHP() {
    const formData = {
        action: 'updateUser',
        data: {
            name: document.getElementById('nameInput').value,
            email: document.getElementById('emailInput').value
        }
    };
    
    fetch('evo-bridge.php', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(formData)
    })
    .then(response => response.json())
    .then(data => {
        console.log('Success:', data);
    });
}
</script>

<?php
// PHP: Handle AJAX requests in evo-bridge.php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $input = json_decode(file_get_contents('php://input'), true);
    
    if ($input['action'] === 'updateUser') {
        $userData = $input['data'];
        // Process the data
        echo json_encode(['status' => 'success', 'message' => 'User updated']);
    }
}
?>
```

## 🎨 Built-in Framework Support

### React Components
```evo
<!DOCTYPE html>
<html>
<head>
    <title>EVO React App</title>
    <!-- React CDN is auto-included -->
</head>
<body>
    <div id="root"></div>
    
    <script type="text/babel">
        // React component
        function UserCard({ user }) {
            return (
                <div className="bg-white p-4 rounded-lg shadow-md">
                    <h3 className="text-xl font-bold">{user.name}</h3>
                    <p className="text-gray-600">{user.email}</p>
                    <button 
                        className="bg-blue-500 text-white px-4 py-2 rounded mt-2"
                        onClick={() => alert(`Hello ${user.name}!`)}
                    >
                        Click Me
                    </button>
                </div>
            );
        }
        
        // Main App component
        function App() {
            const [users, setUsers] = React.useState([]);
            
            React.useEffect(() => {
                // Load users from PHP
                const phpUsers = <?php 
                    $users = [
                        ['name' => 'John Doe', 'email' => 'john@example.com'],
                        ['name' => 'Jane Smith', 'email' => 'jane@example.com']
                    ];
                    echo json_encode($users);
                ?>;
                setUsers(phpUsers);
            }, []);
            
            return (
                <div className="container mx-auto p-4">
                    <h1 className="text-3xl font-bold mb-4">Users</h1>
                    <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                        {users.map((user, index) => (
                            <UserCard key={index} user={user} />
                        ))}
                    </div>
                </div>
            );
        }
        
        ReactDOM.render(<App />, document.getElementById('root'));
    </script>
</body>
</html>
```

### Tailwind CSS Classes
```evo
<div class="min-h-screen bg-gradient-to-br from-blue-500 to-purple-600">
    <div class="container mx-auto px-4 py-8">
        <div class="bg-white rounded-lg shadow-xl p-6 max-w-md mx-auto">
            <h1 class="text-3xl font-bold text-gray-800 mb-4">Welcome to EVO</h1>
            <p class="text-gray-600 mb-6">Built-in Tailwind CSS support!</p>
            <button class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded transition duration-200">
                Get Started
            </button>
        </div>
    </div>
</div>
```

### Node.js Polyfills
```evo
<script>
// Node.js modules available in browser
const fs = require('fs');
const path = require('path');
const http = require('http');

// Example usage
console.log('Node.js modules loaded!');

// Mock file operations
function readConfig() {
    // This would work in a Node.js environment
    // In browser, it's mocked by EVO
    return {
        apiUrl: 'https://api.example.com',
        version: '1.0.0'
    };
}
</script>
```

## 🛠️ Custom EVO Syntax

### Variable Declaration
```evo
<!-- EVO Custom Syntax -->
evo:var $message = "Hello EVO World!";
evo:var $userCount = 42;
evo:var $isLoggedIn = true;

<!-- Equivalent PHP -->
<?php
$message = "Hello EVO World!";
$userCount = 42;
$isLoggedIn = true;
?>
```

### Function Definition
```evo
<!-- EVO Custom Syntax -->
evo:func greetUser($name, $age = 25) {
    evo:out "<h2>Hello " . $name . "!</h2>";
    evo:out "<p>You are " . $age . " years old.</p>";
}

<!-- Usage -->
evo:call greetUser("John", 30);
evo:call greetUser("Jane"); // Uses default age

<!-- Equivalent PHP -->
<?php
function greetUser($name, $age = 25) {
    echo "<h2>Hello " . $name . "!</h2>";
    echo "<p>You are " . $age . " years old.</p>";
}

greetUser("John", 30);
greetUser("Jane");
?>
```

### Class Definition
```evo
<!-- EVO Custom Syntax -->
evo:class User {
    evo:var $name;
    evo:var $email;
    
    evo:func __construct($name, $email) {
        evo:var $this->name = $name;
        evo:var $this->email = $email;
    }
    
    evo:func getInfo() {
        evo:return $this->name . " (" . $this->email . ")";
    }
}

<!-- Usage -->
evo:var $user = new User("John Doe", "john@example.com");
evo:out $user->getInfo();
```

### Control Structures
```evo
<!-- EVO Custom Syntax -->
evo:if ($userCount > 0) {
    evo:out "<p>There are " . $userCount . " users online.</p>";
} evo:else {
    evo:out "<p>No users online.</p>";
}

<!-- Loops -->
evo:for ($i = 0; $i < 5; $i++) {
    evo:out "<div>Item " . ($i + 1) . "</div>";
}

<!-- While Loop -->
evo:var $counter = 0;
evo:while ($counter < 3) {
    evo:out "<p>Count: " . $counter . "</p>";
    evo:var $counter++;
}
```

### Framework Shortcuts
```evo
<!-- React Component Shortcut -->
evo:react MyComponent {
    evo:return (
        <div className="p-4">
            <h1>My Component</h1>
        </div>
    );
}

<!-- Tailwind Class Shortcut -->
evo:tailwind bg-blue-500 text-white p-4 rounded-lg

<!-- Node.js Module Shortcut -->
evo:node require('fs').readFileSync('config.json')
```

## ✅ Best Practices

### 1. **File Organization**
```evo
<!DOCTYPE html>
<html>
<head>
    <!-- Meta tags first -->
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
    
    <!-- CSS styles -->
    <style>
        .custom-style { color: blue; }
    </style>
</head>
<body>
    <!-- HTML structure -->
    <div id="app"></div>
    
    <!-- PHP server-side logic -->
    <?php
    // Server-side processing
    $data = processData();
    ?>
    
    <!-- JavaScript client-side logic -->
    <script>
        // Client-side processing
        const data = <?php echo json_encode($data); ?>;
        processClientSide(data);
    </script>
</body>
</html>
```

### 2. **Data Security**
```evo
<?php
// Always sanitize user input
$userInput = filter_input(INPUT_POST, 'user_input', FILTER_SANITIZE_STRING);
$email = filter_input(INPUT_POST, 'email', FILTER_VALIDATE_EMAIL);

// Use prepared statements for database queries
$stmt = $pdo->prepare("SELECT * FROM users WHERE email = ?");
$stmt->execute([$email]);
?>
```

### 3. **Error Handling**
```evo
<?php
try {
    // Risky operation
    $result = riskyOperation();
    echo json_encode(['success' => true, 'data' => $result]);
} catch (Exception $e) {
    error_log("Error: " . $e->getMessage());
    echo json_encode(['success' => false, 'error' => 'Operation failed']);
}
?>

<script>
// JavaScript error handling
fetch('evo-bridge.php')
    .then(response => response.json())
    .then(data => {
        if (data.success) {
            console.log('Success:', data.data);
        } else {
            console.error('Error:', data.error);
        }
    })
    .catch(error => {
        console.error('Network error:', error);
    });
</script>
```

## 🔄 Common Patterns

### 1. **Form Handling**
```evo
<!DOCTYPE html>
<html>
<body>
    <form id="userForm">
        <input type="text" id="name" placeholder="Name" required>
        <input type="email" id="email" placeholder="Email" required>
        <button type="submit">Submit</button>
    </form>
    
    <div id="result"></div>
    
    <script>
        document.getElementById('userForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = {
                name: document.getElementById('name').value,
                email: document.getElementById('email').value
            };
            
            fetch('evo-bridge.php', {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify(formData)
            })
            .then(response => response.json())
            .then(data => {
                document.getElementById('result').innerHTML = 
                    `<p class="text-green-500">${data.message}</p>`;
            });
        });
    </script>
</body>
</html>
```

### 2. **Dynamic Content Loading**
```evo
<!DOCTYPE html>
<html>
<body>
    <div id="content"></div>
    <button onclick="loadContent()">Load Content</button>
    
    <script>
        function loadContent() {
            fetch('evo-bridge.php?action=getContent')
                .then(response => response.json())
                .then(data => {
                    document.getElementById('content').innerHTML = data.html;
                });
        }
    </script>
</body>
</html>
```

### 3. **Real-time Updates**
```evo
<!DOCTYPE html>
<html>
<body>
    <div id="liveData"></div>
    
    <script>
        function updateLiveData() {
            fetch('evo-bridge.php?action=getLiveData')
                .then(response => response.json())
                .then(data => {
                    document.getElementById('liveData').innerHTML = 
                        `<p>Last updated: ${data.timestamp}</p>
                         <p>Users online: ${data.userCount}</p>`;
                });
        }
        
        // Update every 5 seconds
        setInterval(updateLiveData, 5000);
        updateLiveData(); // Initial load
    </script>
</body>
</html>
```

## 🚨 Error Handling

### PHP Error Handling
```evo
<?php
// Enable error reporting in development
error_reporting(E_ALL);
ini_set('display_errors', 1);

// Custom error handler
set_error_handler(function($severity, $message, $file, $line) {
    throw new ErrorException($message, 0, $severity, $file, $line);
});

try {
    // Your code here
    $result = processData();
} catch (Exception $e) {
    // Log error
    error_log("EVO Error: " . $e->getMessage());
    
    // Return error response
    http_response_code(500);
    echo json_encode(['error' => 'Internal server error']);
}
?>
```

### JavaScript Error Handling
```evo
<script>
// Global error handler
window.addEventListener('error', function(e) {
    console.error('EVO JavaScript Error:', e.error);
    
    // Send error to server
    fetch('evo-bridge.php', {
        method: 'POST',
        headers: {'Content-Type': 'application/json'},
        body: JSON.stringify({
            action: 'logError',
            error: e.error.toString(),
            file: e.filename,
            line: e.lineno
        })
    });
});

// Promise error handling
fetch('evo-bridge.php')
    .then(response => {
        if (!response.ok) {
            throw new Error(`HTTP ${response.status}`);
        }
        return response.json();
    })
    .catch(error => {
        console.error('Fetch error:', error);
        // Handle error gracefully
    });
</script>
```

## 📝 Examples & Templates

### Template 1: Basic CRUD Application
```evo
<!DOCTYPE html>
<html>
<head>
    <title>EVO CRUD App</title>
</head>
<body>
    <div id="app">
        <h1>User Management</h1>
        
        <!-- Add User Form -->
        <form id="addUserForm">
            <input type="text" id="name" placeholder="Name" required>
            <input type="email" id="email" placeholder="Email" required>
            <button type="submit">Add User</button>
        </form>
        
        <!-- Users List -->
        <div id="usersList"></div>
    </div>
    
    <script>
        // Load users on page load
        loadUsers();
        
        // Add user form handler
        document.getElementById('addUserForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const userData = {
                name: document.getElementById('name').value,
                email: document.getElementById('email').value
            };
            
            fetch('evo-bridge.php', {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify({action: 'addUser', data: userData})
            })
            .then(response => response.json())
            .then(data => {
                if (data.success) {
                    loadUsers(); // Reload users
                    document.getElementById('addUserForm').reset();
                }
            });
        });
        
        function loadUsers() {
            fetch('evo-bridge.php?action=getUsers')
                .then(response => response.json())
                .then(data => {
                    const usersList = document.getElementById('usersList');
                    usersList.innerHTML = data.users.map(user => `
                        <div class="user-item">
                            <h3>${user.name}</h3>
                            <p>${user.email}</p>
                            <button onclick="deleteUser(${user.id})">Delete</button>
                        </div>
                    `).join('');
                });
        }
        
        function deleteUser(id) {
            fetch('evo-bridge.php', {
                method: 'POST',
                headers: {'Content-Type': 'application/json'},
                body: JSON.stringify({action: 'deleteUser', id: id})
            })
            .then(response => response.json())
            .then(data => {
                if (data.success) {
                    loadUsers();
                }
            });
        }
    </script>
</body>
</html>
```

### Template 2: Dashboard with Charts
```evo
<!DOCTYPE html>
<html>
<head>
    <title>EVO Dashboard</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
    <div class="dashboard">
        <h1>Analytics Dashboard</h1>
        
        <div class="stats-grid">
            <div class="stat-card">
                <h3>Total Users</h3>
                <p id="totalUsers">Loading...</p>
            </div>
            <div class="stat-card">
                <h3>Active Sessions</h3>
                <p id="activeSessions">Loading...</p>
            </div>
        </div>
        
        <div class="chart-container">
            <canvas id="userChart"></canvas>
        </div>
    </div>
    
    <script>
        // Load dashboard data
        loadDashboardData();
        
        function loadDashboardData() {
            fetch('evo-bridge.php?action=getDashboardData')
                .then(response => response.json())
                .then(data => {
                    // Update stats
                    document.getElementById('totalUsers').textContent = data.totalUsers;
                    document.getElementById('activeSessions').textContent = data.activeSessions;
                    
                    // Update chart
                    updateChart(data.chartData);
                });
        }
        
        function updateChart(chartData) {
            const ctx = document.getElementById('userChart').getContext('2d');
            new Chart(ctx, {
                type: 'line',
                data: {
                    labels: chartData.labels,
                    datasets: [{
                        label: 'Users',
                        data: chartData.values,
                        borderColor: 'rgb(75, 192, 192)',
                        tension: 0.1
                    }]
                },
                options: {
                    responsive: true,
                    scales: {
                        y: {
                            beginAtZero: true
                        }
                    }
                }
            });
        }
    </script>
</body>
</html>
```

## 🎯 Key Takeaways for AI Assistants

1. **Always use `.evo` extension** for EVO files
2. **Mix HTML, PHP, and JavaScript** naturally in one file
3. **Use `evo:` syntax** for custom EVO language features
4. **Leverage built-in frameworks** (React, Tailwind, Node.js)
5. **Implement proper error handling** for both PHP and JavaScript
6. **Follow security best practices** for data handling
7. **Use the PHP-JavaScript bridge** for seamless data exchange
8. **Structure files logically** with clear separation of concerns

This guide should help any AI assistant understand and code .evo files effectively!
