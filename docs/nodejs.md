The Node.js implementation for the Worldpay Within IoT payment SDK. This SDK enables smart devices to discover each other, negotiate a price for services, make a payment (through Worldpay) for services, and then consume services via a **trusted trigger**. For an overview, see [Home](index).

## Prerequisites

Before you get started:

*   Install [Node.js](https://nodejs.org/en/) on your system. We've tested this wrapper with version 8.6.0 on Ubuntu and 4.8.4 on Raspberry Pi.
*	If you do not have it, install [git](https://git-scm.com).
*   Install [npm](https://npmjs.com/) on your machine. We've tested version 5.5.1 on Ubuntu and 2.5.11 on Raspberry Pi.
*   Create an account with [Worldpay Online](https://online.worldpay.com) so that you can generate your own test API key. You'll replace the Worldpay test keys with your own in the SDK. 

!!! warning
	
	Make sure you only use test API keys.

## Get started

Once you've got Node.js and npm.js, you should be good to go.

1.  Clone or download [the repository](https://github.com/WPTechInnovation/wpw-sdk-nodejs): `git clone https://github.com/WPTechInnovation/wpw-sdk-nodejs.git`
2.  Change to the folder `cd wpw-sdk-nodejs`
3. 	Update the submodules: `git submodule update --init --recursive`
4. 	Download the required modules: `npm install`

!!! note
		
	If you are using a different package manager than npm, please adjust the command accordingly.  
	(If there are issues about access rights, add `sudo` in front of the above command)

## Run the examples

Now you can start testing to see if it works. We'd recommend using your own test API keys for this. We've left ours in the code, but you won't be able to see the payments with our keys.

1.  In one terminal/cmd (or on one device) run: `node example-producer-callbacks.js`
2.  In another terminal/cmd, (or on another device, on the same network) run: `node example-consumer.js`
3.  A payment should fire. If you see the `serviceDeliveryToken` returned within the producer terminal/cmd, you'll know that the payment was complete. This payment will happen with our test keys, so you won't be able to see the payment.

## Creating your own keys
You can do this whenever you want, but you're going to need to create your own API keys. These keys allow you to simulate payments and see the outcome, rather than just using the keys Worldpay included in their SDKs.

!!! warning

	Make sure you only use test keys.

To add your own test API keys:

1. 	Login to [Worldpay Online](https://online.worldpay.com).
2. 	Go to **Settings**.
3. 	Then click **API Keys**.
4. 	Grab your **Service key** and **Client key**. They'll look something like this: `T_S_fd00db67-b77b-4d6e-1a2a-45f65123f795`.
5. 	Find the config folder of the SDK and find the producer JSON files.
6. 	Add your Service and Client keys:
	1.	The `pspConfig.merchant_client_key` and `pspConfig.hte_public_key` must have the same key.
	2.	The `pspConfig.merchant_service_key` and `pspConfig.hte_private_key` must have the same keys.
7. 	Save your work.

Once you've added your own test keys, you'll be able to start testing your payments.

## Seeing your payments
Now that you've added your own test keys to the producer config files, you can start testing your payments. Refer to the **Run the examples** topic for more information about this.

To see your test payments:

1. Login to [Worldpay Online](https://online.worldpay.com).
2. On the homepage, scroll down to the **Recent Orders** section.
3. Your payments are here. You'll be able to see:
	1.	**Order Code** - The order code
	2.	**Customer Order Code** - The customer's order code
	3.	**Gross Amount** - The gross amount of the order
	4.	**State** - The state of the order. For example, SUCCESS or AUTHORIZED
	5.	**Payment type** - The type of payment. For example, ECOM
	6.	**Order type**  - The type of order. For example, VISA_CREDIT or VISA_DEBIT
	7.	**Updated** - The last time the payment state changed

For more information, refer to the [Worldpay Online documentation](https://developer.worldpay.com/jsonapi/docs).

## Debugging

If you're having trouble, you can contact us at [Innovation@Worldpay.com](mailto:innovation@worldpay.com). Alternatively, you can [raise an issue in GitHub](https://github.com/WPTechInnovation/worldpay-within-sdk/issues).

### OS-specific issues
On Debain 14, the default version of Node.JS is 0.10. Distributions based on it such as Raspbian and Ubuntu would be impacted as well. To install Node.JS 8.x:

1. In a terminal, run `curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -`
2. Then do `sudo apt-get install -y nodejs`

To install Node.JS 4.x (Long Time Support release):

1. In a terminal, run `curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash-`
2. Then do `sudo apt-get install -y nodejs` 

## So what's happening?

![The Worldpay Within puzzle piece](images/architecture/Architecture1.png)
<figcaption>The Worldpay Within Flows sequence diagram</figcaption>

You can see there are four phases; **Discover**, **Select**, **Pay**, and **Release**. For more information, see [Home](index).

## What IoT devices can I run this on?

Hopefully any. We've only tested this on RPi - Raspberry Pis - at the moment, but we welcome experiments on all other kinds of devices! 
!!! note
	
	The devices need to be on the same network - and that network should allow for UDP broadcast traffic. Most mobile hotspots allow this; a lot of corporate networks do not...

## Want to contribute?

If you want to contribute, clone the repository and create a branch. Once you've made your changes, create a pull request. We'll review your code, and if accepted it will be merged into the code base. It's worth checking out the [Internal Structure of Worldpay Within](internal-structure) and [Sample Service Messaging](sample-service-messaging) pages if you want to learn more about how Worldpay Within works.

You can also [raise an issue in GitHub](https://github.com/WPTechInnovation/worldpay-within-sdk/issues), or contact us directly at [Innovation@Worldpay.com](mailto:innovation@worldpay.com). 