---
stoplight-id: qchoke79kyh2p
---

# Errors

Learn about common mistakes and how to solve them.

## HTTP Status Codes

Kushki might return different HTTP status codes depending on the requests made. Below are the most common HTTP status codes, their associated standard message, as well as a more detailed description of the response.

| Code     | Message     | Detail     |
| ---------- | ---------- | ---------- |
| 200      | OK       | The process was successful. Everything worked as expected, according to the HTTP method      |
| 400      | Bad Request       | The server cannot interpret the request (incorrect syntax, too large size, missing parameters)       |
| 401       | Authorization Required       | Credentials must be authenticated, or authentication has failed       |
| 403       | Forbidden       | Do not have the necessary permissions to perform this action       |
| 404       | Not Found       | Resource or page not found       |
| 409       | Conflict       | The request cannot be processed because of a conflict with the resource (e.g., multiple simultaneous updates)      |
| 410       | Gone       | The requested resource has been deleted from the server, and will no longer be available |
| 412       | Precondition failed | Indicates that access to the target resource has been denied |
| 429       | Too Many Requests       | Too many requests have been sent in a short period of time       |
| 430       | Request Header Fields Too Large       | This status code indicates that the server is unwilling to process the request because its header fields are too large. |
| 500       | Internal Server Error       | An unexpected server-side error occurred       |
| 502       | Bad Gateway       | The server (acting as a proxy or gateway) received an invalid response from another server       |
| 503       | Service Temporarily Unavailable       | The server is unavailable (usually because it is under maintenance, or because it is overloaded)       |
| 504       | Gateway Timeout       | The server (acting as a proxy or gateway) has not received a response from the other server in time     |

## Error codes for Creating Payment Request Service

In case of error while generating a payment request a response like the following will be returned:

```json
{
  "error": true,
  "code": "MR-110",
  "message": "Transaction Amount is less than allowed minimum"
}
```

The following table describes the errors that can be generated during the [generation of a payment request](https://api-docs.kushkipagos.com/docs/card-present-chile/cloud-terminal-api/operations/create-a-remote-payment-v-2-create).


|  Code |  Type |  Message |
|---|---|---|
|  MR-100	 | Device  | Device for API-Key doesn't exist  | 
| MR-110  | Input field  | Transaction Amount is less than allowed minimum  |
| MR-120	  | Input field  |  Transaction Amount is more than allowed	 | 
| MR-130	  | Input field  | DTE type not recognized	  |
|  MR-140	 | Input field   | No exempt amount found for DTE Type 99  |
|  MR-141	 | Input field   | Exempt amount not equal to transaction amount  |
| MR-150	  | Input field  | Exempt Amount is not less than transaction amount  | 
| MR-151	  |  Input field  |  Exempt Amount is invalid	 |
| MR-000	  |  Authorization |  Not Authorized	 |
| MR-160	  |  Payment Request | Payment Request doesn't exist	  |
| MR-161	  | Device |  Device by SN not found	 | 
| MR-170	  | Service  | Error with Database	  |
| MR-180	  |  Queue of Requests | Payment Request Queue for the device is full. **Note: The maximum number of requests in queue is up to 5.**	  |
| I-04	  | Customized Fields  | ExtraData String has invalid characters	  |
| INT-MIDDLEWARE-429  | Limit of Requests  | API Quota Exceeded! Quota: {0} per {1}, Try Again in {2} seconds  |
| KEY-002 	  | Authentication  | API Key is missing in the request header  |
| KEY-003 	  | Authentication | Invalid API Key	  |
| RP-000 	  | Idempotency	  | Invalid Idempotency Key	  |
| RP-001 	  |  Input field |  Idempotency Key length must be between 1 and 36 characters |
| RP-003 	  | Input field  |  The characters entered are invalid |
| RP-004 	  | Input field   |  Invalid characters in source version |
| RP-007 	  | Custom Fields  | Reserved custom field name	  |
| RP-010 	  | Custom Fields | Maximum custom fields exceeded  |
| RP-026 	  | Custom Fields  | Duplicate custom field names	  |
| I-02	  | Custom Fields   |  Custom field length invalid	 |
| I-03	  |  Custom Fields  | Custom field length invalid	  |
| MR-191 	  | Idempotency	  | The identifier provided is already in use.  |
| MR-203 *	  |  Payment request | Payment request is in process	  |
|RP-005 *	  | Input field | No exempt amount for specific DTE types  |
| RP-006 *	  | Input field  |  Exempt amount does not match total |


## Codes returned by Kushki in Voids attempts

The response codes received by processors and issuers will appear in the `kushki_response` object as in the next example. 

```json
"kushki_response": {
        "code": "01",
        "message": "Refer to card issuer"
    },
```

In the __code__ and __message__ columns of the table below, the code and message sent by Kushki are shown. In the column __What to do?__, we provide you with a more detailed explanation of the causes and the possible procedure to follow.

 An example of a message returned by Kushki's API is shown below:


| code | message | What to do? |
| -- | -- | -- |
| 000 | Transacción Aprobada. | Indicates that the transaction was successfully approved. |
| 01 | Refer to card issuer | The cardholder must contact their card issuer to understand why the transaction was rejected |
| 04 | Capture card | The cardholder must retry the transaction|
| 05 | Do not honor | The cardholder must retry the transaction|
| 12 | Invalid transaction | The transaction is not allowed by the payment processor or the card issuer. Contact the card issuer|
| 32 | Expired card | The cardholder should use an alternative card |
| 41 | Lost card | The cardholder should contact their card issuer for them to review the case |
| 57 | Transaction not permitted to cardholder| The cardholder should contact their card issuer for them to review the case |
| 62 | Restricted card | The cardholder should contact their card issuer for them to review the case |
| 91 | Authorization System or issuer system inoperative |  The cardholder should retry the transation
| 92 | Unable to route transaction | The cardholder should retry or contact the issuer|
| 6P | Verification data failed| Retry the transaction|
| E016 | Refund not available| Check that the refund is within the allowed period |