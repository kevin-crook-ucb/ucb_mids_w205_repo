# Unstable Network Connections

Unstable network connections will cause issues such as:

* Zoom video having a couple seconds of freeze up every once in a while, such as:  once an hour, once every couple of hours, once every 30 mintues, etc.

* Jupyter Notebooks that are connected to remote servers will lose the connection to the JN kernel.  Even a 1 or 2 second glitch is enough to cause them to lose connection.

* SSH based connections will freeze up when they lose the network connection.  Even a 1 or 2 second glitch is enough to cause them to lose connection.
  * Mac
    * ssh on the command line
    * scp on the command line
  * Windows
    * PuTTY on Windows (uses SSH)
    * WinSCP on Windows (uses SSH)
  * Linux on the Desktop, such as Ubuntu or Lubuntu
    * ssh on the command line
    * scp on the command line

## Wifi router inherent issues

If you are running a wifi router, be aware that it is wireless, it goes through the air, and anything wireless that goes through the air will ALWAYS have issue with connectivity.   Even Hollywood shows with the latest and greatest multi-million dollar equipment will have rare, but occasional glitches with wireless microphones. 

* Wifi routers have 2 main frequencies, and several channels (aka subfrequencies, side channels, subchannels).  These are shared by everone using wifi.  Everyone has wifi.  So there will always be interference.
* Wifi routers channel surf between channels to avoid interference.  When they get interference on one channel, they try to switch to another, which may take a second or two glitch.
* Apartments, condos, high rises, and other high density living areas will always have a lot more interference than free standing homes will.
* Free standing homes can still get interference from neighbors, just less impactful.
* IoT devices that use wifi often implement subsets of the wifi protocol due to low CPU and low memory or take shortcuts with wifi protocols.  Essentially they don't play well with others.  There are more and more IoT devices, so this impact is only going to get worse.
* With Covid, more and more people are home and using the Internet more and more, so intererence will only get worse.

## Best solution: hardwired Ethernet connection

By far the best solution is a hardwired Ethernet connection.  If the location of your router and the location of where you use your laptop or desktop allows for this, a less than $10 cable might solve everything.

Get a category 5 or higher Ethernet cable (RJ45). I'm not even sure they sell anything less than cat 6 these days.  You can get these on Amazon, Walmart, Target, etc.

Plug one end of the cable into your router and the other end into your laptop (desktop).

Some laptops may not have an RJ45 port.  In that case you may have to buy an adapter.  Be sure it's returnable in case it does not work.

I have used a hardwired Ethernet connection for over 5 years now for many hours per week.  I've never once had an issue with Zoom freeze ups or stability warnings, JN disconnects, SSH disconnects, etc.

When I was on wifi in a house with a big yard, I would get glitches every couple of hours.

##  Wifi best practices

If you can't easily hardwire your Ethernet connection, here are some wifi best practices to try:

* Reboot your modem and router once a week or so. If the last time your modem and router were rebooted was the last time the power went out months ago, this could be part of the problem (or even a big part of the problem).   In general, the longer a modem and router run, the more likely they are to get cumulative memory leaks, which will cause more and more glitches and unstability over time.  I make a habit of rebooting mine every Sunday night so they are fresh and ready to go for the coming week.

* Your wifi chipset and/or firmware in your laptop (desktop) may have power saving logic built into it to shutdown when not in use.  Wifi uses a lot of power. So, the thinking is to shut it down when not in use to save power, especially for laptops.  When it shuts down, it loses all connections and has to reconnect when it comes back.  The instructions may be different depending on OS, patch level, etc.  Google how to turn off power saving mode for your wifi and see if you can turn it off.

* If you cannot turn off your wifi, you may be able to buy an external wifi device that doesn't have power saving mode.  You will have to disable the built in wifi and enable the external wifi.  This may not be possible depending on the OS, patch level, etc.  Be sure it's returnable in case it doesn't work. 

* Hardwired Ethernet does not use much power at all, so typically it does not have power saving mode.  But if you are using hardwired Ethernet, you are probably not having any issues.

* Try a wifi repeater that you can put very close to your laptop or desktop.  Be sure it's returnable in case it doesn't work. 

* Try relocating your router, laptop (desktop) if practical.

## Powerline Ethernet as a second best to hardwired Ethernet

Powerline Ethernet is a way to run Ethernet over the existing electrical wiring.  It works like this:

* You plug the main Powerline device into an electrical outlet near your router.
* You plug an Ethernet cable into the main Powerline device.
* You plug the other end of the Ethernet cable into your router.
* You plug a Powerline device into an electical outlet near your laptop (desktop).
* You plug another Ethernet cable into the Powerline device.
* You plug the other end of the Ethernet cable into your laptop(desktop).

I have used Powerline for over 5 years and never once had an issue with it.

As always, make sure it's returnable in case it doesn't work for you.  The instructions say some electrical wiring configurations may not work.

The Cadelliac brand is Netgear, as they invented the technology.  Then tend to cost more.  Since Covid they have been really hard to find in stock.  They run around $115 for a pair.  Here is the one I've bought most recently:  

NETGEAR Powerline adapter Kit, 2000 Mbps Wall-plug, 2 Gigabit Ethernet Ports with Passthrough + Extra Outlet (PLP2000-100PAS)

Amazon also has some off brands as low as $50.  I haven't used them.  Here is the off brand that Amazon currently recommends:

TP-Link Powerline Ethernet Adapter Starter Kit - AV1000 Gigabit Port, Plug&Play, Ethernet Over Power, Nano Size, Ideal for Smart TV, Online Gaming, Wired Connection Only (TL-PA7017 KIT) 

## Specific to SSH, SCP, PuTTY, WinSCP: Keepalive can help, but it can also make it worse

TCP/IP has a keepalive setting that will send a keep alive packet at X second interval that you specify.   

If you have a stable network connection, you should not need to set keepalive.

Setting keepalive the keepalive can be very tricky.  It's very dependent on the network latency, stability, etc.  It can take a lot of tweaking for even the most experienced network engineers to get it tuned.

If the stability of your wifi network varies (like the neighbor logs into Zoom for a conference call and your stability goes down), then you may have to adjust the keepalive interval.

A stable network will work with any keepalive interval.

A less stable network needs a keepalive to a shorter interval, because it can recover quickly and not lose the connection.

An unstable network needs a keepalive to a longer interval, because it cannot recover quickly.  It will actually cause it to lose the connection more frequently.

In networking academies, it's not unusual for students with weeks or months of networking experience to have a lot of difficulty with keepalive tuning labs.  So, there isn't a magic easy formula to set here that will work for all cases.


For PuTTY and WinSCP on Windows, there is a keepalive interval you can set in the GUI.  Try setting it to 10 seconds as a starting point.  That will work for networks that have occasional few second glitches.   Adjuct it down or up to tweak it to see if you get better results.

For Mac or Linux Desktop (Ubuntu, etc.) you will need to create an SSH configuration file.  This can vary, so Google to find out the specifics.

## Windows VM in Cloud and connect using remote desktop

If the issue is more your ISP, and no tweaks to your wifi, router, etc. will help, or if you feel this is an easier option, you may want to create a Windows VM in the Cloud and connect using Windows remote desktop. 

If your network glitches, you will lose the Windows remote desktop connection.  It will give you an error message with an option to reconnect.  You can try reconnecting until it reconnects.  Once it reconnects the Windows VM's desktop will still be in the same state as you left it.

Typically only Windows server version will be available, and the Windows desktop verson will not be available.  Windows server is very similar, and if all you will be running is a web browser, PuTTY, WinSCP, etc. then the differences won't be that unreasonable.

The disadvantages is that you will need to pay parking feed on the Windows VM image, and when you are running the Windows VM, you will incur costs per minute.  It will cost about twice as much as Linux, as they have to pay royalties to Microsoft for Windows server.

