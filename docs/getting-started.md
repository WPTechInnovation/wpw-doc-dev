Worldpay Within is an open source project that provides a downloadable SDK that can be used as an API to provide a set of really cool services. For example, one device can pay for services from another.

The SDK is available in a number of supported languages that we refer to as "wrappers". While these provide the development kit to make the devices work in the expected way, you still need to get the core IoT componet from the releases - we refer to this as the "RPC-agent".

More information about the inner workings of the internal architecture can be found in the [Internal architecture](internal-structure) page.

### 1. Get the SDK (software development kit) from the Github repository

You'll need to either download or clone the SDK from the GitHub repository, which you can do [here](https://github.com/WPTechInnovation/worldpay-within-sdk).

### 2. Download the core Iot component

You'll then need the core component, which is sometimes called the "RPC-agent". You'll get these from the GitHub repo:

1.  Go to the [release page](https://github.com/WPTechInnovation/worldpay-within-sdk/releases).
2.  Download the latest version of the **wpwithin-<version_number>-bins.tar.gz** zip file. For example, **wpwithin-0.4-bins.tar.gz**.
3.  You just need to download the files you need for the computer and device you're going to develop on and use.
4.  Unzip the file **rpc-agent-bins-<version_number>.tar.gz**.
5.  Choose the RPC-agent file appropriate to your Thing or development machine.

### 3. Setup your environment Worldpay Within

You'll need to drop the core IoT component (RPC-agent file) into the appropriate place in the SDK (or wrapper directory).

Follow the instructions for each supported language on where to place the core IoT component (RPC-agent file) and what to call it. The instructions will also let you know if there are any other pre-requisites to install on your device before you get started.

<div class="download">
  <a class="md-button" href="nodejs">Node.js</a>
  <a class="md-button" href="python27">Python</a>
  <a class="md-button" href="java">Java</a>
  <a class="md-button" href="dotnet">.NET</a>
  <a class="md-button" href="getting-started-with-go">Go</a>
</div>