<div style="background:#1E65AE;">

<br>
<h1 style="color:white;font-weight:bold;font-size: 60px;margin-left:100px;margin-top:50px;margin-right:100px;margin-bottom:50px;">Release notes</h1>

<p style="color:white;margin-left:100px;margin-bottom:50px;margin-right:100px;font-size:1.3em;">Discover the latest feature releases, product improvements and bug fixes for <b>Kushki Card Present Payment Services</b>.</p>
<br>
</div>

<br>

**Stay up to date with changes and updates to the Kushki API.**

We used the [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) standard (**YYYY-MM-DD**) for dates, the Semantic Versioning (**MAJOR.MINOR.PATCH**) for version numbers, increasing the:

1. **MAJOR** version when we make incompatible API changes,
2. **MINOR** version when we add functionality in a backward-compatible manner, and
3. **PATCH** version when we make backward-compatible bug fixes.

### Types of changes

- <b style="background-color:#0DC298;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">NEW</b> for new features.
- <b style="background-color:#4498EE;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">IMPROVEMENTS</b> for changes in existing functionality.
- <b style="background-color:#ffa500;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">DEPRECATED</b> for soon-to-be removed features.
- <b style="background-color:#E26C81;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">REMOVED</b> for now removed features.
- <b style="background-color:#DD85C3;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">FIX</b> for any bug fixes.
- <b style="background-color:#D62C4B;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">SECURITY</b> in case of vulnerabilities.

<hr>

<!-- 


#### Estilos para los tipos de cambios

NEW: 

<b style="background-color:#0DC298;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">NEW</b>

IMPROVEMENTS:

<b style="background-color:#4498EE;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">IMPROVEMENTS</b>

DEPRECATED:

<b style="background-color:#ffa500;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">DEPRECATED</b>

REMOVED:

<b style="background-color:#E26C81;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">REMOVED</b>

FIX:

<b style="background-color:#DD85C3;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">FIX</b>

SECURITY:

<b style="background-color:#D62C4B;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">SECURITY</b>

#### Estilo para el último release note

<h2> <b style="background-color:#023365;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;border-style:solid;border-color:red;">1.14.0</b> 2024-01-29 </h2>

-->

## Latest

###  <b style="background-color:#023365;color:white;border-radius: 10px;padding: 5px;width: 20%;text-align: center;">1.1.0 - 2024-12-05</b>

<b style="background-color:#00E6B2;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">NEW</b> **Idempotency**


Idempotency ensures that multiple requests with the same purpose do not create duplicate transactions. To create a new payment request, the client must include the idempotency key (mandatory). The `idempotencyKey` must be unique for each request and is used to track the transaction's status.

- New service: [Create payment request with idempotency](https://api-docs.kushkipagos.com/docs/card-present-chile/cloud-terminal-api/operations/create-a-remote-payment-v-2-create).
- New service: [Get payment request status](https://api-docs.kushkipagos.com/docs/card-present-chile/cloud-terminal-api/operations/get-a-remote-payment-v-2-get-payment-request). This service returns the `transactionReference` and `acquirerId` (ticket_number).

<!-- theme: warning -->
> #### Deprecated services!
>
> Existing endpoints are still available but will be deprecated soon.
>We recommend you to migrate to the new idempotency services.

<b style="background-color:#4498EE;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">IMPROVEMENTS</b>
- The `ticket_number` is now printed in the voucher.
- Information sent in `customFields` object will be mapped to Kushki metadata.


## Previous release notes

<!--
Previous release notes
-->

###  <b style="background-color:#023365;color:white;border-radius: 10px;padding: 5px;width: 20%;text-align: center;">1.0.1 - 2024-11-14</b>

<b style="background-color:#4498EE;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">IMPROVEMENTS</b>

Updated transaction status for voids and refunds.

<hr>

###  <b style="background-color:#023365;color:white;border-radius: 10px;padding: 5px;width: 20%;text-align: center;">1.0.0 - 2024-10-29</b>

<b style="background-color:#00E6B2;color:white;border-radius: 8px;padding: 5px;width: 20%;text-align: center;font-size: 12px;">NEW</b>

- Accept card present payments.

<br>

<!-- focus: false -->

