![](https://raw.github.com/oanda/apidocs/master/images/oanda_header.png)
=========

Now you can build applications, or even entire companies, on top of our award winning 
currency trading platform, [fxTrade](http://fxtrade.com) with the OANDA REST API.

What can I do with the OANDA REST API?
--------------------------------------

Our REST API gives you full access to our online Forex trading platform in real time.  You can:

* Get real-time (up to the millisecond) currency rates on over 90 pairs, including precious metals and CFDs
* Retrieve historical currency rates going back over ten years
* Open, close and modify trades on a customer trading account
* Monitor the forex market for changes in real-time, 24 hours a day

What can I build?
-----------------

[OANDA](http://www.oanda.com) is a leading forex broker enabling you to trade over 90 currency pairs, metals, and CFDs. Everything you ask for is live and real-time.  The only limit is your imagination.  If you have an idea for a product or company
built on top of our platform we want to help!  You could:

* Build a full fledged trading app on our platform
* Create a service that provides exchange rates for eCommerce companies
* Start a business to hedge currency risks for other companies
* Implement high frequency trading algorithms that make money while you sleep
* Create a social, big data, mobile mashup targeted at disrupting the Gen Y crowd
* Build a "Chart Chat" service that combines our chart data with the stock twits api

Try it!
-------

<table style="border:1px solid lightgray">
	<tr>
		<td style="background-color:#EEEEEE; padding:15px">
		Issue the following GET request using your favourite HTTP client, or just click on the link.  The response will tell you what price EUR/USD is currently trading at.  Seriously, try it out.
		<br/><br/>
		<a href="http://api-sandbox.oanda.com/v1/instruments/EUR_USD/price">http://api-sandbox.oanda.com/v1/instruments/EUR_USD/price</a>
		<br/><br/>
		You'll see the currency pair you requested, the time you made the request (in epoch time), the bid price, and the ask price.  All responses are in JSON.
		</td>
		<td style="background-color:#CCC"><img src="https://raw.github.com/oanda/apidocs/master/images/box.png" /></td>
	</tr>
</table>

How do I start?
---------------

* Read the [Getting Started Guide](https://github.com/oanda/apidocs/blob/master/sections/getting_started.md)
* Try some [Sample Code](https://github.com/oanda/apidocs/blob/master/sections/code_samples.md)
* Browse the [Reference Documentation](https://github.com/oanda/apidocs/blob/master/sections/reference.md)

Disclaimer: The OANDA API is currently available for use in our developer sandbox, where you are free to develop and test your apps.  To use the API with production accounts, please email us at api@oanda.com or visit [developer.oanda.com](http://developer.oanda.com).

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/08c4e77e4cb54028197e21a0923e9311 "githalytics.com")](http://githalytics.com/oanda/apidocs)

