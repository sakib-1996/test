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

## 2. Create Your Package Directory

Use the following commands to set up your package directory structure.  
Replace `YourName` with your GitHub username or vendor name, and `Hello` with your actual package name.  
Make sure the package name matches your GitHub repository name if you plan to publish it.

```bash
# Create the directory structure
mkdir -p packages/YourName/Hello/src/routes
```
```bash
# Navigate to the package folder
cd packages/YourName/Hello
```
```bash
# Create essential files
touch composer.json
touch src/HelloServiceProvider.php
touch src/routes/web.php
```
#### 📌 Note: Ensure the YourName/Hello structure aligns with your Composer and PSR-4 autoloading configuration.
