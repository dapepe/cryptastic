cryptastic
==========

THIS IS A MODIFIED VERSION OF THE cryptastic CLASS by Andrew Johnson

The original code can be found at the following URL

http://www.itnewb.com/v/PHP-Encryption-Decryption-Using-the-MCrypt-Library-libmcrypt


Example
-------

```php
$pass = 'the password';
$salt = 'the password salt';
$msg  = 'This is the secret message.';

/**********************************************************************************************************************/

// EXAMPLE #1 USING STRING AS MESSAGE

$cryptastic = new cryptastic;

$key = $cryptastic->pbkdf2($pass, $salt, 1000, 32) or
	die("Failed to generate secret key.");

$encrypted = $cryptastic->encrypt($msg, $key) or
	die("Failed to complete encryption.");

$decrypted = $cryptastic->decrypt($encrypted, $key) or
	die("Failed to complete decryption");

echo $decrypted . "<br /><br />\n";

/**********************************************************************************************************************/

// EXAMPLE #2 USING ARRAY AS MESSAGE

$msg        = array('message' => $msg);
$encrypted  = $cryptastic->encrypt($msg, $key);
$decrypted  = $cryptastic->decrypt($encrypted, $key);

echo $decrypted['message'];
```
