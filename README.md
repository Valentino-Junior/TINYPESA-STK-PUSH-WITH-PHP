# TINYPESA-STK-PUSH-WITH-PHP

This is a sample implementation of the Mpesa STK Push API using PHP.

## Requirements

1. TinyPesa STK Push API requires PHP 7.0 and above.

2. You tinypesa API key.

Create an account at [tinypesa.com](https://tinypesa.com) to get your API key.

Create a file called `stk.php` and paste the code below.

```php
$amount = '1'; //Amount to transact
$phonenuber = '07XXXXXXXX'; // Phone number paying start with 07
$Account_no = 'UMESKIA SOFTWARES'; // Enter account number optional
$url = 'https://tinypesa.com/api/v1/express/initialize';
$data = array(
    'amount' => $amount,
    'msisdn' => $phonenuber,
    'account_no' => $Account_no
);
$headers = array(
    'Content-Type: application/x-www-form-urlencoded',
    'ApiKey: xxxxxxxxx' // Replace with your api key
);
$info = http_build_query($data);
$curl = curl_init();
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_POSTFIELDS, $info);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($curl, CURLOPT_HTTPHEADER, $headers);
$resp = curl_exec($curl);
if ($resp === false) {
    echo "CURL ERROR: " . curl_error($curl);
}
$msg_resp = json_decode($resp);

if ($msg_resp->success == 'true') {
    echo "WAIT FOR NEVEREST STK POP UP";
}
```

Surpport this project by giving it a star.

You can also support this project by donating to the following Mpesa Till Number: 5926541
