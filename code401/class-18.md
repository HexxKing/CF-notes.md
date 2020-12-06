# [Web Scrape with Python in 4 minutes](https://towardsdatascience.com/how-to-web-scrape-with-python-in-4-minutes-bc49186a8460)
- Important notes about web scraping:
  - Read through the website’s Terms and Conditions to understand how you can legally use the data. Most sites prohibit you from using the data for commercial purposes.
  - Make sure you are not downloading data at too rapid a rate because this may break the website. You may potentially be blocked from the site as well.
- The first thing is to figure out where we can locate the links to the files we want to download inside the multiple levels of HTML tags.  
  - there is a lot of code on a website page and we want to find the relevant pieces of code that contains our data. 
  - On the website, right click and click on “Inspect”. This allows you to see the raw code behind the site.
  - If you click on the arrow in the top left of the console, and then click on an area of the site itself, the code for that particular item will be highlighted in the console.
  - you will find that the <a> is used for hyperlinks.
- import your libraries 
  - `import requests`
  - `from bs4 import BeautifulSoup`
- assign the url to the website and access the site with our requests library.
  - `url = "http://blahblahblah"`
  - `response = requests.get(url)`
- To test the connection, input : `response` and the output should be `200`
  - 200 means it went through successfully
- Next we parse the html with BeautifulSoup so that we can work with a nicer, nested BeautifulSoup data structure.
  - `soup = BeautifulSoup(response.text, “html.parser”)`
- We use the method .findAll to locate all of our `<a>` tags.
  - `soup.findAll('a')`
- we should include this line of code so that we can pause our code for a second so that we are not spamming the website with requests. This helps us avoid getting flagged as a spammer.
  - `time.sleep(1)`

# [What is Web Scraping?](https://en.wikipedia.org/wiki/Web_scraping)

# [Track Amazon Prices Video](https://www.youtube.com/watch?v=Bg9r_yLk7VY)

