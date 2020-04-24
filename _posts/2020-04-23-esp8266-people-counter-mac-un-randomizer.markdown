---
layout: post
title:  "esp8266 people counter MAC (un)randomizer"
date:   2020-04-22 18:16:26 +0200
categories: people-counter
---
Recent versions of mobile operatig systems like [Android 10](https://www.android.com/android-10/) uses a new privacy setting to avoid tracking, randomizing the last 3 bytes of the device MAC address.

To overide this, I added the new `mac_randomizer_mode` to the MQTT people counter script. This mode marks as the same MAC address if the first 3 bytes of the MAC address appears in the last 15 minutes (you can change the threshold). It's not a perfect solution, but the chances to get the same first 3 bytes (often related to a brand specific model series) in a short time window within a few meters distance from the detector device are very few.


{% highlight python %}
if mac_randomizer_mode:
			mac_half=mac[0:6]
			last15mResults = influxclient.query('SELECT activity FROM traffic_accounting WHERE mac =~ /^'+mac_half+'/ and time > now() - 15m;')
		else:
			last15mResults = influxclient.query('SELECT activity FROM traffic_accounting WHERE mac = \''+mac+'\' and time > now() - 15m;')
{% endhighlight %}


Check out the [esp8266 people counter project repo](https://github.com/ferrithemaker/esp8266-wifi-people-counter) for more information.

