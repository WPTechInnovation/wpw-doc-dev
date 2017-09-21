!!! summary
    
    This is an early reference guide which has evolved since it was first published. However, in combination with the SDK code, it should give you plenty of hints as to how to work with the SDK. 

## Service discovery messages

We're going to build a reference application to prove the concepts and APIs outlined above. This reference application will be implemented on the current range of platforms aimed at providing IoT services. These boards are typically running ‘M’ class processors which as yet do not contain an SE. Currently only the application processors (A class such as A57 Cortex) contain SEs. However developments are being made in the IoT platform space, for example ARM has released a new M architecture with does contain an SE, although there will be a delay before boards using these processors and compiler tools become mainstream. This document requires these more secure platforms to be available.

### Service broadcast

``` json
{
	"DeviceDescription": "Worldpay Within Enabled Electric Car Charger",
	"Hostname": "[Your hostname]",
	"PortNumber": [Your port number],
	"ServerID": "58d8f9fb-b3e9-45bc-b701-fcdd295bc265",
	"UrlPrefix": "v1/carcharge"
}
```


### Service list request

To build the URL, use the hostname and the port number, then concatenate the URL with “service/discover”.

`http://[Your hostname]:[Your port number]/v1/carcharge/service/discover`
    
``` json
 {
 } 
```

!!! note

    The body content is empty; the request is direct to the server, which is indicated in the broadcast.

### Service list response

``` json
{
	"ServerID": "58d8f9fb-b3e9-45bc-b701-fcdd295bc265",
 	"Services": [
 		{
 			"ServiceID": 0,
 			"ServiceDescription": "Car charging"
 		},
 		{
 			"ServiceID": 1,
 			"ServiceDescription": "Car parking"
 		}
 	]
}
```

## Service negotiation messages

### Service price request

To build the URL, use the hostname, with the port number, the url prefix all concatenated. The concatenate with “service” concatenated with “service ID” and then “prices”.

`http://[Your hostname]:[Your port number]/v1/carcharge/service/0/prices`

``` json
{
} 
```

!!! note
	
	Body content is empty. URL includes the serviceID (i.e. 0) for the prices being requested, e.g. for serviceID 1, URL would be `/v1/carcharge/service/1/prices`)

### Service price response

``` json
{
	"ServerID" : "58d8f9fb-b3e9-45bc-b701-fcdd295bc265",
 	"Prices" : [
 		{
 			"ServiceID" : 0,
 			"PriceID" : 0,
 			"PricePerUnit" : 140,
 			"UnitID" : 0,
 			"UnitDescription" : "kW",
 			"PriceDescription" : "Slow (3.6kWh)"
 		}, {
 			"ServiceID" : 0,
 			"PriceID" : 1,
 			"PricePerUnit" : 70,
 			"UnitID" : 0,
 			"UnitDescription" : "kW",
 			"PriceDescription" : "Medium (7.2kWh)"
 		}, {
 			"ServiceID" : 0,
 			"PriceID" : 2,
 			"PricePerUnit" : 10,
 			"UnitID" : 0,
 			"UnitDescription" : "kW",
 			"PriceDescription" : "Super (120kWh)"
 		}
 	]
}
```

### Get Total price request

To build the URL, use the hostname, with the port number, the url prefix all concatenated. The concatenate with “service” concatenated with `service ID` and then `requestTotal`.

`http://[Your hostname]:[Your port number]/v1/carcharge/service/0/requestTotal`

``` json
{
	"ClientID":"54560ba2-87c0-4172-a904-67a9b7a5e1ee",
 	"SelectedNumberOfUnits":8,
 	"SelectedPriceID":1
}
```

### Get Total price response

``` json
{
 	"ServerID": "58d8f9fb-b3e9-45bc-b701-fcdd295bc265",
 	"ClientID": "54560ba2-87c0-4172-a904-67a9b7a5e1ee",
 	"PriceID": 1,
 	"UnitsToSupply": 8,
 	"TotalPrice": 560,
 	"PaymentReferenceID": "e7c18800-706d-4f0c-933c-19f8d5be72da",
 	"MerchantClientKey": " T_C_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx "
}
```

### Token request

HTTP POST to:

`https://api.worldpay.com/v1/tokens`

No custom HTTP headers used.

``` json
{
 	"clientKey" : "T_C_xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
 	"paymentMethod" : {
 		"cardNumber" : "1234567890124444",
 		"expiryMonth" : 2,
 		"expiryYear" : 2021,
 		"name" : "Bilbo Baggins",
 		"type" : "Card"
 	},
 	"reusable" : false
}
```

### Token response

``` json
{
 	"token": "TEST_SU_yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy",
 	"paymentMethod": {
 		"type": "ObfuscatedCard",
 		"name": "Bilbo Baggins",
 		"expiryMonth": 2,
 		"expiryYear": 2021,
 		"cardType": "MASTERCARD_CREDIT",
 		"maskedCardNumber": "**** **** **** 4444",
 		"cardSchemeType": "consumer",
 		"cardSchemeName": "MCI CREDIT",
 		"cardIssuer": "LLOYDS BANK PLC",
 		"countryCode": "GB",
 		"cardClass": "credit",
 		"cardProductTypeDescNonContactless": "MasterCard Business",
 		"cardProductTypeDescContactless": "CL MasterCard Bus",
 		"prepaid": "unknown"
 		},
 	"reusable": false
}
```

### Payment request

HTTP POST to:

`http://[Your hostname]:[Your port number]/v1/carcharge/payment`

``` json
{
 	"ClientID" : "54560ba2-87c0-4172-a904-67a9b7a5e1ee",
 	"ClientToken" : "TEST_SU_yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy ",
 	"PaymentReferenceID" : "e7c18800-706d-4f0c-933c-19f8d5be72da"
}
```

### Order request

HTTP POST to `https://api.worldpay.com/v1/orders`. 

HTTP header includes the Merchant's Service Key (Private)

``` json
{
 	"amount" : 560,
 	"currencyCode" : "GBP",
 	"customerOrderCode" : "Car charge (8kW @ Medium (7.2kWh)) - 26\/01\/2016 15:40",
 	"orderDescription" : "Car charging payment",
 	"token" : "TEST_SU_yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy "
}
```

### Order response

``` json
{
 	"orderCode" : "4d22cb5d-5dfb-43ce-9108-dfe230151429",
 	"token" : "TEST_SU_yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy ",
 	"orderDescription" : "Car charging payment",
 	"amount" : 560,
 	"currencyCode" : "GBP",
 	"paymentStatus" : "SUCCESS",
 	"paymentResponse" : {
 		"type" : "ObfuscatedCard",
 		"name" : "Bilbo Baggins",
 		"expiryMonth" : 2,
 		"expiryYear" : 2021,
 		"cardType" : "MASTERCARD_CREDIT",
 		"maskedCardNumber" : "**** **** **** 4444",
 		"cardSchemeType" : "consumer",
 		"cardSchemeName" : "MCI CREDIT",
 		"cardIssuer" : "LLOYDS BANK PLC",
 		"countryCode" : "GB",
 		"cardClass" : "credit",
 		"cardProductTypeDescNonContactless" : "MasterCard Business",
 		"cardProductTypeDescContactless" : "CL MasterCard Bus",
 		"prepaid" : "unknown"
 	},
 	"customerOrderCode" : "Car charge (8kW @ Medium (7.2kWh)) - 26/01/2016 15:40",
 	"environment" : "TEST",
 	"riskScore" : {
 		"value" : "1"
 	}
}
```

### Payment request response

``` json
{
 	"ServerID" : "58d8f9fb-b3e9-45bc-b701-fcdd295bc265",
 	"ClientID" : "54560ba2-87c0-4172-a904-67a9b7a5e1ee",
 	"TotalPaid" : 0,
 	"ServiceDeliveryToken" : "3e7b4c25-157d-4b47-999c-e4faba086590",
 	"client-uuid":"719D329B-8909-4A8B-B352-E449C3132074"
}
```

### Begin Service Delivery request

HTTP POST to 

`http://[Your hostname]:[Your port number]/v1/carcharge/service/0/delivery/begin`

URL encodes the `serviceID` being requested

``` json
{
 	"ClientID" : "54560ba2-87c0-4172-a904-67a9b7a5e1ee",
 	"ServiceDeliveryToken" : "3e7b4c25-157d-4b47-999c-e4faba086590",
 	"UnitsToSupply" : 8
}
```

### Begin Service Delivery response content:

``` json
{
 	"ServerID" : "58d8f9fb-b3e9-45bc-b701-fcdd295bc265",
 	"ClientID" : "54560ba2-87c0-4172-a904-67a9b7a5e1ee",
 	"ServiceDeliveryToken" : "3e7b4c25-157d-4b47-999c-e4faba086590",
 	"UnitsToSupply" : 8
}
```

### End Service Delivery request

HTTP POST to 

`http://[Your hostname]:[Your port number]/v1/carcharge/service/0/delivery/end`

URL encodes the `serviceID` being requested

``` json
{
 	"ClientID" : "54560ba2-87c0-4172-a904-67a9b7a5e1ee",
 	"ServiceDeliveryToken" : "3e7b4c25-157d-4b47-999c-e4faba086590",
 	"UnitsReceived" : 8
}
```

### End Service Delivery response content

``` json
{
 	"ServerID" : "58d8f9fb-b3e9-45bc-b701-fcdd295bc265",
 	"ClientID" : "54560ba2-87c0-4172-a904-67a9b7a5e1ee",
 	"ServiceDeliveryToken" : "3e7b4c25-157d-4b47-999c-e4faba086590",
 	"UnitsJustSupplied" : 8,
 	"UnitsRemaining" : 0
}
```