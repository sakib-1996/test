# Hello Laravel Package

A simple Laravel package that returns a "Hello" response. Built for educational and testing purposes.

## 📦 Features

- Returns a test "Hello" route
- Supports Laravel 9.x, 10.x, and 11.x
- Supports vendor publishing
- PSR-4 autoloading
- Clean package structure for local development

---

## 🚀 Installation & Development Guide

### 1. Create a New Laravel Application

```bash
composer create-project laravel/laravel laravel-hello-app
cd laravel-hello-app

2. Create Your Package Directory
bash
Copy
Edit
mkdir -p packages/YourName/Hello/src/routes
cd packages/YourName/Hello
touch composer.json
touch src/HelloServiceProvider.php
touch src/routes/web.php
Replace YourName with your GitHub or vendor name and Hello with your package name (should match your GitHub repository name if publishing).

📁 Package Structure
css
Copy
Edit
laravel-hello-app/
└── packages/
    └── YourName/
        └── Hello/
            ├── composer.json
            └── src/
                ├── HelloServiceProvider.php
                └── routes/
                    └── web.php
🛠️ Package composer.json Example
json
Copy
Edit
{
  "name": "yourname/hello",
  "description": "Just a test package that returns hello",
  "type": "library",
  "autoload": {
    "psr-4": {
      "YourName\\Hello\\": "src/"
    }
  },
  "extra": {
    "laravel": {
      "providers": [
        "YourName\\Hello\\HelloServiceProvider"
      ]
    }
  },
  "require": {
    "php": "^8.0",
    "illuminate/support": "^9.0|^10.0|^11.0"
  }
}
🧩 Add Package to Laravel Application
Update the root composer.json in your Laravel app:

json
Copy
Edit
"repositories": [
  {
    "type": "path",
    "url": "packages/YourName/Hello"
  }
]
Then install the package via Composer:

bash
Copy
Edit
composer require yourname/hello:@dev
🧪 Example: HelloServiceProvider.php
php
Copy
Edit
<?php

namespace YourName\Hello;

use Illuminate\Support\ServiceProvider;
use Illuminate\Support\Facades\Route;

class HelloServiceProvider extends ServiceProvider
{
    public function boot()
    {
        $this->loadRoutesFrom(__DIR__.'/routes/web.php');

        // Publishable config or views
        $this->publishes([
            __DIR__.'/config/hello.php' => config_path('hello.php'),
        ], 'hello-config');
    }

    public function register()
    {
        //
    }
}
🌐 Example: web.php
php
Copy
Edit
<?php

use Illuminate\Support\Facades\Route;

Route::get('/hello', function () {
    return 'Hello from the package!';
});
🛠️ Optional: Add a Config File
If you want to support config publishing, add a config file:

Create: src/config/hello.php

php
Copy
Edit
<?php

return [
    'message' => 'Hello from config!'
];
Then update HelloServiceProvider.php to register the config.

📤 Publishing Config (or Assets)
To publish the config file from the package:

bash
Copy
Edit
php artisan vendor:publish --tag=hello-config
✅ Test the Route
After installation and running your Laravel app, visit:

bash
Copy
Edit
http://localhost:8000/hello
You should see:

csharp
Copy
Edit
Hello from the package!
🧹 Cleanup & Refresh
If you make changes in your package during development:

bash
Copy
Edit
composer dump-autoload
