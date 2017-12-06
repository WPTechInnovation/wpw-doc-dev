# Frequently asked questions
During the last Worldpay Within Hackthon, we identified some commonly-asked questions.
## 1. How do I find my producer amongst everyone else's on the network?
### What is the problem?
When you run your consumer, it might fail because it is finding the first producer on the network and wrongly assuming that it is your one!
### How do I solve it?
First, make sure your device name is unique.  In the examples below we use **"UniqueProducerName"**, but make sure you use something unique to your team or solution.
Here is one way to do it (another way is to filter the list of discovered devices by device name or device description):
#### Node.js
Replace:

`client.deviceDiscovery(10000, function (err, response) {...})`

With:

`client.searchForDevice(10000, "UniqueProducerName", function (err, response) {...})`

#### Python
Replace:

`wpw.deviceDiscovery(10000)`

With:

`oneSvcMsg = wpw.searchForDevice(10000, "UniqueProducerName")`

#### Java
Replace:

`Set<WWServiceMessage> devices = wpw.deviceDiscovery(10000);`

With:

`WWServiceMessage device = wpw.searchForDevice(10000, "UniqueProducerName");`

#### Go
Replace:

`serviceMessages, err := wpw.DeviceDiscovery(10000)`

With:

`serviceMessage, err := wpw.SearchForDevice(10000, "UniqueProducerName")`

#### C# .NET
Replace:

`WPWithinService.DeviceDiscovery(10000).ToList();`

With:

`WPWithinService.SearchForDevice(10000, "UniqueProducerName");`

## 2. I still can't find my producer. Why?
It could be that you're not waiting long enough for the producer to broadcast its message. The SDK broadcasts the producer message every 5000 milliseconds (that's every 5 seconds). So this means that your consumer has to be searching for the device for more than 5 seconds to ensure that it finds it.
If this is too long for you, and you're at a hackathon, come and talk to a mentor. Else, [email us](mailto:innovation@worldpay.com).

## 3. I've tried that but I still cannot find my producer.

!!! note

    This issue has mostly been found on Windows devices.

If none of your consumers can see a broadcasting producer then check to see which network interface the producer is broadcasting on.
The SDK will always broadcast on the first available network adapter.  So, for example, if you're using the Wireless network but your first adapter when you list the interfaces is **eth0**, then your broadcasts will be on **eth0** and *not* on the **wlan0** or any other wireless adapter.
To fix this, the easiest thing to do is to disable the unused adapter so that your wireless adapter is the first one. Alternatively you can modify the routing table so that **255.255.255.255** goes to the right adapter.

## 4. Can I change the operating system on our Raspberry Pi?
Our Raspberry Pis come pre-loaded with Raspbian, but during the hackathon you can choose whichever operating system you'd like (as long as it works on a Raspberry Pi!).

## 5. How can I see what I'm actually doing on my Raspberry Pi?
We'd recommend you use [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/). We used it at the Romania Hackathon and it worked well.

## 6. What currency should I use?
We'd recommend you use GBP for now.

## 7. Why can't I get the .NET SDK to work on my Raspberry Pi?
It doesn't work yet, but we're looking to get it working.
