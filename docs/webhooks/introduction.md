# Introduction

[Webhooks](https://es.wikipedia.org/wiki/Webhook) are callbacks that notify events in your account. A webhook will make an HTTP request to your application (usually by the `POST` method), whose body will contain an object describing the associated event. They are incredibly useful and a simple way to implement reactions to events.

For example: When a capture of an authorization is generated, a Webhook allows you to receive a notification so that you can take an action, such as sending a thank you email to the user.

Webhooks are also helpful in two situations:

- When a generated event is not a direct result of a call to the API. For example, a chargeback.
- When services or features need the response to a call, but they do not perform it directly. For example, an accounting service that needs to update accounting records when a transaction is generated.

These are some cases where Webhooks are used:

- When updating a customer's membership in your database when payment is successful.
- When recording an accounting entry after a transaction is made.

## Consume a Webhook

The first step to consume a Webhook is creating an endpoint to receive them. This is not different from creating any other page on your website. Simply create a new path with the desired URL.

Webhook data are sent in JSON format in the body of the POST call. All the event details are included and can be used directly (after parsing the JSON).

## Security

### Encryption

You may use an HTTP or an HTTPS URL for webhooks. In most cases, an HTTP is enough, but HTTPS may be useful if you're dealing with sensitive data or if you want to protect your system against replay attacks, for example.

### Authentication

In principle, anyone could send a request to your endpoint, so __it's important to check that these webhooks are originated by Kushki__. Therefore, to verify their authenticity, valid Webhooks will contain the following headings:

- `X-Kushki-Key`: Merchant ID.
- `X-Kushki-Signature:` It is the HMAC SHA256 signature of the body of the request, plus the timestamp, using your Webhook signature ID.
- `X-Kushki-SimpleSignature:` Corresponds to the HMAC SHA256 signature of the `X-Kushki-Id`, using your webhook signature ID.
- `X-Kushki-Id:` Date in timestamp format (`UNIX Time`).

<!-- theme: info -->

> #### What is the IP used to send notifications from Kushki?
>
> Notifications are sent from the following static IP of Kushki, you can also check this as an additional validation.
>
> - UAT: `54.208.105.247`
> - Production: `34.230.185.20`

You should use these headings to compare the signature generated from your side by using your Merchant's Webhooks signature ID, that you can find in the console. You can use both `X-Kushki-Signature` and `X-Kushki-SimpleSignature` for the check.

#### How to get the Webhook Signature?

You can view and copy the webhook signature from the Console. To do this, go to __Desarrolladores > Webhooks__. At the top you can easily copy the webhook signature.

![Webhook signature gif](//images.ctfassets.net/mmjbm94f6iyd/6A2NvAuzHFiAzSOHikIRml/6b17e2af6bf0d7dd79deadc722e0fb1b/gif_corto_webhook__1_.gif)

#### Examples

Below you'll find some examples of how to perform a signature check in the headings.

##### X-Kushki-Signature

<CodeTabs group="backend">

```javascript
var crypto = require('crypto')
/**
 * webhook_signature: Backoffice > Desarrolladores > Webhooks
 * x_kushki_id: Request Header
 * $x_kushki_signature: Request header
 * body : Request body
 */
var x_kushki_signature = request.headers["x-kushki-signature"];
var webhook_signature = process.env.WEBHOOK_SIGNATURE;
var x_kushki_id = request.headers["x-kushki-id"];

var body = request.body;
var payload = `${JSON.stringify(body)}.${x_kushki_id}`;

var generated_signature = crypto.createHmac('sha256', webhook_signature).update(payload).digest("hex");
if(x_kushki_signature === generated_signature){
    response.status("200")
} else{
    response.status("401")
}
```

```python
import hmac
import hashlib
import os

####
## webhook_signature: Backoffice > Desarrolladores > Webhooks
## x_kushki_id: Request Header
## $x_kushki_signature: Request header
## body : Request body
####

x_kushki_signature = request.headers["x-kushki-signature"]
x_kushki_id = request.headers["x-kushki-id"]
webhook_signature = os.getenv('WEBHOOK_SIGNATURE')
body = request.body
payload = json.dumps(body)+.+x_kushki_id

generated_signature = hmac.new(bytes(webhook_signature , 'utf-8'), msg = bytes(payload , 'utf-8'), digestmod = hashlib.sha256).hexdigest()

if x_kushki_signature == generated_signature:
    response.status(200)
else:
    response.status(401)
```

```php
<?php
    /**
  * webhook_signature: Backoffice > Desarrolladores > Webhooks
  * x_kushki_id: Request Header
  * $x_kushki_signature: Request header
  * body: Request body
  */

    $webhook_signature = getenv('WEBHOOK_SIGNATURE');
    $x_kushki_id = $_SERVER['HTTP_X_KUSHKI_ID'];
    $x_kushki_signature = $_SERVER['HTTP_X_KUSHKI_SIGNATURE'];
    $body = file_get_contents('php://input');
    $payload = $body.'.'.$x_kushki_id;

    $signature_generated = hash_hmac("sha256", $payload, $webhook_signature);
    if ($signature_generated === $x_kushki_signature) {
        header("Status: 200 OK");
    } else {a
        header("Status: 401 Not authenticated");
    }
?>
```

</CodeTabs>

##### X-Kushki-SimpleSignature

<CodeTabs group="backend">

```javascript
var crypto = require('crypto')

/** 
  * webhook_signature: Backoffice > Desarrolladores > Webhooks
  * x_kushki_id: Request Header
  * $x_kushki_simple_signature: Request header
  */

var x_kushki_simple_signature = request.headers["x-kushki-simplesignature"];
var webhook_signature = process.env.WEBHOOK_SIGNATURE;
var x_kushki_id = request.headers["x-kushki-id"];

var generated_signature = crypto.createHmac('sha256', webhook_signature).update(kushki_id).digest("hex");

if(x_kushki_simple_signature === generated_signature){
  response.status("200")
} else{
  response.status("401")
}
```

```python
import hmac
import hashlib
import os

####
## webhook_signature: Backoffice > Desarrolladores > Webhooks
## x_kushki_id: Request Header
## $x_kushki_simple_signature: Request header
####

x_kushki_simplesignature = request.headers["x-kushki-simplesignature"]
x_kushki_id = request.headers["x-kushki-id"]
webhook_signature = os.getenv('WEBHOOK_SIGNATURE')

generated_signature = hmac.new(bytes(webhook_signature , 'utf-8'), msg = bytes(x_kushki_id , 'utf-8'), digestmod = hashlib.sha256).hexdigest()

if x_kushki_simplesignature == generated_signature:
    response.status(200)
else:
    response.status(401)
```

```php
<?php
    /** 
  * webhook_signature: Backoffice > Desarrolladores > Webhooks
  * x_kushki_id: Request Header
  * $x_kushki_simple_signature: Request header
  */

    $webhook_signature = getenv('WEBHOOK_SIGNATURE');
    $x_kushki_id = $_SERVER['HTTP_X_KUSHKI_ID'];
    $x_kushki_simple_signature = $_SERVER['HTTP_X_KUSHKI_SIMPLESIGNATURE'];
    $signature_generated = hash_hmac("sha256", $x_kushki_id, $webhook_signature);
    if ($signature_generated === $x_kushki_simple_signature) {
        header("Status: 200 OK");
    } else {
        header("Status: 401 Not authenticated");
    }
?>
```

</CodeTabs>

--- 

According to the functionalities you have integrated, there will be different types of body for requests:

- [Card Payments](card-payments.md)
- [Refunds](refunds.md)


---
