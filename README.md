### Industrial Project Amazon Scrapper
Start project with: 
<ul>
<li>npm install</li>
<li>npm i</li>
<li>npm i -g amazon-buddy</li>
</ul>

Example to run to retrieve a product JSON with asin B072C7TNC5 : 
<ul>
<li>amazon-buddy asin B072C7TNC5 -n 1 --filetype json</li>
</ul>

How to "read" pretty the JSON, use next online tool:
https://jsonformatter.curiousconcept.com/

How to check product asin  B072C7TNC5 on Amazon:\
--> Search in google "amazon B072C7TNC5" and open the first link.
This link is in fact:  https://www.amazon.com/Samsung-49-Inch-Curved-Monitor-LC49HG90DMNXZA/dp/B072C7TNC5 


Now you should be able to visualize all data from JSON retrived above, directly from Amazon offcial site.

Example:
https://github.com/rusuot/industrial_project_amzn_web_scrapper/blob/main/asin(B072C7TNC5)_1712771589712.json 



__________________________________________________________________




### Purpose of this amazon scrapper
As websites scrapping is completly legal, without touching  retrieving any sensitive data such as credentials, \
logins  and so on, a website scrapping details has it's purpose when product details from specific websites are needed. \

Let's suppose we need a JSON file with all details related to an amazon product. \
This kind of JSON file is needed for example for Industrial Project CRUD API Firebase, and further to the website developed for this whole project. \

Let's start with understanding amazon website and URLs. 
1. Open Google and write next: "Amazon SAMSUNG 49-Inch CHG90 144Hz Curved Gaming Monitor (LC49HG90DMNXZA) – Super Ultrawide Screen QLED Computer Monitor, 3840 x 1080p Resolution, 1ms Response, FreeSync 2 with HDR,Black" \
2. This is a simple search for Amazon website with a product name - a Smasung Ultrawide Screen QLED \
3. Now, open the first link Google has returned. \
4. In my case, the URL is next one: 
```
https://www.amazon.com/Samsung-49-Inch-Curved-Monitor-LC49HG90DMNXZA/dp/**B072C7TNC5**"
```
The asin for this product can be found in the above URL, rigth after/dp/. 
In the example above this is:
```
B072C7TNC5
```
### Run the scrapper and obtain a JSON as a response, containing B072C7TNC5 product details
1. In Visual Code Terminal, run:
```
amazon-buddy products -k 'SAMSUNG 49-Inch CHG90 144Hz Curved Gaming Monitor (LC49HG90DMNXZA) - Super Ultrawide Screen QLED Computer Monitor, 3840 x 1080p Resolution, 1ms Response, FreeSync 2 with HDR,Black' -n 1 --filetype json
```
In my case next file was saved: products(SAMSUNG 49-Inch CHG90 144Hz Curved Gaming Monitor (LC49HG90DMNXZA) – Super Ultrawide Screen QLED Computer Monitor, 3840 x 1080p Resolution, 1ms Response, FreeSync 2 with HDR,Black)_1712770654253.json

OR RUN
```
amazon-buddy asin B072C7TNC5 -n 1 --filetype json
```
In my case next file was saved: asin(B072C7TNC5)_1712771589712.json


### What can we do with this website scrapper?
We obtain real data for any product desired from Amazon in this case (can be mapped to any website) and has / have a JSON format.

### How does product details retried look like?
I will explain further next JSON file, retrieved earlier:
```
products(SAMSUNG 49-Inch CHG90 144Hz Curved Gaming Monitor (LC49HG90DMNXZA) – Super Ultrawide Screen QLED Computer Monitor, 3840 x 1080p Resolution, 1ms Response, FreeSync 2 with HDR,Black)_1712770654253
```
In this repo - the JSON file was renamed to:  SAMSUNG_PRODUCT.json

As there are many details, please use next tool to read the file easier: https://jsonformatter.curiousconcept.com/
Steps:  
1. Open https://jsonformatter.curiousconcept.com/
2. Insert the file content into the tool at "JSON Data/URL"
3. Click PROCESS
4. At: "Formatted JSON Data" you will be able to see better the JSON content.
5. It looks like:
```
[
   {
      "position":{
         "page":1,
         "position":1,
         "global_position":1
      },
      "asin":"B07PZR2YY4",
      "price":{
         "discounted":false,
         "current_price":0,
         "currency":"USD",
         "before_price":0,
         "savings_amount":0,
         "savings_percent":0
      },
      "reviews":{
         "total_reviews":0,
         "rating":4.4
      },
      "url":"https://www.amazon.com/dp/B07PZR2YY4",
      "score":0,
      "sponsored":false,
      "amazonChoice":false,
      "bestSeller":false,
      "amazonPrime":false
   },
   {
      "position":{
         "page":1,
         "position":2,
         "global_position":2
      },
      "asin":"B0BM7WNLPL",
      "price":{
         "discounted":false,
         "current_price":0,
         "currency":"USD",
         "before_price":0,
         "savings_amount":0,
         "savings_percent":0
      },
      "reviews":{
         "total_reviews":0,
         "rating":4.5
      },
      "url":"https://www.amazon.com/dp/B0BM7WNLPL",
      "score":0,
      "sponsored":false,
      "amazonChoice":false,
      "bestSeller":false,
      "amazonPrime":false
   },
........
........
```
As can be seen there are so many details and for Industrial Project, at this moment we use only: id, title, price, description, category, image, rating->rate & rating->count.

###
So, now we have the products details saved in JSON files, but we need an API.
We have at this moment the option to work in two ways:
1. FakeAPI OR create a Fake JSON API(using https://mocki.io/fake-json-api ) using this files  (much easier to fetch directly from these fake APIs containing real amanzon data)
2. We have as well the CRUD API Firebase done for Industrial Project, with which we can POST (create) products in DB using these JSON details.

Fetch from fake API simulates data retrival form amazon, and with CRUD API Firebase we can add JSON contents into Firebase DB, as well
Most probably the Industrial Project will be a combination of these too.



##### This scrapper is inspired from GitHub amazon-scrappers, it does have some updateds made by team group projet members but this scrapper is inspired from GIT.
Inspired from:  https://github.com/linconrezende/amazon-scraper 
