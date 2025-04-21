# Hello Laravel Package

A simple Laravel package that returns a "Hello" response. Built for educational and testing purposes.

## 📦 Features

-   Setup steps
-   Package structure
-   composer.json configuration (jsut in tuch)
-   Installation via local path repository
-   Service provider
-   Vendor publish support
-   Example usage

---

## 🚀 Installation & Development Guide

### 1. Create a New Laravel Application

```bash
composer create-project laravel/laravel laravel-hello-app
cd laravel-hello-app
```

### 2. Create Your Package Directory

Use the following commands to set up your package directory structure.  
Replace `YourName` with your GitHub username or vendor name, and `Hello` with your actual package name.  
Make sure the package name matches your GitHub repository name if you plan to publish it.

**Create the directory structure**:

```bash
mkdir -p packages/YourName/Hello/src/routes
```

# Navigate to the package folder

```bash
cd packages/YourName/Hello
```

**Create composer.json files (this will be root directory in the package)** `composer.json`:

```bash
touch composer.json
```

**Create your NECESSARY file folder in the (src/) directory** `packages/YourName/Hello/src`:

```bash
touch src/HelloServiceProvider.php
touch src/routes/web.php
```

#### 📌 Note: Ensure the YourName/Hello structure aligns with your Composer and PSR-4 autoloading configuration.

### 3. Add the package repository to your Laravel application's `composer.json`:

    ```json
    "repositories": [
      {
        "type": "path",
        "url": "packages/{YourName}/Packagename"
      }
    ]
    ```

**Require the package** using Composer:

    ```bash
    composer require yourname/hello:@dev
    ```

    This will install the package locally in your Laravel application.

##### 📁 Hare Package Structure Example

```bash
laravel-hello-app/
└── packages/
        └── YourName/
                └── Hello/
                    ├── composer.json
                    └── src/
                    ├── HelloServiceProvider.php
                    └── routes/
                        └── web.php
```

##### 🛠️ Package composer.json Example

```bash
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
    "php": "^8.0", # hare you can use your php version
    "illuminate/support": "^9.0|^10.0|^11.0"  # laravel version
  }
}
```
