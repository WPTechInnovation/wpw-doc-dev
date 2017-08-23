  There are certain flows that are allowable for the consumer and producer, and this flow should be adhered to when utilising the Worldpay Within SDK. What follows is a diagram of the flow, and then a detailed breakdown of the steps of the flows, what they do; and explicitly the order in which they should be followed.

  The devices are not synchronised by the SDK in any way - so it is up to the developer of the app that sits on top of the SDK to call the Worldpay Within API in the correct order. This is the responsibility of the developer. However if the order below is adhered to then the outcome of the functionality will be as desired.
      
## The Flows diagram

![alt text][logo]
[logo]: ../images/the-flows.svg "The flows of the producer and consumer"

<figcaption>The flows of the producer and consumer</figcaption>




## The Consumer flow

!!! note
    This is the flow of the consumer, please note that these flow steps map to the interface either in Go or in the Wrapper - e.g. in Java this is fully documented in the javadoc.

| Step in Flow | What it does |
| ------------------------ | --------------------------------------------------------------------- |
| 1. SETUP                 | Setups up the device                                                  | 
| 2. DEVICE DISCOVERY      | Discover devices that are broadcasting messages                       | 
| 3. (CHOOSE MESSAGE)      | Choose the message, then use that information in the following steps  | 
| 4. INIT CONSUMER         | Initialises the device as a consumer                                  | 
| 5. REQUEST SERVICES      | Request service messages from the device that is broadcasting, which lists what services it's offering | 
| 6. GET SERVICE PRICES    | Get's the prices for the service you are interested in                | 
| 7. SELECT SERVICE        | Selects the service the device wants to consume                       | 
| 8. MAKE PAYMENT          | Makes a payment for the service that is chosen                        | 
| 9. BEGIN SERVICE DELIVERY| Starts the process / flow to consume the service based on the service token received         | 
| 10. STOP SERVICE DELIVERY| Called to tell the other thing that it has completed it's consumption of the service         | 

## The Producer flow

!!! note
    This is the flow of the producer, please note that these flow steps map to the interface either in Go or in the Wrapper - e.g. in Java this is fully documented in the javadoc.

| Step in Flow | What it does |
| ------------------------ | --------------------------------------------------------------------- |
| 1. SETUP                 | Setups the device                                                  | 
| 2A. ADD SERVICE          | Adds a service to the producer                       | 
| 2B. REMOVE SERVICE       | Remvoves a service from the producer  | 
| 3. INIT PRODUCER         | Initialises the producer                                  | 
| 4A. START BROADCAST      | Starts the producer broadcasting it's service message | 
| 4B. STOP BROADCAST       | Stops the producer from broadcasting it's service message                | 

## API calls

  The steps in the flow neatly map to the api flows, here is some further information about what they do:

| Method                 | Description                                     |
| ---------------------- | ----------------------------------------------- |
| `setup`                | Sets up the wrapper to be able to start communicating with the underlying SDK |
| `addService`           | Adds a service of type WWSerive to the producer, used if the device you are operating on is a producer, if added to a device you intend as a consumer this will give that device producer functionality |
| `removeService`        | This removes the service from the producer      |
| `initConsumer`         | This initiates the device as a consumer, which enables it to find services, negotiate prices, make payments and receive services |
| `initProducer`         | This initiates the device as a producer / or initialises the devices producer capability |
| `getDevice`            | This is able to provide back details of the the current device that the SDK is running on, and it credentials / information |
| `startServiceBroadcast`| This enables the producer device to start broadcasting itself via UDP broadcast over the network to notifiy devices it is available to be consumed      |
| `stopServiceBroadcast` | This method stops the SDK from broadcasting the current service messages that it is broadcasting |
| `deviceDiscovery`      | This enables the consumer device to discovery other devices (producers) on the network that are UDP broadcasting |
| `requestServices`      | Get a list of services that are avaialble from the broadcasting device |
| `getServicePrices`     | This is used by the consumer to get the list of prices associated with a particular serviceId |
| `selectService`        | Selection of a service is performed by the consumer, providing details of the service, the amount and at what price point it wants to purchase the service     |
| `makePayment`          | This allows the consumer to request a payment be made at the producer device, by providing the total price response object as the request. The producer will then make the payment (or attempt to) and send back a Payment Response detailing whether it was successful or not    |
| `beginServiceDelivery` | This begins the service delivery, and is requested by the consumer, and will proceed as long as the correct information is provided to the producer. If the correct credentials are passed through, then the producer will start releasing the service known as a 'trusted trigger'   |
| `endServiceDelivery`   | This ends the service delivery, a request initiated by the consumer |