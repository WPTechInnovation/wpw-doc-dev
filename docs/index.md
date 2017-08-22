# Getting started

  We are an open source project, and some of our internal dev terms may spill out to the external SDK - apologies for this. But think of the SDK you download as being the API to a set of really cool services that allow smart devices to pay for services from oneanother

  What you get from the SDK you download from our git repo, is access to the API in all the supported languages (we refer this as the 'wrapper'), you will still need to get the core IoT component from the releases (we refer to this as the 'RPC-agent'). <a href="internal-structure.html">If you're interested further on the internal architectcure of the project check this out</a>.


## Get the SDK (software development kit) from the Github repository
  Please either download the repo, or clone the repo from Github, <a href="https://github.com/WPTechInnovation/worldpay-within-sdk">the github repo for Worldpay Within can be found here</a>

## Download the core Iot component

  The Iot core component is sometimes called the "RPC-Agent" (and sometimes referred to as the binaries) from the Github Repository

  1. Go to the releases page here <a href="https://github.com/WPTechInnovation/worldpay-within-sdk/releases">https://github.com/WPTechInnovation/worldpay-within-sdk/releases</a>
  2. Download the zip file entitled 'wpwithin-&lt;version_number&gt;-bins.tar.gz' e.g. wpwithin-0.4-bins.tar.gz - make sure to get the latest one though!
  3. You don't need all the files in this download! Oh no, you'll just need the ones for the computer that you are developing on, and thing (smart device) that you are going to run it on.
  4. Unzip the file rpc-agent-bins-&lt;version_number&gt;.tar.gz
  5. Choose the RPC-agent file appropriate to your Thing or development machine.

## Setup your environment Worldpay Within
  You'll need to drop the core IoT component (RPC-agent file) into the appropriate place in the SDK (or wrapper directory).

  Follow the instructions for each supported language on where to place the core IoT component (RPC-agent file) and what to call it. The instructions will also let you know if there are any other pre-requisites to install on your device before you get started.


<a class="md-button" href="https://github.com/WPTechInnovation/worldpay-within-sdk/tree/master/wrappers/java">Java</a>
<a class="md-button" href="dotnet.html">.NET</a>
<a class="md-button" href="getting-started-with-go.html">Go</a>
<a class="md-button" href="nodejs.html">Node.js</a>
<a class="md-button" href="python27.html">Python (2.7)</a>