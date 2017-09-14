For the alpha release, we made the decision to go with four different wrappers. Their documented API can be found here:

[The flows diagram and introduction to the api is useful here too](the-flows.html#setup)

<div class="download">
  <a class="md-button" href="wrapper-doc/javadoc">Java (Javadoc)</a>
  <a class="md-button" href="python27.html">Python 2.7 doc</a>
  <a class="md-button" href="dotnet.html">.net / C# doc</a>
  <a class="md-button" href="nodejs.html">Node.js doc</a>
</div>

#### Specification

|**Parameter**|**Description**|
| ------------- | -----|
|setup|Sets up the wrapper to be able to start communicating with the underlying SDK.|
|addService|Adds a service of type WWService to the producer, used if the device you are operating on is a producer, if added to a device you intend as a consumer this will give that device producer functionality.|
|removeService|This removes the service from the producer|
|initConsumer|This initiates the device as a consumer, which enables it to find services, negotiate prices, make payments and receive services.|
|initProducer|This initiates the device as a producer / or initialises the devices producer capability.|
|getDevice|This is able to provide back details of the the current device that the SDK is running on, and it credentials / information.|
|startServiceBroadcast|This enables the producer device to start broadcasting itself via UDP broadcast over the network to notify devices it is available to be consumed.|
|stopServiceBroadcast|This method stops the SDK from broadcasting the current service messages that it is broadcasting.|
|deviceDiscovery|This enables the consumer device to discovery other devices (producers) on the network that are UDP broadcasting.|
|requestServices|Get a list of services that are available from the broadcasting device.|
|getServicePrices|This is used by the consumer to get the list of prices associated with a particular serviceId|
|selectService|Selection of a service is performed by the consumer, providing details of the service, the amount and at what price point it wants to purchase the service.|
|makePayment|This allows the consumer to request a payment be made at the producer device, by providing the total price response object as the request. The producer will then make the payment (or attempt to) and send back a Payment Response detailing whether it was successful or not.|
|beginServiceDelivery|This begins the service delivery, and is requested by the consumer, and will proceed as long as the correct information is provided to the producer. If the correct credentials are passed through, then the producer will start releasing the service known as a 'trusted trigger'|
|endServiceDelivery|This ends the service delivery, a request initiated by the consumer.|