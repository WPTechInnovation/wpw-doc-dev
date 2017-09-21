## What is Worldpay Within and what does it do

Worldpay Within is an embeddable payments agent for the Internet of Things (IoT) that can be 'plugged' into your smart device app, enabling it to discover, pay for, and consume the services of other devices. Conversely it also allows your smart device to expose services to consumer devices, receive payments for those services, and then release services to a consumer using the idea of a **Trusted Trigger**.

It is all about enabling payments in IoT, allowing smart devices to communicate with each other and exchange value for services.

### Consumers and producers
A consumer (shopper) is a smart device which is looking for services, pays for services and consumes services.

A producer (merchant) is a smart device that is able to advertise availability of it's owner services to consumers, take a payment, and release those services to the trusted consumer that made the payment.

## How could I use it?
![What Worldpay Within Does](images/the-flows/car-fuel-flow.png)
<figcaption>What Worldpay Within Does</figcaption>

The above example has a smart car looking for petrol and then paying for the service from the petrol station. The smart car "wants petrol", so has HCE (Host Card Emulation; card credentials), making it act as a Shopper. When trying to make a payment, it will connect to Worldpay and request tokenised card credentials based on the smart device it is trying to consume services from.

This token is then securely passed to the petrol pump. In this case the petrol station is the Producer, or is acting as the merchant, or HTE (Host Terminal Emulation, accepting payment), which then directly communicates with the Worldpay gateway to make a 'card on file' or 'eCommerce' payment authorisation request. With the payment authorised, the petrol station then releases the purchased service to the shopper.

The beauty of Worldpay Within is that it enables smart devices to both make *and* receive payments. In the example above, the petrol station could then go on to make payments to the oil company's smart hub which is providing the petrol.

## How the Wrapper works

![How the Wrapper Works](images/the-flows/how-the-wrapper-works.png)
<figcaption>How the Wrapper Works.</figcaption>

On the left-hand side you have the SDK, on the right-hand side you have the Wrapper, in this case the Java Core. The SDK in Golang has an RPC layer on top which is exposed via Thrift. The Java Core or Wrapper, is built up of the Thrift layer which does the RPC comms to the core SDK. The wrapper also acts as an adapter converting all the data / objects / errors into Pojos that the Java core, or the app you are building can work with.

The important thing to recognise here is that none of the Thrift layer is exposed to you as a developer, and all the RPC calls are handled for you. Essentially you are calling Worldpay Within seamlessly, managed by the Worldpay Within Wrapper in the appropriate language you are working in.

## How the wrapper and SDK work

![How the wrapper and SDK work](images/the-flows/internal-structure-3.png)
<figcaption>How the wrapper and SDK work.</figcaption>

This is another view of the SDK and the app. In this scenario there are two devices with Worldpay Within installed on them that communicate over the internet. One is the 'consumer' and the other is the 'producer', as explained above. As you go down the layers, you have the RPC layer, then the Thrift layer and finally the wrapper layer (above). The wrapper communicates with the SDK via RPC calls. What is not shown is your app will be the next layer shown on the diagram.

In this scenario, the producer is UDP broadcasting a service message, which includes its hostname, IP and UrlPrefix. Once the consumer discovers the broadcast, it is able to communicate over HTTP with the RESTful endpoint on the producer to find out what services it offers. The shopper will then continue the rest of the flow.

## What's happening inside the SDK

We have open sourced the wrappers, example apps, and the Golang SDK. For an overview, see [Home](home).

Click [here](architecture) for more information about the Worldpay Within architecture.