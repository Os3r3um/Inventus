# Inventus

Inventus is a spider designed to find subdomains of a specific domain by crawling it and any subdomains it discovers. It's a [Scrapy](https://scrapy.org/) spider, meaning it's easily modified and extendable to your needs.

[![forthebadge](http://forthebadge.com/images/badges/fuck-it-ship-it.svg)](http://forthebadge.com)

# Demo

[![asciicast](https://asciinema.org/a/PGIeEpEwZTUdgxrolBpCjljHL.png)](https://asciinema.org/a/PGIeEpEwZTUdgxrolBpCjljHL)

# Requirements

 - Linux -- I haven't tested this on Windows.
 - Python 2.7 or Python 3.3+
 - [Scrapy](https://scrapy.org/) 1.4.0 or above.

# Installation

Inventus requires [Scrapy](https://scrapy.org/) to be installed before it can be run. Firstly, clone the repo and enter it.

```
$ git clone https://github.com/nmalcolm/Inventus
$ cd Inventus
```

Now install the required dependencies using `pip`.

```
$ pip install -r requirements.txt
```

Assuming the installation succeeded, Inventus should be ready to use.

# Usage

The most basic usage of Inventus is as follows:

```
$ cd Inventus
$ scrapy crawl inventus -a domain=facebook.com
```

This tells Scrapy which spider to use ("inventus" in this case), and passes the domain to the spider. Any subdomains found will be sent to `STDOUT`.

The other custom parameter is `subdomain_limit`. This sets a max limit of subdomains to discover before quitting. The default value is 10000, but isn't a hard limit.

```
$ scrapy crawl inventus -a domain=facebook.com -a subdomain_limit=100
```

# Exporting

Exporting data can be done in multiple ways. The easiest way is redirecting `STDOUT` to a file.

```
$ scrapy crawl inventus -a domain=facebook.com > facebook.txt
```

Scrapy has a built-in feature which allows you to export items into various formats, including CSV, JSON, and XML. Currently only subdomains will be exported, however this may change in the future.

```
$ scrapy crawl inventus -a domain=facebook.com -t csv -o Facebook.csv
```

# Configuration

Configurations can be made to how Inventus behaves. By default Inventus will ignore robots.txt, has a 30 second timeout, caches crawl data for 24 hours, has a crawl depth of 5, and uses Scrapy's AutoThrottle extension. These and more can all be changed by editing the `inventus_spider/settings.py` file. Scrapy's settings are [well documented](https://doc.scrapy.org/en/latest/topics/settings.html#aws-access-key-id) too.

# Bugs / Suggestions / Feedback

Feel free to open a new issue for any of the above. Inventus was built in only a few hours and will likely contain bugs. You can also connect with me on [Twitter](https://twitter.com/NathOnSecurity).

# License

Released under the MIT License. See LICENSE.