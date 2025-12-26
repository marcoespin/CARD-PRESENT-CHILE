# Card payments webhooks

Kushki can send webhook events notifying your application when one of the following events occurs:

* When a credit or debit card transaction is approved or rejected.
* When a void is made

### Structure

The webhooks sent by Kushki will contain the headers [listed here](introduction.md#authentication). <br/>
These are the possible variables that are submitted in the Webhook body:

__Method:__ `POST`

__Body:__ `Object`

| Variable     | Type     |
| ---------- | ---------- | 
| `country` | `string` |
| `franchise` | `string` |
| `metadata`       | `object`       |
| `metadata.key0`       | `string`       |
| `metadata.key1`       | `string`       |
| `metadata.key2`       | `string`       |
| `available` | `boolean` |
| `channel` | `string` |
| `public_credential_id` | `string` |
| `client_transaction_id` | `string` |
| `mcc` | `string` |
| `card_country` | `string` |
| `processor_name` | `string` |
| `transaction_reference` | `string` |
| `payment_method` | `string` |
| `card_details` | `object` |
| `card_details.prosa_info` | `object` |
| `card_details.reading_type` | `string` |
| `card_details.card_sequential` | `string` |
| `card_details.tlv` | `string` |
| `transaction_id` | `string` |
| `created` | `integer` |
| `merchant_name` | `string` |
| `transaction_type` | `string` |
| `processor` | `object` |
| `processor.code` | `string` |
| `processor.message` | `string` |
| `reference_number` | `string` |
| `tax_id` | `string` |
| `sync_mode` | `string` |
| `additional_info` | `object` |
| `additional_info.f7` | `string` |
| `additional_info.f63` | `string` |
| `additional_info.f11` | `string` |
| `additional_info.f37` | `string` |
| `additional_info.f32` | `string` |
| `additional_info.f62s2` | `string` |
| `subtotal_iva0` | `number` |
| `deferred` | `object` |
| `deferred.months` | `string` |
| `response_code` | `string` |
| `transaction_status` | `string` |
| `social_reason` | `string` |
| `payment_brand` | `string` |
| `acquirer_bank` | `string` |
| `request_amount` | `number` |
| `merchant_id` | `string` |
| `merchant_category` | `string` |
| `acq_transaction_type` | `string` |
| `security` | `object` |
| `security.ip` | `string` |
| `security.user_agent` | `string` |
| `masked_credit_card` | `string` |
| `authorization_code` | `string` |
| `issuing_bank` | `string` |
| `processor_id` | `string` |
| `foreign_card` | `boolean` |
| `pos_details` | `object` |
| `pos_details.model` | `string` |
| `pos_details.location` | `object` |
| `pos_details.location.latitude` | `number` |
| `pos_details.location.longitude` | `number` |
| `pos_details.version` | `string` |
| `pos_details.brand` | `string` |
| `pos_details.terminal_id` | `string` |
| `last_four_digits` | `string` |
| `approval_code` | `string` |
| `amount` | `object` |
| `amount.extra_taxes` | `object` |
| `amount.currency` | `string` |
| `amount.subtotal_iva0` | `number` |
| `rules_response` | `object` |
| `rules_response.country` | `string` |
| `rules_response.commercial_executive` | `string` |
| `rules_response.business_category` | `string` |
| `rules_response.address` | `string` |
| `rules_response.city` | `string` |
| `rules_response.authorizer` | `object` |
| `rules_response.authorizer.authorizer_name` | `string` |
| `rules_response.authorizer.soft_descriptor` | `string` |
| `rules_response.authorizer.authorizer_bank_id` | `string` |
| `rules_response.authorizer.commerce_code` | `string` |
| `rules_response.authorizer.authorizer_type` | `string` |
| `rules_response.authorizer.retailer_id` | `string` |
| `rules_response.authorizer.authorizer_acquirer_bin` | `string` |
| `rules_response.authorizer.category_model` | `string` |
| `rules_response.authorizer.url` | `string` |
| `rules_response.authorizer.authorizer_alias` | `string` |
| `rules_response.authorizer.terminal_id` | `string` |
| `rules_response.contact_person` | `string` |
| `rules_response.merchant_name` | `string` |
| `rules_response.telephone` | `string` |
| `rules_response.mcc` | `string` |
| `rules_response.url` | `string` |
| `rules_response.zip_code` | `string` |
| `rules_response.tax_id` | `string` |
| `rules_response.province` | `string` |
| `rules_response.business_registration_id` | `string` |
| `rules_response.tcc` | `string` |
| `rules_response.total_amount` | `string` |
| `rules_response.business_line` | `string` |
| `rules_response.currency` | `string` |
| `rules_response.id` | `string` |
| `rules_response.acquirer_type` | `string` |
| `acq_transaction_scope` | `string` |
| `contact_details` | `object` |
| `contact_details.document_number` | `string` |
| `contact_details.document_type` | `string` |
| `acq_transaction_mode` | `string` |
| `card_type` | `string` |
| `ticket_number` | `string` |
| `card_country_code` | `string` |
| `credential_alias` | `string` |
| `bin_card` | `string` |
| `credential_id` | `string` |
| `cvm_type` | `string` |
| `approved_transaction_amount` | `number` |
| `transactionReference` | `string` |

### Examples

```json
{
    "country": "Chile",
    "franchise": "VISA",
    "metadata": {
    "transaccionCodigo": "1245",
    "type": "test",
    "transaccionId": "1234"
  },
    "available": true,
    "channel": "POS",
    "public_credential_id": "146cbac61b881aa4111cbf9825162671",
    "client_transaction_id": "ae6a111a-9173-4ec7-8734-3178454b13341",
    "mcc": "1234",
    "card_country": "CHL",
    "processor_name": "VISA",
    "transaction_reference": "718fa526-6f41-405f-a1f5-a71db52dfa12",
    "payment_method": "card",
    "card_details": {
        "prosa_info": {},
        "reading_type": "MCR"
    },
    "transaction_id": "111663595155511179",
    "created": 1663895155240,
    "merchant_name": "Tu libreria",
    "transaction_type": "SALE",
    "processor": {
        "code": "000",
        "message": "Transacción Aprobada."
    },
    "reference_number": "226520101123",
    "tax_id": "7283839521223",
    "sync_mode": "online",
    "additional_info": {
        "f7": "0922200555",
        "f63": "MDS8TNCN9",
        "f11": "101883",
        "f37": "226520101883"
    },
    "subtotal_iva0": 101.99,
    "deferred": {
        "months": "1"
    },
    "response_code": "00",
    "transaction_status": "APPROVAL",
    "social_reason": "TU LIBRERIA",
    "payment_brand": "VISA",
    "acquirer_bank": "Kushki",
    "request_amount": 101.99,
    "merchant_id": "20000000305053001000",
    "approved_transaction_amount": 101.99,
    "merchant_category": "Medium",
    "acq_transaction_type": "charge",
    "security": {
        "ip": "192.0.254.111",
        "user_agent": "PostmanRuntime"
    },
    "masked_credit_card": "400000XXXXXX0002",
    "authorization_code": "533804",
    "issuing_bank": "BankACQ",
    "processor_id": "1652365464",
    "foreign_card": true,
    "pos_details": {
        "model": "P2-EU",
        "location": {
            "latitude": -0.1848114,
            "longitude": -78.4719161
        },
        "brand": "SUNMI",
        "version": "Kushki SunmiV1.1.13",
        "terminal_id": "PB04209860123"
    },
    "last_four_digits": "004",
    "approval_code": "533804",
    "amount": {
        "extra_taxes": {},
        "currency": "CLP",
        "subtotal_iva0": 101.99
    },
    "rules_response": {
        "country": "CHL",
        "address": "Centro 123",
        "business_category": "0",
        "commercial_executive": "user@example.com",
        "authorizer": {
            "authorizer_name": "VISA",
            "soft_descriptor": "KSK*TEST",
            "authorizer_bank_id": "",
            "authorizer_type": "",
            "commerce_code": "353453",
            "retailer_id": "",
            "authorizer_acquirer_bin": "400000",
            "category_model": "0",
            "terminal_id": "1652365413",
            "authorizer_alias": "VISA",
            "url": "http://internal-k8s-acquirer-acquirer-83c4eec5cf-1220747559.us-east-1.elb.amazonaws.com/mc/"
        },
        "city": "Monterrey",
        "contact_person": "John Doe",
        "merchant_name": "Tu libreria",
        "telephone": "8100000001",
        "mcc": "1234",
        "tax_id": "asdf12345678",
        "url": "http://internal-k8s-acquirer-acquirer-83c4eec5cf-1220747559.us-east-1.elb.amazonaws.com/mc/",
        "zip_code": "64000",
        "province": "NUEVO LEON",
        "tcc": "H",
        "total_amount": "101.990000",
        "business_registration_id": "000000000001",
        "business_line": "37006",
        "currency": "MXN",
        "id": "1652365464",
        "acquirer_type": "kushki"
    },
    "acq_transaction_scope": "international",
    "contact_details": {
        "document_number": "123666",
        "document_type": "0"
    },
    "acq_transaction_mode": "Authorization",
    "card_type": "credit",
    "ticket_number": "111663890155212345",
    "card_country_code": "MEX",
    "credential_alias": "Tu libreria",
    "bin_card": "400000",
    "credential_id": "245c10532cd844e2a1ec9a83177abb1",
    "transactionReference": "718fa426-bf41-405f-a1f5-a71db52da122"
}
```
