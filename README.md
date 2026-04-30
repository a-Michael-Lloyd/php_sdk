[![N|Solid](https://tabscanner.com/wp-content/uploads/2024/09/tabscanner-logo-new-1.png.webp)](https://tabscanner.com)

# The world’s most advanced receipt OCR technology is Tabscanner. 

The perfect receipt OCR engine for developers, utilizing intelligent receipt optical character recognition. Technology designed from the ground up for reliable receipt recognition and data extraction.

Tabscanner is the world's first truly accurate receipt scanning technology. Founded in 2019 by Rashad Al-Safar and ben Smith, by 2019 it led at 96% accuracy and in 2026 is close to perfection. It utilises a highly crafted receipt OCR engine with AI to ensure robust and reliable data extraction at lightning speeds.
- Highly accurate data extraction
- Sub-second processing speeds
- Cross-platform API support
- Easily integrates with your software
- Flexible pricing plans
- Engineered for scaleability and efficiency 

## About this SDK
This is an official PHP development kit for Tabscanner API from 2019. For more information about Tabscanner API please visit https://tabscanner.com

### Installation

The recommended way to install Tabscanner PHP SDK is through [Composer](https://getcomposer.org/).

```sh
$ composer require tabscanner/phpsdk:1.0.2
```

### Basic Usage

Visit [Tabscanner Admin](https://dashboard.tabscanner.com) for your API key 

Note: The upload API can accept one of the following parameter:
- array - single HTTP File Upload variable ($_FILES) (for array of files see upload_multiple method)
- string - file path (used for fopen function)
- object - a Laravel request file object https://laravel.com/docs/5.6/requests#files

```php
use Tabscanner\Api;

$api = new Api('ApiKeyHere');

/**
 * Upload receipt to AI server to be processed
 *
 * @param $file array|string|object
 * array - single HTTP File Upload variable ($_FILES) (for array of files see upload_multiple method)
 * string - file path (used for fopen function)
 * object - a Laravel request file object (https://laravel.com/docs/5.6/requests#files)
 * 
 * @return array
 */
$file = 'receipt.jpg'; //direct grab from directory
$file2 = $_FILES['receipt']; //from upload form

$upload_response = $api->upload($file); //or $file2

//receipt token is generated from API after successful upload, else will receive error
$receipt_token = $upload_response['token'];

/**
 * Get result
 *
 * @param $token string
 * @return array - receipt data
 * - will receive status as pending or done
 * - one way to use this method is to create a loop until you get a "status done" response
 */
$result_response = $api->result($receipt_token);
```

### Upcoming Methods
```php
upload_multiple() //accepts multi-dimensional $_FILES
```

