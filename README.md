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

**Navigate to the package folder**:

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

    ```bash
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

### 4. src/config/hello.php:

Make a directory for configuration (config/hello.php)
This is the configuration file for the package. You can modify this file to add package-specific settings that can be customized by the application

```bash
    <?php

        return [
            'message' => 'Hello from the package config!',
        ];
```

### 5. Vendor Publishing

If you want your users to be able to publish configuration files, views, or other resources, you can use the publishes method in your service provider.

In this example, the hello.php configuration file is published to the Laravel application's config directory. The user can run the following command to publish the configuration file:

```bash
    php artisan vendor:publish --provider="YourName\Hello\HelloServiceProvider" --tag="config"
```

This will copy the hello.php configuration file to config/hello.php in the main Laravel application.

If you want to publish views, resources, or other files, you can add them to the publishes method in your service provider:

```bash
$this->publishes([
    __DIR__.'/resources/views' => resource_path('views/vendor/hello'),
], 'views');
```

Then, users can publish the views with the following command:

```bash
php artisan vendor:publish --provider="YourName\Hello\HelloServiceProvider" --tag="views"
```

**src/resources/views/hello.blade.php**
You can add a view to be rendered from your package. For example, here is a simple view that renders a hello message.

```bash
    <!DOCTYPE html>
    <html>
        <head>
            <title>Hello Package</title>
        </head>
        <body>
            <h1>{{ config('hello.message') }}</h1>
        </body>
    </html>
```
**src/resources/views/hello.blade.php**
````bash
Route::get('/hello-view', function () {
    return view('vendor.hello.hello');
});
````

**Testing the Package**
Once you have installed and published the configuration and views, you can test your package by visiting the route defined in src/routes/web.php. Simply go to:
This will render the view located in resources/views/vendor/hello/hello.blade.php

##### 📁 Hare Package Structure Example
```bash
laravel-hello-app/
└── packages/
        └── YourName/
                └── Hello/
                    ├── composer.json
                    └── src
                        └── config
                            └── hello.php:
                    ├── HelloServiceProvider.php
                    └── routes/
                        └── web.php
                    └── resources
                        └── views
                            └── hello.blade.php
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
