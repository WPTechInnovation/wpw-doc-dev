For the alpha release, we decided to go with five different languages. Their documented API can be found here:

<div class="download">
  <a class="md-button" href="../nodejs/">Node.js</a>
  <a class="md-button" href="../python27/">Python</a>
  <a class="md-button" href="../java/">Java</a>
  <a class="md-button" href="../dotnet/">.NET</a>
  <a class="md-button" href="../getting-started-with-go/">Go</a>
</div>

## Specification

|**Parameter**|**Description**|
| ------------- | -----|
|`setup`|Sets up the wrapper to be able to start communicating with the underlying SDK.|
|`addService`|Adds a WWService service type to the producer (merchant). Used if the device you are operating on is a producer. If added to a device you intend as a consumer (shopper), this will give that device producer functionality.|
|`removeService`|Removes the service from the producer.|
|`initConsumer`|Initiates the device as a consumer, which enables it to find services, choose prices, make payments and receive services.|
|`initProducer`|Initiates the device as a producer / or initialises the producer capability.|
|`getDevice`|Provides details of the the current device that the SDK is running on, and its credentials / information.|
|`startServiceBroadcast`|Enables the producer device to start broadcasting itself via UDP broadcast over the network to notify devices it is available to be consumed.|
|`stopServiceBroadcast`|Stops the SDK from broadcasting the messages that it is broadcasting.|
|`deviceDiscovery`|Enables the consumer device to discover other devices broadcasting on the same UDP network.|
|`requestServices`|Gets a list of services that are available from the broadcasting device.|
|`getServicePrices`|Used by the consumer to get the list of prices associated with a particular `serviceId`.|
|`selectService`|Performed by the consumer, this provides details of the service, the amount and at what price point it wants to purchase the service.|
|`makePayment`|Allows the consumer to request a payment to be made at the producer device, by providing the total price response object as the request. The producer will then make the payment (or attempt to) and send back a payment response detailing whether it was successful or not.|
|`beginServiceDelivery`|Requested by the consumer, this begins the service delivery which proceeds as long as the correct information is provided to the producer. If the correct credentials are passed, the producer will start releasing the service known as a 'trusted trigger'.|
|`endServiceDelivery`|Ends the service delivery - a request initiated by the consumer.|

