# Instructions for Breakouts for Week 12

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.

## Breakout 1 - Ethics of tracking users and indexing "news" behind paywalls

In the asynch and labs, we learned about cookies and how companies use cookies to track users:

* Users do not have to be logged in to be tracked

* Cookies can be valid for days, weeks, months

* Rebooting your computer does not clear cookies

* Due to privacy laws many websites give you the option to turn off cookies

* If you turn off cookies, the website may not function properly or allow you to use certain features

* Search engines pass along tracking cookies in links and sell your data based on tracking cookies

* Companies that make search engines also make browsers.  No surprise that it's so difficult to delete tracking cookies.

* When you login to any account, that company can match tracking cookies and sell your data to websites you visited but didn't create accounts with

* DNS is not encrypted (unless you have setup to use an encrypted DNS server) so your ISP knows every website you have visited.  NOTE: this is a hot topic and may change in the future

* Even if you use a VPN, which frequently gives you a new IP address, when you login to a website, that website can report your data linked to the IP address.  It will be short lived, and reduce your exposure, but still can allow them to harvest data.

* "News" is given a special place in search engines, especially in the era is disinformation, "fake news", etc.  However, search engines will bring back "news" that is behind a paywall.

Discuss the following from an ethical standpoint:

* Should websites be allowed to limit functionality if you don't accept cookies?

* Should websites that you have an account with (and login to) sell your personal data to other companies?

* Should websites that you have an account with (and login to) be allowed to harvest tracking cookies from search engines and sell them with your personal data?

* Should search engines be allowed to pass tracking cookies in links to other companies?

* Should search engines be allowed to track and sell you search history to other companies?

* Should search engines be allowed to present "news" results that are behind a paywall?  Is "news" behind a paywall really legitimate news?

* Should search engine companies be allowed to make browsers?  Or should there be a law that is they do, they have to make it really easy to erase tracking cookies?

* Should ISPs be allowed to track and sell your DNS lookup history to other companies?

* Should DNS be required to be encrypted?


## Breakout 2 - Being a professional, respectful user of APIs

In the asynch and labs, we learned about users can negatively affect servers by doing such things as:

* Repeatedly connecting, disconnecting, connecting, disconnecting.  Each connection has huge overhead at the TCP/IP level.

* Repeatedly logging on / logging off.  Each logon and logoff has huge overhead for the server.

* When a server goes down (as all servers do), repeatedly hammering the server with connection or login requests in a tight loop.

* Ditto for scheduled maintenance on servers (as all servers have downtime for scheduled maintenance).

* Not respecting published, known rate limits.  

* When getting a rate limit response code ignoring it and continuing to hammer the server with API requests

In most cases, this is just basic laziness and/or incompetence on the part of the programmer, and not done with malice or criminal intent.  However, it is still unethical and illegal if you are causing damage to the server, and can subject the programmer to civil lawsuits for damages and/or criminal charges.

Discuss some best practices for being a professional, respectful, lawful user of APIs.

Hints: Python and most programming languages have a sleep() function which can be used to pause execution for seconds and/or fractions of seconds, for example: 0.1, 0.33, 0.5, 0.66, 1.0, 1.33, 2.0, 2.66, etc.

Other related areas:

* While screen scraping is generally considered unethical (and in most cases illegal), if we have permission to screen scrap legally, what of the best practices would apply?

* With regards to database servers (or other servers), what of the best practices would apply?
 
## Breakout 3 - Designing a scale out web server

In this scenario, assume we are a startup company with a new product:

* We only have 1 product with a few minor variations, such as color

* The product is a new innovation, unique, the first of it's kind, utility patent pending

* The product is for a common problem that a lot of people have

* We have an "explainer video" on our website that demonstrates the common problem and how the product solves it

So far, sales have been good at a few hundred per day.  

For the main website, we have a WordPress website.  We chose WordPress because it's super easy to use, much like a word processor, and allowed us to build a nice website and to easily update it with press releases, notices of public demonstrations, etc.  It also allows us to server the explainer video.  WordPress has a downside.  WordPress is 100% dynamic content, so it cannot by nature handle a large number of visitors at the same time.  

For the sales website, we are using a 3rd party online store that we link to from WordPress when customers get ready to buy.  From the customer perspective, the 3rd party online store is oriented towards stores with lots of products with lots of variations per product.  So, it looks a bit strange to customers, such as having a "showcase" of 1 product, but most customers probably understand that we are using a generic store product.  The payment processing is very easy to use and very secure backed by a big name.  From the company perspective, the online store software is wonderful. It allows us to do inventory, fullfillment, returns, backorders, payments, etc.   The online store software has another big advantage: it can scale up well to handle a really large number of customers at the same time.  

We tried out for one of those TV shows where ordinary people with startups, especially innovative products, pitch them to extremely successful entrepreneurs in hopes of getting an investment and the knowledge and connections of an extremely successful entrepreneur.   The TV show accepted our company and we are scheduled to film in a few weeks and then be shown on TV a few weeks after that.  The TV show warned us that the exposure will cause our website to receive possibly million of customers hitting our website to check out our product.  

Discuss how you would prepare for the possibility of millions of visitors hitting the website in a few weeks (short term perspective):

* Should we keep WordPress or use something else such as a static website using Bootstrap?

* What would be the advantages of Bootstrap over WordPress? Disadvantages?  Do we have a choice?

* Should we use a CDN?  If so what should we put into CDN?

* Where should we host the video?  CDN?  3rd party niche video hosting?

* Should we keep the 3rd party online store or develop our own?

Discuss the same with a long term perspective, say months out after we have appeared on the TV show.


## Breakout 4 - Best practices for providing data to users

In the asynch and labs, we discussed several ways to give data to users:

* Screen scraping

* API

* Downloading files of data

* Sneakernet

Discuss for each of these best practices of when we should use the method to provide data to users.



