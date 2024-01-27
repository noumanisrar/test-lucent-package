<div align="center">
  
![Lucent](lucent-dark.png)

</div>

# Lucent-Package

## Introduction

The `lucent-package` is an essential component that connects your applications with the Lucent Web App for seamless error logging. It is crafted to be integrated into the very applications you wish to monitor for errors. 

**Important:** Before incorporating the `lucent-package` into your app, ensure that you have the Lucent Web App configured and ready to go. If you haven't set up the Lucent Project yet, please follow the link below to get started.

## Getting Started with Lucent

To establish a robust error tracking system, your first step is to set up the Lucent Project. Detailed instructions and necessary resources can be found at the following link:

[Set Up Lucent Project](https://github.com/manadinho/lucent)

Once the Lucent Project is in place, you can proceed to integrate the `lucent-package` into your application to begin error logging.


## Installation

Install Lucent Package
```bash
composer require manadinho/lucent
```
Publish Configurations
```bash
php artisan vendor:publish --provider="Manadinho\Lucent\LucentServiceProvider"
```

## Configuration
After creating a new project in your Lucent Project, you will obtain a `LUCENT_KEY`. Place this key along with the URL of your Lucent Project into the `.env` file of the Laravel project you wish to track. Your `.env` file should now include the following entries:
```bash
LUCENT_KEY=paste_your_copied_lucent_key_here
LUCENT_URL=https://example.com/lucent
```
Navigate to the `app/Exceptions/Handler.php` file in your Laravel project and import the Lucent Facade at the beginning of the file:
```bash
use Manadinho\Lucent\Facades\Lucent;
```
Then, within the register method of your Handler.php file, enhance the reportable method by adding a call to Lucent::register($e). This ensures that any thrown exceptions are captured and logged by the Lucent Web App. Here's the complete method for clarity:
```bash
public function register(): void
{
    $this->reportable(function (Throwable $e) {
        Lucent::register($e);
    });
}
```
## Config Options
We can manage the settings of the package from `config/lucent.php` file. These are the details.

```
show_translate_button [boolean]
```
You can also control if you want to show the translate button for the translation keys.

