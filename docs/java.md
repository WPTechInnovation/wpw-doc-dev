The Java implementation for the Worldpay Within IoT payment SDK. This SDK enables smart devices to discover each other, negotiate a price for services, make a payment (through Worldpay) for services, and then consume services via a **trusted trigger**. For an overview, see [Home](index).

## Prerequisites

Before you get started:

*   Install the Java SDK on your system, and prefereably a Java IDE (Integrated Development Environment) - our dev's love Netbeans, Eclipse and IntelliJ, but it's your choice; we've provided a maven script to build everything. 
*   Create an account with [Worldpay Online](https://online.worldpay.com) so that you can generate your own test API key. You'll replace the Worldpay test keys with your own in the SDK.

!!! warning

    Make sure you only use test API keys.

## Get started

1. Download the [repository](https://github.com/WPTechInnovation/wpw-sdk-java).
2. Get the dependent repos by typing `git submodule init` and then `git submodule update --recursive --remote`
 
## Run the examples

You can try the examples by running them in two different console windows. Or, if you're installing on two separate devices, they must be one the same network that allows UDP broadcast traffic. Make sure you're using rhw Online Worldpay (OWP) files rather than the Worldpay Total (WT) ones.

*   In the first window, run the consumer JAR
*   In the second window, run the producer JAR
*   The two smart devices should communicate with each other and make a payment

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

If you get some odd error messages talking about a rpc-agent:

*   Try typing the following command: `ps -e | grep rpc` to get the pid(s) of rpc-agents that are running.
*   Then do `kill <pid>`, such as `kill 13249234` to kill these processes.
*   Try re-running the examples

If you're still having trouble, you can contact us at [Innovation@Worldpay.com](mailto:innovation@worldpay.com). Alternatively, you can [raise an issue in GitHub](https://github.com/WPTechInnovation/worldpay-within-sdk/issues).

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
