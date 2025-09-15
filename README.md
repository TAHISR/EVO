
# 🚀 EVO Programming Language

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](https://github.com/evo-lang/evo-programming-language)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![PHP](https://img.shields.io/badge/PHP-7.4+-777BB4.svg)](https://php.net)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E.svg)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Node.js](https://img.shields.io/badge/Node.js-14+-339933.svg)](https://nodejs.org)

> **The Ultimate Bridge Between PHP and JavaScript** - Write PHP in PHP style, JavaScript in JavaScript style, and they work together seamlessly!

## 🌟 What is EVO?

EVO is a revolutionary programming language that creates a **seamless bridge between PHP and JavaScript**. Unlike traditional approaches, EVO allows you to:

- Write **PHP code in natural PHP style**
- Write **JavaScript code in natural JavaScript style** 
- Have them **communicate perfectly** without complex APIs
- Use **built-in frameworks** (React, Tailwind CSS, Node.js)
- Run **globally like Python** with simple commands

## ✨ Key Features

### 🔗 **Seamless PHP-JavaScript Bridge**
```evo
<?php
$userData = ['name' => 'John', 'age' => 25];
$jsonData = json_encode($userData);
?>

<script>
// JavaScript automatically receives PHP data
const userData = <?php echo $jsonData; ?>;
console.log(userData.name); // "John"

// Send data back to PHP seamlessly
fetch('evo-bridge.php', {
    method: 'POST',
    body: JSON.stringify({action: 'updateUser', data: userData})
});
</script>
```

### 🎨 **Built-in Framework Support**
```evo
<!DOCTYPE html>
<html>
<head>
    <title>My EVO App</title>
    <!-- React, Tailwind CSS, and Node.js are automatically included! -->
</head>
<body>
    <div id="app" class="bg-blue-500 text-white p-4">
        <h1 class="text-2xl font-bold">Hello EVO World!</h1>
    </div>

    <script type="text/babel">
        // React components work out of the box!
        function App() {
            return (
                <div className="container mx-auto p-4">
                    <h1 className="text-3xl font-bold text-blue-600">
                        Welcome to EVO!
                    </h1>
                </div>
            );
        }
        
        ReactDOM.render(<App />, document.getElementById('app'));
    </script>
</body>
</html>
```

### 🛠️ **Custom EVO Syntax**
```evo
<!DOCTYPE html>
<html>
<body>
    <!-- EVO Custom Syntax -->
    evo:var $message = "Hello EVO World!";
    evo:func showMessage($text) {
        evo:out "<h1>" . $text . "</h1>";
    }
    
    evo:call showMessage($message);
    
    <!-- Built-in framework shortcuts -->
    evo:react MyComponent
    evo:tailwind bg-blue-500 text-white p-4
    evo:node require('fs').readFileSync('data.txt')
</body>
</html>
```

## 🚀 Quick Start

### 1. **Install EVO Globally**
```bash
# Download EVO-Programming-Language.zip
# Extract and run as administrator:
evo-installer-script.bat

# Restart your terminal, then:
evo version
```

### 2. **Create Your First EVO App**
```bash
# Initialize a new project
evo init my-first-evo-app
cd my-first-evo-app

# Run your app
evo run hello-world.evo
```

### 3. **Development Mode**
```bash
# Start development server with hot reload
evo dev hello-world.evo

# Or start a general development server
evo serve 8000
```

## 📁 Project Structure

```
my-evo-project/
├── evo_handler.php          # EVO language processor
├── evo-bridge.php           # PHP-JavaScript bridge
├── evo-js-handler.js        # JavaScript handler
├── evo-dev-server.js        # Development server
├── .htaccess                # Apache configuration
├── package.json             # Node.js dependencies
├── hello-world.evo          # Your EVO application
└── evo-language-extension/  # Cursor/VSCode extension
```

## 🎯 EVO Commands

| Command | Description | Example |
|---------|-------------|---------|
| `evo version` | Show EVO version | `evo version` |
| `evo run <file>` | Run an EVO file | `evo run app.evo` |
| `evo dev <file>` | Development mode | `evo dev app.evo` |
| `evo serve [port]` | Start dev server | `evo serve 8000` |
| `evo init <project>` | Create new project | `evo init my-app` |
| `evo help` | Show help | `evo help` |

## 🔧 Built-in Frameworks

### **React Support**
```evo
<script type="text/babel">
    function Counter() {
        const [count, setCount] = React.useState(0);
        
        return (
            <div className="p-4">
                <h2>Count: {count}</h2>
                <button 
                    className="bg-blue-500 text-white px-4 py-2 rounded"
                    onClick={() => setCount(count + 1)}
                >
                    Increment
                </button>
            </div>
        );
    }
    
    ReactDOM.render(<Counter />, document.getElementById('root'));
</script>
```

### **Tailwind CSS Support**
```evo
<div class="bg-gradient-to-r from-blue-500 to-purple-600 text-white p-8 rounded-lg shadow-lg">
    <h1 class="text-4xl font-bold mb-4">Welcome to EVO</h1>
    <p class="text-lg opacity-90">Built-in Tailwind CSS support!</p>
</div>
```

### **Node.js Polyfills**
```evo
<script>
    // Node.js modules work in the browser!
    const fs = require('fs');
    const path = require('path');
    const http = require('http');
    
    // Use Node.js APIs seamlessly
    console.log('Node.js modules available!');
</script>
```

## 🎨 IDE Support

### **Cursor/VSCode Extension**
- ✅ **Syntax highlighting** for EVO files
- ✅ **IntelliSense** and autocomplete
- ✅ **Code snippets** for common patterns
- ✅ **Custom file icons** with your logo
- ✅ **Error detection** and diagnostics

**Install the extension:**
```bash
# Extension is automatically installed with EVO
# Or install manually:
cursor --install-extension evo-language-extension/evo-language-support.vsix
```

## 📚 Examples

### **Basic PHP-JavaScript Bridge**
```evo
<!DOCTYPE html>
<html>
<body>
    <?php
    $serverTime = date('Y-m-d H:i:s');
    $userAgent = $_SERVER['HTTP_USER_AGENT'];
    ?>
    
    <h1>Server Information</h1>
    <p>Server Time: <?php echo $serverTime; ?></p>
    
    <script>
        // JavaScript receives PHP data
        const serverTime = "<?php echo $serverTime; ?>";
        const userAgent = "<?php echo $userAgent; ?>";
        
        // Display client-side information
        document.body.innerHTML += `
            <p>Client Time: ${new Date().toLocaleString()}</p>
            <p>User Agent: ${navigator.userAgent}</p>
        `;
        
        // Send data back to PHP
        fetch('evo-bridge.php', {
            method: 'POST',
            headers: {'Content-Type': 'application/json'},
            body: JSON.stringify({
                action: 'logVisit',
                data: {timestamp: new Date().toISOString()}
            })
        });
    </script>
</body>
</html>
```

### **React Component with PHP Backend**
```evo
<!DOCTYPE html>
<html>
<head>
    <title>EVO React App</title>
</head>
<body>
    <div id="root"></div>
    
    <?php
    // PHP backend logic
    $apiData = [
        'users' => [
            ['id' => 1, 'name' => 'John Doe', 'email' => 'john@example.com'],
            ['id' => 2, 'name' => 'Jane Smith', 'email' => 'jane@example.com']
        ]
    ];
    ?>
    
    <script type="text/babel">
        function UserList() {
            const [users, setUsers] = React.useState(<?php echo json_encode($apiData['users']); ?>);
            
            return (
                <div className="max-w-md mx-auto bg-white rounded-xl shadow-md p-6">
                    <h2 className="text-2xl font-bold mb-4">Users</h2>
                    {users.map(user => (
                        <div key={user.id} className="border-b pb-2 mb-2">
                            <h3 className="font-semibold">{user.name}</h3>
                            <p className="text-gray-600">{user.email}</p>
                        </div>
                    ))}
                </div>
            );
        }
        
        ReactDOM.render(<UserList />, document.getElementById('root'));
    </script>
</body>
</html>
```

## 🛠️ Installation

### **System Requirements**
- **PHP 7.4+** (for server-side processing)
- **Node.js 14+** (for development server)
- **Apache/Nginx** (for production)
- **Windows/Linux/macOS** (cross-platform)

### **Global Installation**
1. **Download** `EVO-Programming-Language.zip`
2. **Extract** the archive
3. **Run** `evo-installer-script.bat` as administrator
4. **Restart** your terminal
5. **Test** with `evo version`

### **Manual Installation**
```bash
# Clone the repository
git clone https://github.com/evo-lang/evo-programming-language.git
cd evo-programming-language

# Install dependencies
npm install

# Set up web server
# Copy evo_handler.php and .htaccess to your web root
# Configure your web server to process .evo files
```

## 🔧 Configuration

### **Apache Configuration**
```apache
# .htaccess
RewriteEngine On
RewriteRule ^(.*)\.evo$ evo_handler.php [L,QSA]
AddType application/x-httpd-php .evo
```

### **Nginx Configuration**
```nginx
location ~ \.evo$ {
    try_files $uri =404;
    fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
    fastcgi_index evo_handler.php;
    fastcgi_param SCRIPT_FILENAME $document_root/evo_handler.php;
    include fastcgi_params;
}
```

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### **Development Setup**
```bash
# Clone your fork
git clone https://github.com/your-username/evo-programming-language.git
cd evo-programming-language

# Install dependencies
npm install

# Run development server
evo dev

# Test your changes
evo run test-extension.evo
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **PHP Community** - For the amazing server-side language
- **JavaScript Community** - For the versatile client-side language
- **React Team** - For the incredible UI library
- **Tailwind CSS Team** - For the utility-first CSS framework
- **Node.js Team** - For the JavaScript runtime

## 📞 Support



**Made with ❤️ by TAHISR And For The EVO And Developers Community **

## 📰 Are You A Vibe Coder
- Dont Worry Because We Made A Package That You give Cursor And Other Ai's it will help them know what coding languge you are using its called AI-EVO-CODING-GUIDE.md you could download it easily from the source codes


## 🎢 Want To Know How You Could Learn ?

- soon we would post you give full guides how to code this coding languge so stay tuned
