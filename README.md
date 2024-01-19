# Swiftsms-GH PHP SDK

The Swiftsms-GH PHP SDK provides a suitable approach to the Swiftsms-GH API from applications written in PHP. It includes pre-defined set of classes and functions for API resource that initialize themselves from  API responses.

The library provides other features. For Example:
1. Easy configuration path for fast setup and use
2. Helpers for pagination.

You can sign up for an Swiftsms-GH account at [swiftsmsgh.com](https://swiftsmsgh.com)

## Prerequisites
PHP ^8.0 and later

## Installation
Via [Composer](http://getcomposer.org/)
```
$ composer require swiftsmsgh/swiftsmsgh-api-sdk
```

Via Git Bash
```
git clone https://github.com/majesty-scofield/swiftsmsgh-api-sdk.git
```

## Documentation
Please see [https://swiftsmsgh.com/developer](https://swiftsmsgh.com/developer) for up-to-date documentation

## Usage

### Step 1:
If you install the Swiftsms-GH PHP SDK via Git Clone then load the Swiftsms-GH PHP API class file and use namespace.

```php
require_once '/path/to/src/Swiftsmsgh.php';
use Swiftsms\Swiftsmsgh;
```

If you install Swiftsms-GH PHP SDK via [Composer](http://getcomposer.org/) require the autoload.php file in the index.php of your project or whatever file you need to use Swiftsms-GH PHP API classes.

```php
require __DIR__ . '/vendor/autoload.php';
use Swiftsms\Swiftsmsgh;
```

The Swiftsms-GH PHP SDK endpoints are RESTful, and consume and return JSON. All Http endpoints requires an API Key in the request header.

For more information on how to get an API Key visit [here](https://app.swiftsmsgh.com/developers) to copy or generate new key for authorization. 

## HTTP ENDPOINTS
* https://app.swiftsmsgh.com/api/v3/sms/send
* https://app.swiftsmsgh.com/api/v3/sms/{uid}
* https://app.swiftsmsgh.com/api/v3/sms
* https://app.swiftsmsgh.com/api/v3/me
* https://app.swiftsmsgh.com/api/v3/balance
* https://app.swiftsmsgh.com/api/v3/contacts
* https://app.swiftsmsgh.com/api/v3/contacts/{group_id}/show/
* https://app.swiftsmsgh.com/api/v3/contacts/{group_id}
* https://app.swiftsmsgh.com/api/v3/contacts/{group_id}/store
* https://app.swiftsmsgh.com/api/v3/contacts/{group_id}/search/{uid}
* https://app.swiftsmsgh.com/api/v3/contacts/{group_id}/update/{uid}
* https://app.swiftsmsgh.com/api/v3/contacts/{group_id}/delete/{uid}
* https://app.swiftsmsgh.com/api/v3/contacts/{group_id}/all


### Step 2:
Instantiate the SwiftsmsghSMSSDKAPI
```php
$api_token = "Enter Your API Token here";

$sender_id = "Enter your approved Sender ID here";

$client = new Swiftsmsgh\SwiftsmsghSMS($api_token, $sender_id);
```

## Send SMS
```php
$recipients = "233500000000,233540000000";

$message = "This is a test message";

$response = $client->send_sms($recipients, $message);
```


## Check SMS Credit Balance
```php
$url = "https://app.swiftsmsgh.com/api/v3/balance";

$get_credit_balance = $client->check_balance($url);
```


## View Profile
```php
$url = "https://app.swiftsmsgh.com/api/v3/me";

$get_profile = $client->profile($url);
```

## Status Code

| Status | Message |
| --- | --- |
| `ok`  | Successfully Send |
| `100` | Bad gateway requested |
| `101` | Wrong action |
| `102` | Authentication failed |
| `103` | Invalid phone number |
| `104` | Phone coverage not active |
| `105` | Insufficient balance |
| `106` | Invalid Sender ID |
| `107` | Invalid SMS Type |
| `108` | SMS Gateway not active |
| `109` | Invalid Schedule Time |
| `110` | Media url required |
| `111` | SMS contain spam word. Wait for approval |