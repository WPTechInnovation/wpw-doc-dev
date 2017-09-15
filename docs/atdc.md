## Setting up your Pi for Worldpay Within @ ATDC hackathon

### Quick start

1.  Get a pre-provisioned SD card, which should put you on the 'Connectify' network
2.  The go, and RPi Python wrapper should be ready to go, the RPC agent is available for you to provision the other wrappers too. Speak to Conor or Kevin for help with this

### How to see my transactions on Worldpay total?

Don't get this confused with the global/european system, for this hackathon you can view the transactions through the virtual terminal here: [terminal.demo.securenet.com](https://terminal.demo.securenet.com) - login credentials from Clint

### Android wrapper?

We have not developed an Android wrapper, however there is one in development on the 'native-interface' branch, which allows you to call into the RPC-agent/SDC by going directly without need for RPC. This partially works, and is not certified, and is on older code, but you are free to experiment with this.

Probably better is to use a 'proxy' Pi as your consumer, and expose each step / feature as a simple RESTful api, which the Android can call to orchestrate the flow, the business logic can then all be included in the Android app, with the Worldpay Within SDK running on the Pi. Please discuss with Conor for any more help on this topic

### Self provision the Raspberry Pi

1.  Get the Pi to the provisioning team so they can get it on the Connectify network, or choose Connectify with password: wpt1c123
2.  You should now be able to do the rest yourself, by ssh-ing to the device at `ssh pi@wppi##` e.g. for the Pi number 40: `ssh pi@wppi40`˜∏
3.  Change to the directory with the Worldpay Within SDK in it: `~/go/src/github.com/wptechinnovation/worldpay-within-sdk/`
4.  Change to the develop branch `git checkout develop`
5.  Pull the latest code `git pull`
6.  Get the latest RPC-agent for Raspberry pi `wget http://bit.ly/wpwlinarm32`

#### How to setup the python 2.7 wrapper

1.  If you want to use the 2.7 python wrapper, then download apache thrift 0.10.0 (latest version)
2.  Extract it and change to the `lib/py/` directory
3.  Run the following command `sudo python setup.py install`
4.  Place the RPC-agent in the python wrapper directory: `~/go/src/github.com/wptechinnovation/worldpay-within-sdk/wrappers/python_2-7`
5.  Rename to `rpc-agent`, run `sudo chmod ugo+x rpc-agent`
6.  Test run it with `./rpc-agent -port 9018`, then close it using ctrl-C and make sure it is killed using `ps -e | grep rpc-agent` and if it's still running do a `Kill <process-id>`
7.  You're now ready to provision your device with your securenet credentials, and the run the example apps

Click [here](python27) for more information about the Python wrapper.

#### How to setup the other wrappers

If you want to use the Java, Node.js, Python 3 or .Net wrappers then here is further information about the setup:

1.  Java wrapper - talk to Conor or Kevin, you'll need to setup a project with the source and pull in the libs
2.  [Node.js](nodejs) - or talk to Conor
3.  Python 3 - talk to Kevin (HINT: once you've got this wrapper, theres a self contained setup.py)
4.  [.net wrapper](dotnet) - or talk to Conor or Kevin

### Environment variables for accessing RPC-agent

Note that with various support on the wrappers (2.7 python does not yet support), you can use an environment variable for finding your rpc-agent

Set the environmental variable `WPW_HOME` which is the path to the WPWithin Home. Binaries should go in the $WPW_HOME/bin directory.

For the node.js and Java wrappers, first check if `$WPW_HOME` is set. If so, the wrappers launch the appropriately named rpc-agent from `$WPW_HOME/bin/`. If not then look for the RPC agent in the `./rpc-agent-bin/` directory. E.g. for Mac OS (go with it that it's called amd64...):

*   `$WPW_HOME/bin/rpc-agent-darwin-amd64`
*   `./rpc-agent-bin/rpc-agent-darwin-amd64`

### Deploying the Java wrapper to the Pi

1.  Assuming you have the consumer or producer app setup in your favourite IDE
2.  Do a clean build of the consumer app to generate a dist directory
3.  Create a `distribtopi` directory
4.  Copy the contents of `dist` into the `distribtopi`
5.  In this directory create a subdirectory called `rpc-agent-bin`
6.  From the latest release, get the Raspberry pi rpc-agent `rpc-agent-linux-arm32`
7.  Zip up this package and put onto your Pi however you prefer
8.  Unzip on the Pi
9.  Run the program with `java -jar <Name-of-your-app>.jar`
10.  Any issues you can't debug, come and have a chat with Kevin or Conor we're happy to help

### Support

Any issues with setting up Worldpay Within (and the wrappers) on your Raspberry Pi or Development machine please reach out to Conor Hackett or Kevin Gordon, who will be able to support you over this weekend. They've familiar with a few gotchas, and will be able to get you up and running in no time!

Also you can join us on slack here: [https://wpwithin-slack-in.herokuapp.com](https://wpwithin-slack-in.herokuapp.com)