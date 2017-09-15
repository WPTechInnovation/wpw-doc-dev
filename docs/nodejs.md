## Node.js
The Node.js implementation for the Worldpay Within IoT payment SDK. This SDK enables smart devices to discover each other, negotiate a price for services, make a payment (through Worldpay) for services, and then consume services via a **trusted trigger**. For more information, see [Home](index).

### Prerequisites

*   Before you get started, you should have [Node.js](https://nodejs.org/en/) installed on your system. We've tested this wrapper with version 6.11.1.
*   You should also have [npm](https://npmjs.com/) installed on your machine too.
*   You should create an account with [Worldpay Online](https://online.worldpay.com) so that you're able to generate your own test API key. You'll replace the Worldpay test keys with your own in the SDK. 

!!! warning
	
	Make sure you only use test API keys.

### Get started

Once you've got Node.js and npm.js, you should be good to go.

1.  Clone or download [the repository](https://github.com/WPTechInnovation/wpw-sdk-nodejs).
2.  Change to the folder `cd wpw-sdk-nodejs` (if using linux / unix).
3.  Run the following command: `npm install thrift sleep`.  
    Note: If you are using a different package manager than npm, please adjust the command accordingly.  
    (If there are issues about access rights, add sudo in front of the above command)

### Run the examples

Once you've got the repository and have changed to the right folder, you can start testing to see if it works. We'd recommend using your own test API keys for this. We've left our ones in the code, but you won't be able to see the payments with our keys.

1.  In one terminal / cmd (or on one device) run: `node example-producer-callbacks.js`.  
    (You can run `node example-producer.js` but this does not recall the producer, once it times out)
2.  In another terminal / cmd, (or on another device, on the same network) run: `node example-consumer.js`.
3.  A payment should happen. If you see the serviceDeliveryToken returned within the producer terminal/cmd, you will know that the payment was complete.

### See the payments

Once the devices have successfully communicated with each other to make a payment, you'll want to check to make sure that your devices are successfully making and receiving payments.

#### If you used your own test API keys

1.  Login to [Worldpay Online](https://online.worldpay.com).
2.  You'll see your dashboard. Scroll down and you should see the payment within your **Recent Orders**.

#### If you've used Worldpay's own test API keys

1.  Login to [Worldpay Online](http://online.worldpay.com).
2.  Got to **Settings > API keys** and get your test keys.
3.  Replace the keys in the producer files.
4.  Re-run the examples and you should see the payments coming through on the Worldpay Online payments dashboard.

### Debugging

If you get some odd error messages talking about a 'rpc-agent':

*   Try typing the following command: 'ps -e | grep rpc' to get the pid(s) of rpc-agents that are running.
*   Then do kill <pid> e.g. kill 13249234 to kill these processes.
*   Try re-running the examples

If you're still having trouble, you can contact us at [Innovation@Worldpay.com](mailto:innovation@worldpay.com) or reach out to us on our [Slack channel](iotpay.slack.com). Alternatively, you can [raise an issue in GitHub](https://github.com/WPTechInnovation/worldpay-within-sdk/issues).

### So what's happening?

![The Worldpay Within puzzle piece](images/architecture/Architecture1.png)
<figcaption>The Worldpay Within Flows sequence diagram</figcaption>

You can see there are four phases; **Discover**, **Select**, **Pay**, and **Release**. For more information, see [Worldpay Within](http://www.worldpaywithin.com).

## What IoT devices can I run this on?

Hopefully any. We've only tested this on RPi - Raspberry Pis at the moment, but we welcome experiments on all other kinds of devices! Note that they will need to be on the same network - and that network should allow for UDP broadcast traffic. Most mobile hotspots allow this; a lot of corporate networks do not...

### Want to contribute?

If you want to contribute, clone the repository and create a branch. Once you've made your changes, create a pull request. We'll review your code, and if accepted it will be merged into the code base. It's worth checkout out the [Internal Structure of Worldpay Within](internal-structure) and [Sample Service Messaging](sample-service-messaging) pages if you want to learn more about how Worldpay Within works.

You can also [raise an issue in GitHub](https://github.com/WPTechInnovation/worldpay-within-sdk/issues), or contact us directly at [Innovation@Worldpay.com](mailto:innovation@worldpay.com). You can also reach out to us on our [Slack channel](iotpay.slack.com).