---
layout: post
type: post
title:  Simple Bitcoin Tracker
permalink: posts/simple-bitcoin-tracker
# All dates must be YYYY-MM-DD format!
date: 2018-03-05
labels:
  - Python
  - Bitcoin
---

<img class="ui tiny left circular floated image" src="../images/bitcoin.png">
Ever feel tempted to check that Bitcoin price again? Ever wanted to automate it so you can track prices yourself, or even use it for some analysis? Here is a *very* simple way of using Python to grab the price of BTC from [blockchain.info](https://blockchain.info).

As it turns out, there are [quite a lot](https://blockchain.info/q) of fun things that blockhain can enable you to do without much effort. For this script however, we are going to keep it simple. Say you want the most recent market price of Bitcoin. Head over to [blockchain's ticker](https://blockchain.info/api/exchange_rates_api), where you can convert the current price in BTC to ~20 different currencies. For this script, let's stick with USD.

The first thing we want to do is call the URL with python. Let's do that now:
{% highlight python %}
from urllib.request import urlopen
link = "https://blockchain.info/ticker"
raw_data = urlopen(link)
{% endhighlight %}

Awesome! But now we want to convert it to a JSON structure ([JavaScript Object Notation](https://en.wikipedia.org/wiki/JSON)) for easier handling. And while we are at it, let's filter the USD parameter.

{% highlight python %}
json_data = json.load(raw_data)
price = str(json_data["USD"]["last"])
print("$"+str(price))
{% endhighlight %}

This last block of code will convert the data from [blockchain's ticker](https://blockchain.info/api/exchange_rates_api), and convert the most recent price to USD.

And that's it! You've now taken your first step toward tracking bitcoin prices.
