# Refunds

Kushki can send events to your webhook notifying your application when one of the following events occurs:

* When a refund is approved.

<!-- theme: info -->

> You can also check the status of returns from your Console.


### Structure

The webhooks sent by Kushki will contain the headers [listed here](introduction.md#authentication). <br/>
These are the possible variables that are submitted in the Webhook body:

__Method:__ `POST`

__Body:__ `Object`

| Variable     | Type     |
| ---------- | ---------- | 
| `country` | `string` |
| `franchise` | `string` |
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

<!--
title: "Refund"
lineNumbers: true
-->
```json
{
    "country": "Mexico",
    "franchise": "VISA",
    "available": true,
    "channel": "POS",
    "public_credential_id": "146cbf33c7fd45c0271cbf9d31d4478d",
    "client_transaction_id": "6681eadc-6d8d-44ba-8ca0-18e061c1172a",
    "mcc": "1234",
    "card_country": "MEX",
    "processor_name": "VISA",
    "transaction_reference": "daa8583d-f18c-419a-840e-be5c95011eb6",
    "payment_method": "card",
    "card_details": {
        "card_sequential": "11",
        "prosa_info": {},
        "reading_type": "ICC",
        "tlv": "9F2701809F1A0206049A032208309F02060000000120005F2A0206044F07A00000000310109F0607A00000000310109F26085DE291D252397F709F100706010A03A020009F37044A05C99750095649534120544553549F6E009F5B009F3602008C9F330360F8C89F03009C010082021C008407A00000000310105F34011195058080048000"
    },
    "transaction_id": "111663896831621702",
    "created": 1663896831738,
    "merchant_name": "Tu libreria",
    "transaction_type": "REFUND",
    "processor": {
        "code": "000",
        "message": "Transacción Aprobada."
    },
    "reference_number": "226520105211",
    "tax_id": "7283839421223",
    "sync_mode": "online",
    "additional_info": {
        "f7": "0922203351",
        "f32": "408210",
        "f11": "100611",
        "f62s2": "40000000000000000302145412649612",
        "f37": "226520100611"
    },
    "subtotal_iva0": 60,
    "deferred": {
        "months": "1"
    },
    "response_code": "00",
    "transaction_status": "APPROVAL",
    "social_reason": "TU LIBRERIA",
    "payment_brand": "VISA",
    "acquirer_bank": "Kushki",
    "request_amount": 60,
    "merchant_id": "20000000105850418000",
    "approved_transaction_amount": 0.6,
    "merchant_category": "Medium",
    "acq_transaction_type": "Refund",
    "security": {},
    "masked_credit_card": "476134XXXXXX0043",
    "authorization_code": "120606",
    "issuing_bank": "VISA",
    "processor_id": "1652365464",
    "cvm_type": "none",
    "foreign_card": true,
    "pos_details": {
        "location": {
            "latitude": -0.22480833333333333,
            "longitude": -78.487955
        },
        "model": "P2-EU",
        "version": "Kushki SunmiV1.1.26",
        "brand": "SUNMI",
        "terminal_id": "PB04216R24337"
    },
    "last_four_digits": "0043",
    "approval_code": "120606",
    "amount": {
        "extra_taxes": {},
        "currency": "MXN",
        "subtotal_iva0": 60
    },
    "rules_response": {
        "country": "MEX",
        "commercial_executive": "user@example.com",
        "business_category": "0",
        "address": "Centro 123",
        "contact_person": "Jhon Doe",
        "authorizer": {
            "authorizer_name": "VISA",
            "soft_descriptor": "KSK*TEST",
            "authorizer_bank_id": "",
            "authorizer_type": "",
            "commerce_code": "353453",
            "authorizer_acquirer_bin": "408210",
            "retailer_id": "",
            "category_model": "0",
            "terminal_id": "1652365464",
            "authorizer_alias": "VISA",
            "url": "http://internal-k8s-acquirer-acquirer-83c4eec5cf-1220747559.us-east-1.elb.amazonaws.com/visa/"
        },
        "city": "Monterrey",
        "merchant_name": "Tu libreria",
        "telephone": "8100000001",
        "mcc": "1234",
        "url": "http://internal-k8s-acquirer-acquirer-83c4eec5cf-1220747559.us-east-1.elb.amazonaws.com/visa/",
        "zip_code": "64000",
        "tax_id": "asdf12345678",
        "province": "NUEVO LEON",
        "total_amount": "60.000000",
        "business_registration_id": "000000000001",
        "tcc": "H",
        "business_line": "37006",
        "currency": "MXN",
        "id": "1652365464",
        "acquirer_type": "kushki"
    },
    "acq_transaction_scope": "international",
    "contact_details": {
        "document_type": "-1"
    },
    "acq_transaction_mode": "Authorization",
    "card_type": "credit",
    "ticket_number": "111663896831738702",
    "card_country_code": "MEX",
    "credential_alias": "Tu libreria",
    "bin_card": "476134",
    "credential_id": "245c10502cd844ebae4ec9a70610d89b",
    "transactionReference": "daa8583d-f18c-419a-840e-be5c95011eb6"
}
```
