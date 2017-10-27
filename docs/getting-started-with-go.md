## Getting started with Go

To code against the raw Go SDK, you'll need to install Go and the Golang SDK. Alternatively, you can code against one of the multiple language wrappers, which give access to the SDK. 

The Golang SDK communicates with these other languages using RPC calls (in both directions), and the wrappers in the background interface using Thrift. This is not exposed to you as a developer; you work with the Interface layer in your language of choice. We've got SDKs in the following languages:
<div class="download">
  <a class="md-button" href="../nodejs">Node.js</a>
  <a class="md-button" href="../python27">Python</a>
  <a class="md-button" href="../java">Java</a>
  <a class="md-button" href="../dotnet">.NET</a>
</div>

## Working with Go source files
### Prerequisites
1. Install the newest [Go command line](https://golang.org/doc/install#install).
2. If you do not have it, install [git](https://git-scm.com).

## Get started
1. Create a $GOPATH environment variable: (for example, on unix do: `export GOPATH=/home/pi/go`).
2. Get Apache Thrift and use the 0.10.0 branch:
		a.	`go get git.apache.org/thrift.git/lib/go/thrift/...`
		b. 	`cd $GOPATH/src/git.apache.org/thrift.git`
    	c.	`git checkout 0.10.0`
3. 	Get the SDK: `go get github.com/WPTechInnovaion/wpw-sdk-go/...`

!!! note
	
	Make sure you ignore the rpio.go system-specific warnings.

## Running the examples
Now you've got everything set up, you're able to build the examples inside: `$GOPATH/src/github.com/WPTechInnovation/wpw-sdk-go/example`
Each example consists of a sample producer and a sample consumer:

*	$GOPATH/src/github.com/WPTechInnovation/wpw-sdk-go/examples/sample-consumer
*	$GOPATH/src/github.com/WPTechInnovation/wpw-sdk-go/examples/sample-producer-callbacks

To test the communication, build and run the producer:

1. 	`cd $GOPATH/src/github.com/WPTechInnovation/wpw-sdk-go/examples/sample-producer-callbacks`
2.	`go build`
3.	`./sample-producer-callbacks`

In a separate terminal window, build and run the consumer:

1.	`cd $GOPATH/src/github.com/WPTechInnovation/wpw-sdk-go/examples/sample-consumer`
2.	`go build`
3. 	`./sample-consumer`

![The output of the log files for the orchestration of the flow](images/get-started/outputoforchestration1.png)
<figcaption>The output of the log files for the orchestration of the flow.</figcaption>

![Showing the payment in online.worldpay.com](images/get-started/order-details-onlineworldpaycom.png)
<figcaption>Showing the payment in online.worldpay.com.</figcaption>

## Creating your own keys
You can do this whenever you want, but you're going to need to create your own API keys. These keys allow you to simulate payments and see the outcome, rather than just using the keys Worldpay included in their SDKs.

!!! warning

	Make sure you only use test keys.

To add your own test API keys:

1. 	Login to [Worldpay Online](https://www.online.worldpay.com).
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