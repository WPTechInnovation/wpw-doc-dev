The Java implementation for the Worldpay Within IoT payment SDK. This SDK enables smart devices to discover each other, negotiate a price for services, make a payment (through Worldpay) for services, and then consume services via a **trusted trigger**. For an overview, see [Home](index).

## Prerequisites

Before you get started:

* 	Install Java JDK 1.8 on your systems.
* 	Install [Apache Maven](https://maven.apache.org/) and add it to PATH.
*   Create an account with [Worldpay Online](https://online.worldpay.com) so that you can generate your own test API key. You'll replace the Worldpay test keys with your own in the SDK.

!!! warning

    Make sure you only use test API keys.

## Get started
1. 	Clone the repository: `git clone https://github.com/WPTechInnovation/wpw-sdk-java.git`
2. 	Change directory: `cd wpw-sdk-java`
3. 	Run `git submodule update --init --recursive`
4. 	Then build it with maven using the default goal: `mvn`

## Run the examples

You can try the examples by running them in two different console windows. Or, if you're installing on two separate devices, they must be one the same network that allows UDP broadcast traffic. Examples included in the repo are the sample projects: **sample-consumer**, **sample-producer** and **sample-producer-callbacks**. To run them you need to:

1.   In the first window, run the consumer JAR.
  *		`cd sample-producer-callbacks`
  * 	`java -jar target/sample-producer-callbacks-<version>-alpha.jar`
2.   Simultaneously run the producer JAR.
  *		`cd sample-consumer`
  *		`java -jar target/sample-consumer-<version>-alpha.jar`
3.   The two smart devices should communicate with each other and make a payment.

The car-example and car-charger are Spring boot projects that start a webservice on **localhost:80** and **localhost:8000**. Those ports should be free if you want to run them. To run these examples you need to:

1.   In the first window, run the car-example.
  *		`cd car-example`
  * 	`java -jar ./target/car-example-<version>-alpha.jar`
2.   Simultaneously run the car-charger.
  *		`cd sample-consumer`
  *		`java -jar ./target/car-charger-<version>-alpha.jar`
3.   In your browser, navigate to `localhost:8000`, open SmartCar UI page in one tab and Producer UI page. Set the battery level by touching the green bar and begin charging by pressing the "Charge the battery" button.

## See the payments

Once the devices have successfully communicated with each other to make a payment, you can check to make sure that your devices are successfully making and receiving payments.

### If you used your own test API keys

1.  Login to [Worldpay Online](https://online.worldpay.com).
2.  You'll see your dashboard. Scroll down and you should see the payment within your **Recent Orders**.

### If you've used Worldpay's own test API keys

1.  Login to [Worldpay Online](https://online.worldpay.com).
2.  Got to **Settings > API keys** and get your test keys.
3.  Replace the keys in the producer Java files.
4.  Re-run the examples and you should see the payments coming through on the Worldpay Online payments dashboard.

## Debugging

If you're having trouble, you can contact us at [Innovation@Worldpay.com](mailto:innovation@worldpay.com). Alternatively, you can [raise an issue in GitHub](https://github.com/WPTechInnovation/worldpay-within-sdk/issues).

## So what's happening?

![The Worldpay Within puzzle piece](images/architecture/Architecture1.png)
<figcaption>The Worldpay Within Flows sequence diagram</figcaption>

You can see there are four phases; **Discover**, **Select**, **Pay**, and **Release**. For more information, see [Home](home).

## What IoT devices can I run this on?

Hopefully any. We've only tested this on RPi - Raspberry Pis - at the moment, but we welcome experiments on all other kinds of devices! 
!!! note
	
	The devices need to be on the same network - and that network should allow for UDP broadcast traffic. Most mobile hotspots allow this; a lot of corporate networks do not...

## Want to contribute?

If you want to contribute, clone the repository and create a branch. Once you've made your changes, create a pull request. We'll review your code, and if accepted it will be merged into the code base. It's worth checking out the [Internal Structure of Worldpay Within](internal-structure) and [Sample Service Messaging](sample-service-messaging) pages if you want to learn more about how Worldpay Within works.

You can also [raise an issue in GitHub](https://github.com/WPTechInnovation/worldpay-within-sdk/issues), or contact us directly at [Innovation@Worldpay.com](mailto:innovation@worldpay.com). 
