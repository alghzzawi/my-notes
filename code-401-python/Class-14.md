# Web Scraping

#### Web scraping could be a method to automatically get to and extract large sums of information from a website which can spare a huge amount of time and effort. In this article, we'll go through a straightforward example of how to automate downloading hundreds of files from the Unused York MTA. Usually a incredible work out for web scraping tenderfoots who are looking to get it how to web scrape. Web scraping can be somewhat scaring, so this instructional exercise will break down the process of how to go almost the process.


### New York MTA Data

#### We will be downloading turnstile data from this site:

    http://web.mta.info/developers/turnstile.html

#### The turnstile data is collected every week from May 2010 to the present, so there are hundreds of .txt files on the site.

#### Important notes about web scraping:

1. #### Read through the website’s Terms and Conditions to understand how you can legally use the data. Most sites prohibit you from using the data for commercial purposes.

2. #### Make sure you are not downloading data at too rapid a rate because this may break the website. You may potentially be blocked from the site as well.


### Python Code

#### We start by importing the following libraries.

    import requests
    import urllib.request
    import time
    from bs4 import BeautifulSoup

#### Next, we set the url to the website and access the site with our requests library.

    url = 'http://web.mta.info/developers/turnstile.html'
    response = requests.get(url)

#### If the access was successful, you should see the following output:

    In [1]: response #200 means it went through
    out[1]: <Response [200]>

#### Next we parse the html with BeautifulSoup so that we can work with a nicer, nested BeautifulSoup data structure. If you are interested in learning more about this library, check out the BeatifulSoup documentation.

    soup = BeautifulSoup(response.text, “html.parser”)

<br>

#### We use the method .findAll to locate all of our <a\> tags.

    soup.findAll('a')

#### This code gives us every line of code that has an <a\> tag. The information that we are interested in starts on line 38 as seen below. That is, the very first text file is located in line 38, so we want to grab the rest of the text files located below.

<img src='./img/subset a.png'>

#### Next, let’s extract the actual link that we want. Let’s test out the first link.

    one_a_tag = soup.findAll(‘a’)[38]
    link = one_a_tag[‘href’]


## Make requests through Proxies and rotate them as needed

#### When scraping, your IP address can be seen. A site will know what you're doing and in case you're collecting data. They might take data such as – client designs or encounter in the event that they are first-time users. Multiple requests coming from the same IP will lead you to induce blocked, which is why we ought to utilize numerous addresses. When we send requests from a proxy machine, the target website will not know where the initial IP is from, making the detection harder. Create a pool of IPs that you just can use and use irregular ones for each ask. At the side this, you have got to spread a modest bunch of requests over numerous IPs. 

#### There are a few methods that can alter your outgoing IP.

* #### TOR

* #### VPNs

* #### Free Proxies

* #### Shared Proxies – the least expensive proxies shared by many users. The chances of getting blocked are high.

* #### Private Proxies – usually used only by you, and lower chances of getting blocked if you keep the frequency low.

* #### Data Center Proxies, if you need a large number of IP Addresses and faster proxies, larger pools of IPs. They are cheaper than residential proxies and could be detected easily.

* #### Residential Proxies, if you are making a huge number of requests to websites that block to actively. These are very expensive (and could be slower, as they are real devices). Try everything else before getting a residential proxy.