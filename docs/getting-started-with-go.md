### Getting started

You will at the very least need to install Go and the Golang SDK, thereafter you can code against the raw Go SDK or alternatively against one of the multiple language wrappers, which give access to the SDK. The Golang SDK communicates with these other languages using RPC calls (in both directions), and the wrappers in the background interface using Thrift, this is not exposed to you as a developer, you work with the Interface layer in your language of choice.

### The binaries (if you don't want to build from source)

Please see the releases section of GitHub for access to pre-built binaries of the RPC Agent and Dev Client apps. Both of the apps have been built for 32bit and 64bit architectures on Windows, MacOS, Linux and Linux (ARM).

While the RPC Agent can be run from anywhere it makes sense to add it to the directory of the application which will call it. The reason for this is that each application needs it own running instance of the RPC Agent and it can easily get confusing when there are multiple applications and agents deployed.

Please see the examples in both the Java and Node.JS wrappers. these examples currently hold binaries for MacOS x64\. I suggest replacing that binary with an alternate build, if required.

The dev client can really be run from anywhere as it is not coupled with anything else.

#### Usage

*   RPC Agent `./rpc-agent -configfile <filename></filename>`. Please see explanation of rpc-agent config file for further info.*   Dev Client `./dev-client`

### Install - if you want to go from the Go source files!

1.  Install Go command line
2.  Set up the environmental variables correctly; you only need to set $GOPATH, and that should be set as //, where is wherever you want the code, is /src/innovation.worldpay.com
3.  clone the repo to $GOPATH/src/innovation.worldpay.com
4.  Get the dependencies; go get github.com/Sirupsen/logrus
5.  Get the dependencies; go get github.com/gorilla/mux
6.  Get the dependencies; go get github.com/nu7hatch/gouuid
7.  Get the dependencies; go get git.apache.org/thrift.git/lib/go/thrift

### Configuration file versus command line flags

The RPC client takes command line flags e.g. -port 9091 but it can also take the flag -configfile 'conf.json' so you can specify the configuration in a config file. For example:

    {
        "WorldpayWithinConfig": {
            "BufferSize" : 100,
            "Buffered": false,
            "Framed": false,
            "Host": "127.0.0.1",
            "Logfile": "worldpayWithin.log",
            "Loglevel": "warn",
            "Port": 9081,
            "Protocol": "binary",
            "Secure": false
        }
    }

### Tutorial on running two example apps on one machine

Tutorial for running on the same machine e.g. Java (producer) and Node.js (consumer)

![The output of the log files for the orchestration of the flow](images/get-started/outputoforchestration1.png)
<figcaption>The output of the log files for the orchestration of the flow.</figcaption>

![Showing the payment in online.worldpay.com](images/get-started/order-details-onlineworldpaycom.png)
<figcaption>Showing the payment in online.worldpay.com.</figcaption>

*   Java - 9090 - Producer
*   Node.js - 9091 - consumer

1.  Each app needs to run on it's own instance of the RPC service, so run one on 9090 and the other on 9091
2.  So we're running Java off of 9090 and running node.js off of 9091
3.  Open two terminal windows
4.  Configure the rpc agent in each terminal window to run on each of the ports, in the producer window run the RPC on port 9090 and the consumer window run the RPC on port 9091
5.  Configure the java app to run on 9090 (run as the producer)
6.  Configure the node.js app to run on 9091 - in createClient in example code (run as the consumer)
7.  Run the java producer app so we're broadcasting, note that the RPC agent broadcasting will continue to run in the background whilst the java program has exited
8.  Run the node.js consumer app immediately
9.  The service discovery, price negotiation, payment and service release flows will all be twiggered, as you can see below