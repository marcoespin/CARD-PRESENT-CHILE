# Good practices


## Idempotency

Kushki stores its notifications on multiple servers to improve redundancy and achieve high availability. For this reason, on rare occasions, you could obtain a duplicate notification.

Remember to design your Webhook endpoint to be idempotent (i.e., it should not be negatively affected when it processes the same notification more than once).

## Quick Response

If your Webhook endpoint runs complex logic or performs HTTP calls, it might occur a timeout before Kushki can be notified of its reception. For this reason, it is best to acknowledge a webhook receipt immediately, by returning an HTTP 200 code, and performing the rest of the tasks afterward, or performing other tasks in parallel, or in the background.

## Tests

Interactions between endpoints on the internet can be somewhat complicated, and they can become a pain in the neck when certain extreme situations occur that can impact the performance of your application. This is why we recommend you check that your Webhook is working adequately before releasing it for production.