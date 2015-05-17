PHPush
======

This is a PHP package to send push notifications to foreign platforms by single API. It's developed by [Hility](http://hility.com).

Currently, we support only 2 platforms - Android and iOS.

Example
-----------

The following examples demonstrate how to send Push notifications with text "Hello, World!" to 2 devices that have different platforms.

```php
// Include PHPush
require_once 'vendor/autoload.php';

// Setting environment
\PHPush\PHPush::Environment(\PHPush\PHPush::ENVIRONMENT_PRODUCTION);

// Adding Android key
\PHPush\PHPush::Provider(\PHPush\Provider::PROVIDER_ANDROID)->setAccessKey('test');

// Adding path to iOS certificate
\PHPush\PHPush::Provider(\PHPush\Provider::PROVIDER_IOS)->setCertificate('ck.pem');

// Creating new queue
$queue = \PHPush\PHPush::Queue();

// Adding Android devices
$queue->add(new \PHPush\providers\android\Device('android_registration_id'));

// Adding iOS devices
$queue->add(new \PHPush\providers\ios\Device('ios_device_token'));

// Setting message
$queue->message('Hello, World!');

// Send message
$queue->send();
```
