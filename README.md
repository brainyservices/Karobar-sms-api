# Karobar SMS API

Karobar SMS API is build for Karobar SMS - Bulk SMS Application For Marketing


### Prerequisites

To run Karobar SMS API you have to install Karobar SMS Application on your server OR get KarobarSMS Reseller Account. 
For more details please visit: [Karobar SMS](https://www.karobarsms.com/)
```
php >=5.6
Karobar SMS - Bulk SMS Application For Markting
```

### Installing
Via Composer
```
composer require brainyservices/karobar-sms-api 
```

And Via Bash

```
git clone https://github.com/brainyservices/karobar-sms-api.git
```

## Usage


 ### Step 1:
If install Karobar SMS API using Git Clone then load your Karobar SMS API Class file and Use namespace. 
```php
require_once 'src/Class_Karobar_SMS_API.php';
use KarobarSMS\KarobarSMSAPI;
```
If install Karobar SMS API using Composer then Require/Include autoload.php file in the index.php of your project or whatever file you need to use **Karobar SMS API** classes:. 
```php
require 'vendor/autoload.php';
use KarobarSMS\KarobarSMSAPI;
```
### Step 2:
set your API_KEY from `https://my.karobarsms.com/api.php` (your application install url)
```php
$api_key = 'YWRtaW46YWRtaW4ucGFzc3dvcmQ=';
```
### Step 2.1:
set your Username 
```php
$username = 'user_name_here';
```
### Step 3:
Change the from number below. It can be a valid phone number or a String
```php
$from = '923001234567';
```

### Step 4:
the number we are sending to - Any phone number
```php
$destination = '923001234568';
```
You have to must include Country code at beginning of the phone number.  

### Step 5:
Replace your Install URL like `https://mywebhost.com/sms/api` with `https://ultimatesms.coderpixel.com/demo/`
`sms/api` is mandatory on your install url

```php
$url = 'https://my.karobarsms.com/api';
```
// SMS Body
```php
$sms = 'test message from Karobar SMS';
```
// Unicode SMS
```php
$unicode = '1'; //For Unicode message
```
// Voice SMS
```php
$voice = '1'; //For voice message
```
// MMS SMS
```php
$mms = '1'; //For mms message
$media_url = 'https://yourmediaurl.com'; //Insert your media url
```
// Schedule SMS
```php
$schedule_date = '09/17/2018 10:20 AM'; //Date like this format: m/d/Y h:i A
```
// Create Plain/text SMS Body for request
```php
$sms_body = array(
    'uname' => $username,
    'api_key' => $api_key,
    'to' => $destination,
    'mask' => $from,
    'text' => $sms
);
```
// Create Unicode SMS Body for request
```php
$sms_body = array(
    'uname' => $username,
    'api_key' => $api_key,
    'to' => $destination,
    'mask' => $from,
    'text' => $sms
    'unicode' => $unicode,
);
```

// Create Voice SMS Body for request
```php
$sms_body = array(
    'uname' => $username,
    'api_key' => $api_key,
    'to' => $destination,
    'mask' => $from,
    'text' => $sms
    'voice' => $voice,
);
```
// Create MMS SMS Body for request
```php
$sms_body = array(
    'uname' => $username,
    'api_key' => $api_key,
    'to' => $destination,
    'mask' => $from,
    'text' => $sms
    'mms' => $mms,
    'media_url' => $media_url,
);
```
// Create Schedule SMS Body for request
```php
$sms_body = array(
    'uname' => $username,
    'api_key' => $api_key,
    'to' => $destination,
    'mask' => $from,
    'text' => $sms
    'schedule' => $schedule_date,
);
```

### Step 6: 
Instantiate a new Karobar SMS API request
```php
$client = new KarobarSMSAPI();
```

## Send SMS
Finally send your sms through Karobar SMS API
```php
$response = $client->send_sms($sms_body, $url);
```

## Get Inbox
Get your all message
```php
$get_inbox=$client->get_inbox($api_key,$url);
```

## Get Balance
Get your account balance
```php
$get_balance=$client->check_balance($api_key,$url);
```
## Response
Karobar SMS API return response with `json` format, like:

```json
{"code":"ok","message":"Successfully Send"}
```

## Status Code

| Status | Message |
| --- | --- |
| `ok` | Successfully Send |
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

## Authors

* **Brainy Services** - *Initial work* - [brainyservices](https://github.com/brainyservices)
