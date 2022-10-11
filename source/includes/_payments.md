<h1 id="digiteal-api">Digiteal API v1.0.0</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

Base URLs:

* <a href="test.digiteal.eu">test.digiteal.eu</a>

Email: <a href="mailto:email">Support</a> 

# Authentication

- HTTP Authentication, scheme: basic 

<h1 id="digiteal-api-card-token">Card Token</h1>

## reserveFunds

<a id="opIdreserveFunds"></a>

> Code samples

```shell
# You can also use wget
curl -X POST test.digiteal.eu/api/v1/payment-cards/token/reserve \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST test.digiteal.eu/api/v1/payment-cards/token/reserve HTTP/1.1

Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "amountInCents": 100
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('test.digiteal.eu/api/v1/payment-cards/token/reserve',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("test.digiteal.eu/api/v1/payment-cards/token/reserve");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`POST /api/v1/payment-cards/token/reserve`

*Reserve funds*

Check funds availability and reserve funds on the debtor card.

> Body parameter

```json
{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "amountInCents": 100
}
```

<h3 id="reservefunds-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[PaymentCardTokenReserveFundsRequest](#schemapaymentcardtokenreservefundsrequest)|true|none|

> Example responses

> 200 Response

```json
{
  "successful": true,
  "reservationId": "uuid",
  "errorCode": "code",
  "errorMessage": "message"
}
```

<h3 id="reservefunds-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|reservation completed|[PaymentCardTokenReserveFundsResponse](#schemapaymentcardtokenreservefundsresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basic
</aside>

## createTokenFromPkey

<a id="opIdcreateTokenFromPkey"></a>

> Code samples

```shell
# You can also use wget
curl -X POST test.digiteal.eu/api/v1/payment-cards/token/pkey \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST test.digiteal.eu/api/v1/payment-cards/token/pkey HTTP/1.1

Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "companyIdentificationNumber": "BE:VAT:1111",
  "tokenProviderKey": "abcd",
  "customerInternalId": "1234",
  "notificationUrl": "https://notification.com",
  "customer": {
    "name": "John Doe",
    "emailAddress": "john@doe.com",
    "streetName": "Rue Email Francqui",
    "streetNumber": "6",
    "city": "Mont-Saint-Guibert",
    "countryCode": "BE",
    "ipAddress": "1.1.1.1"
  },
  "3dsConfig": {
    "redirectUrl": "https://redirecturl.com",
    "language": "fr-FR",
    "fingerPrintStatus": "NOT_REQUIRED"
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('test.digiteal.eu/api/v1/payment-cards/token/pkey',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("test.digiteal.eu/api/v1/payment-cards/token/pkey");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`POST /api/v1/payment-cards/token/pkey`

*Create token*

Store card information into a permanent token.

> Body parameter

```json
{
  "companyIdentificationNumber": "BE:VAT:1111",
  "tokenProviderKey": "abcd",
  "customerInternalId": "1234",
  "notificationUrl": "https://notification.com",
  "customer": {
    "name": "John Doe",
    "emailAddress": "john@doe.com",
    "streetName": "Rue Email Francqui",
    "streetNumber": "6",
    "city": "Mont-Saint-Guibert",
    "countryCode": "BE",
    "ipAddress": "1.1.1.1"
  },
  "3dsConfig": {
    "redirectUrl": "https://redirecturl.com",
    "language": "fr-FR",
    "fingerPrintStatus": "NOT_REQUIRED"
  }
}
```

<h3 id="createtokenfrompkey-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[PaymentCardTokenCreationRequest](#schemapaymentcardtokencreationrequest)|true|none|

> Example responses

> 200 Response

```json
{
  "3dsRedirectUrl": "https://redirecturl.com"
}
```

<h3 id="createtokenfrompkey-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|token creation requested|[PaymentCardCreationTokenResponse](#schemapaymentcardcreationtokenresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basic
</aside>

## processPayment

<a id="opIdprocessPayment"></a>

> Code samples

```shell
# You can also use wget
curl -X POST test.digiteal.eu/api/v1/payment-cards/token/pay \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST test.digiteal.eu/api/v1/payment-cards/token/pay HTTP/1.1

Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "reservationId": "uuid",
  "amountInCents": 100
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('test.digiteal.eu/api/v1/payment-cards/token/pay',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("test.digiteal.eu/api/v1/payment-cards/token/pay");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

`POST /api/v1/payment-cards/token/pay`

*Initiate Payment*

Charge funds from a previously made reservation. Uncharged funds will be released.

> Body parameter

```json
{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "reservationId": "uuid",
  "amountInCents": 100
}
```

<h3 id="processpayment-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[PaymentCardTokenProcessPaymentRequest](#schemapaymentcardtokenprocesspaymentrequest)|true|none|

> Example responses

> 200 Response

```json
{
  "successful": true,
  "paymentId": "472e651e-5a1e-424d-8098-23858bf03ad7",
  "errorCode": "code",
  "errorMessage": "message"
}
```

<h3 id="processpayment-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|payment processed|[PaymentCardTokenProcessPaymentResponse](#schemapaymentcardtokenprocesspaymentresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basic
</aside>

## cancelReservation

<a id="opIdcancelReservation"></a>

> Code samples

```shell
# You can also use wget
curl -X POST test.digiteal.eu/api/v1/payment-cards/token/cancel \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST test.digiteal.eu/api/v1/payment-cards/token/cancel HTTP/1.1

Content-Type: application/json
Accept: application/json

```

```javascript
const inputBody = '{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "reservationId": "uuid"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'
};

fetch('test.digiteal.eu/api/v1/payment-cards/token/cancel',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```java
URL obj = new URL("test.digiteal.eu/api/v1/payment-cards/token/cancel");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```
`POST /api/v1/payment-cards/token/cancel`

*Cancel reservation*

Release funds from a previously made reservation.

> Body parameter

```json
{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "reservationId": "uuid"
}
```

<h3 id="cancelreservation-parameters">Parameters</h3>

|Name|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[PaymentCardTokenCancelReservationRequest](#schemapaymentcardtokencancelreservationrequest)|true|none|

> Example responses

> 200 Response

```json
{
  "successful": true,
  "errorCode": "code",
  "errorMessage": "message"
}
```

<h3 id="cancelreservation-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|reservation cancelled|[PaymentCardTokenCancelReservationResponse](#schemapaymentcardtokencancelreservationresponse)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
basic
</aside>

# Schemas

<h2 id="tocS_PaymentCardTokenReserveFundsResponse">PaymentCardTokenReserveFundsResponse</h2>
<!-- backwards compatibility -->
<a id="schemapaymentcardtokenreservefundsresponse"></a>
<a id="schema_PaymentCardTokenReserveFundsResponse"></a>
<a id="tocSpaymentcardtokenreservefundsresponse"></a>
<a id="tocspaymentcardtokenreservefundsresponse"></a>

```json
{
  "successful": true,
  "reservationId": "uuid",
  "errorCode": "code",
  "errorMessage": "message"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|successful|boolean|true|none|The reservation is successful if the funds are available and could be reserved on the card.|
|reservationId|string|false|none|The unique id of the reservation.<br>Set only if the reservation is successful.|
|errorCode|string|false|none|Reason code to the reservation failure.<br>Set only if the reservation is not successful.|
|errorMessage|string|false|none|Reason message to the reservation failure.<br>Set only if the reservation is not successful.|

<h2 id="tocS_PaymentCardTokenReserveFundsRequest">PaymentCardTokenReserveFundsRequest</h2>
<!-- backwards compatibility -->
<a id="schemapaymentcardtokenreservefundsrequest"></a>
<a id="schema_PaymentCardTokenReserveFundsRequest"></a>
<a id="tocSpaymentcardtokenreservefundsrequest"></a>
<a id="tocspaymentcardtokenreservefundsrequest"></a>

```json
{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "amountInCents": 100
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|companyIdentificationNumber|string|true|none|Creditor of the transaction.<br>The company must be registered on Digiteal and link to your integrator account.<br>[Format](https://docs.digiteal.eu/technical/index.html#company_national_identifiers)|
|token|string|true|none|Permanent token generated by Digiteal.|
|amountInCents|number|true|none|Amount to be reserved on the card.|

<h2 id="tocS_PaymentCardCreationTokenResponse">PaymentCardCreationTokenResponse</h2>
<!-- backwards compatibility -->
<a id="schemapaymentcardcreationtokenresponse"></a>
<a id="schema_PaymentCardCreationTokenResponse"></a>
<a id="tocSpaymentcardcreationtokenresponse"></a>
<a id="tocspaymentcardcreationtokenresponse"></a>

```json
{
  "3dsRedirectUrl": "https://redirecturl.com"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|3dsRedirectUrl|string(url)|false|none|Url to redirect to the 3DS challenge web page if a challenge is requested by the acquirer.|

<h2 id="tocS_Config3ds">Config3ds</h2>
<!-- backwards compatibility -->
<a id="schemaconfig3ds"></a>
<a id="schema_Config3ds"></a>
<a id="tocSconfig3ds"></a>
<a id="tocsconfig3ds"></a>

```json
{
  "redirectUrl": "https://redirecturl.com",
  "language": "fr-FR",
  "fingerPrintStatus": "NOT_REQUIRED"
}

```

3D secure configuration

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|redirectUrl|string(uri)|true|none|Url to be redirected to after 3DS challenge completion.|
|language|string(bcp-47)|true|none|Language to use on 3DS challenge web page.|
|fingerPrintStatus|string|true|none|Status on the fingerprint request at PKey creation.|

#### Enumerated Values

|Property|Value|
|---|---|
|fingerPrintStatus|NOT_REQUIRED|
|fingerPrintStatus|REQUIRED_ASKED|
|fingerPrintStatus|REQUIRED_NOT_ASKED|

<h2 id="tocS_Customer">Customer</h2>
<!-- backwards compatibility -->
<a id="schemacustomer"></a>
<a id="schema_Customer"></a>
<a id="tocScustomer"></a>
<a id="tocscustomer"></a>

```json
{
  "name": "John Doe",
  "emailAddress": "john@doe.com",
  "streetName": "Rue Email Francqui",
  "streetNumber": "6",
  "city": "Mont-Saint-Guibert",
  "countryCode": "BE",
  "ipAddress": "1.1.1.1"
}

```

Card holder information.

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|name|string|false|none|Card holder full name. Should contains first and last name of the card holder.<br>This field is required if this information was not provided at PKey creation.|
|emailAddress|string(email)|false|none|Card holder email.|
|streetName|string|false|none|Card holder address street name.|
|streetNumber|string|false|none|Card holder address street number.|
|city|string|false|none|Card holder address city name.|
|countryCode|string(iso-3166-2)|false|none|Card holder address country code.|
|ipAddress|string(ipv4)|false|none|Card holder ip address.|

<h2 id="tocS_PaymentCardTokenCreationRequest">PaymentCardTokenCreationRequest</h2>
<!-- backwards compatibility -->
<a id="schemapaymentcardtokencreationrequest"></a>
<a id="schema_PaymentCardTokenCreationRequest"></a>
<a id="tocSpaymentcardtokencreationrequest"></a>
<a id="tocspaymentcardtokencreationrequest"></a>

```json
{
  "companyIdentificationNumber": "BE:VAT:1111",
  "tokenProviderKey": "abcd",
  "customerInternalId": "1234",
  "notificationUrl": "https://notification.com",
  "customer": {
    "name": "John Doe",
    "emailAddress": "john@doe.com",
    "streetName": "Rue Email Francqui",
    "streetNumber": "6",
    "city": "Mont-Saint-Guibert",
    "countryCode": "BE",
    "ipAddress": "1.1.1.1"
  },
  "3dsConfig": {
    "redirectUrl": "https://redirecturl.com",
    "language": "fr-FR",
    "fingerPrintStatus": "NOT_REQUIRED"
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|companyIdentificationNumber|string|true|none|The creditor of the transaction.<br>The company must be registered on Digiteal and link to your integrator account.<br>[Format](https://docs.digiteal.eu/technical/index.html#company_national_identifiers)|
|tokenProviderKey|string|true|none|PKey (temporary token) generated by a Token Service Provider.|
|customerInternalId|string|true|none|Identification used for your reference. This value will be returned in the notification call.|
|notificationUrl|string(uri)|true|none|Url used to make asynchronous call with the token information. [Notifications](https://digiteal.readme.io/docs#notification)|
|customer|[Customer](#schemacustomer)|false|none|Card holder information.|
|3dsConfig|[Config3ds](#schemaconfig3ds)|true|none|3D secure configuration|

<h2 id="tocS_PaymentCardTokenProcessPaymentResponse">PaymentCardTokenProcessPaymentResponse</h2>
<!-- backwards compatibility -->
<a id="schemapaymentcardtokenprocesspaymentresponse"></a>
<a id="schema_PaymentCardTokenProcessPaymentResponse"></a>
<a id="tocSpaymentcardtokenprocesspaymentresponse"></a>
<a id="tocspaymentcardtokenprocesspaymentresponse"></a>

```json
{
  "successful": true,
  "paymentId": "472e651e-5a1e-424d-8098-23858bf03ad7",
  "errorCode": "code",
  "errorMessage": "message"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|successful|boolean|true|none|The payment initiation is successful if the funds are properly charged.|
|paymentId|string(uuid)|false|none|The unique id of the payment.<br>Set only if the payment initiation is successful.|
|errorCode|string|false|none|Reason code to the reservation failure.<br>Set only if the payment initiation is not successful.|
|errorMessage|string|false|none|Reason message to the reservation failure.<br>Set only if the payment initiation is not successful.|

<h2 id="tocS_PaymentCardTokenProcessPaymentRequest">PaymentCardTokenProcessPaymentRequest</h2>
<!-- backwards compatibility -->
<a id="schemapaymentcardtokenprocesspaymentrequest"></a>
<a id="schema_PaymentCardTokenProcessPaymentRequest"></a>
<a id="tocSpaymentcardtokenprocesspaymentrequest"></a>
<a id="tocspaymentcardtokenprocesspaymentrequest"></a>

```json
{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "reservationId": "uuid",
  "amountInCents": 100
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|companyIdentificationNumber|string|true|none|The creditor of the transaction.<br>The company must be registered on Digiteal and link to your integrator account.<br>[Format](https://docs.digiteal.eu/technical/index.html#company_national_identifiers)|
|token|string|true|none|Permanent token generated by Digiteal.|
|reservationId|string|true|none|Identification of the reservation to use.|
|amountInCents|number|true|none|Amount to be charged on the reserved funds.|

<h2 id="tocS_PaymentCardTokenCancelReservationResponse">PaymentCardTokenCancelReservationResponse</h2>
<!-- backwards compatibility -->
<a id="schemapaymentcardtokencancelreservationresponse"></a>
<a id="schema_PaymentCardTokenCancelReservationResponse"></a>
<a id="tocSpaymentcardtokencancelreservationresponse"></a>
<a id="tocspaymentcardtokencancelreservationresponse"></a>

```json
{
  "successful": true,
  "errorCode": "code",
  "errorMessage": "message"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|successful|boolean|true|none|The cancellation is successful if the funds are properly released.|
|errorCode|string|false|none|Reason code to the reservation failure.<br>Set only if the cancellation is not successful.|
|errorMessage|string|false|none|Reason message to the reservation failure.<br>Set only if the cancellation is not successful.|

<h2 id="tocS_PaymentCardTokenCancelReservationRequest">PaymentCardTokenCancelReservationRequest</h2>
<!-- backwards compatibility -->
<a id="schemapaymentcardtokencancelreservationrequest"></a>
<a id="schema_PaymentCardTokenCancelReservationRequest"></a>
<a id="tocSpaymentcardtokencancelreservationrequest"></a>
<a id="tocspaymentcardtokencancelreservationrequest"></a>

```json
{
  "companyIdentificationNumber": "BE:VAT:1111",
  "token": "abcd",
  "reservationId": "uuid"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|companyIdentificationNumber|string|true|none|The creditor of the transaction.<br>The company must be registered on Digiteal and link to your integrator account.<br>[Format](https://docs.digiteal.eu/technical/index.html#company_national_identifiers)|
|token|string|true|none|Permanent token generated by Digiteal.|
|reservationId|string|true|none|Identification of the reservation to cancel.|

