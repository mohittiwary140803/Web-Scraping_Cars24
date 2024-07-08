Overview : 
	This project involved developing a Python script to scrape used car listings from the Cars24 website using the selenium and BeautifulSoup libraries. The aim was to extract detailed information about the cars listed, such as the year of manufacture, make, model, transmission type, kilometers driven, fuel type, and price. 

Libraries and Setup : 
Selenium : Used for automating web browser interaction. Selenium is particularly useful for scraping Dynamic content that loads with javascript.
BeautifulSoup : Used for Parsing HTML and extracting the necessary data.
Requests : Initially attempted to use this for HTTP requests, but it resulted in a 403 error. 
Pandas : Used for organizing and analyzing the scraped data.
Other Utilities : Includes warnings to suppress any unwanted warning messages during execution.

Configuring Selenium : 
Installed the Chrome WebDriver using ‘webdriver_manager.chrome’ .
Configured chrome options to run in headless mode to avoid opening browser windows during execution.
	      Code snippet : 
              from selenium import webdriver 
              from selenium.webdriver.chrome.options import Options 
              from webdriver_manager.chrome import ChromeDriverManager 
              chrome_options = Options() 
              chrome_options.add_argument("--headless")

Defining the URL 
The URL was set to Cars24’s page specifically filtered for Maruti Suzuki Cars, sorted by best match.
        Code snippet : 
              url = 'https://www.cars24.com/buy-used-car?f=make%3A%3D%3Amaruti&sort=bestmatch&serveWarrantyCount=true&gaId=444609335.1720011387&listingSource=TabFilter&storeCityId=2378'

Helper Function - ‘get_details’ 
Used BeautifulSoup to parse the HTML content.
Extracted specific elements such as car names, transmission details, kilometers driven, and prices using their respective HTML tags and classes.

Extracting Car Details : 
Car name : Extracted the year, make, model from the car name element.
Transmission :  Extracted transmission type from a nested list element.
Kilometers Driven : Extracted and cleaned the kilometers driven text.
Fuel Type : Extracted the fuel type from a nested list element.
Prices : Extracted and converted the price text to numerical values.

Challenges Faced - 
1. 403 Forbidden Error with ‘requests’ module : 
Initial attempts to use the ‘requests’ module to fetch the webpage content resulted in a 403 Forbidden response.
Solution :  Implemented Selenium to simulate browser interactions, bypassing the access restriction.
2. Dynamic content loading : 
The Cars24 website loads content dynamically as the user scrolls. 
Solution : Implemented a scrolling mechanism using selenium to ensure all content is loaded before scraping.
3. Parsing Nested HTML Elements : 
Extracting details from nested HTML elements required careful selection of tags and classes.
Solution : Used BeautifulSoup to navigate and extract the necessary elements and their text content.

Insights Gained -
1. Diverse car Listings : 
The data revealed a variety of Maruti car models, with varying years of manufacture, transmission types, and fuel types.

2. Price Range : 
Prices varied significantly, providing insights into the factors influencing used car prices such as model, age, and kilometers driven.

3. Common Transmission Types :
Analysis of the transmission data showed the prevalence of certain transmission types among Maruti cars.

4. Fuel Type Distribution : 
The data allowed for the examination of fuel type preferences with insights into the popularity of petrol vs. diesel cars.

Conclusion - The project successfully extracted detailed information about used Maruti cars from the cars24 website. Despite challenges with access restrictions and dynamic content loading, the use of Selenium and BeautifulSoup enabled effective web scraping. The insights gained from the data provided valuable information on the used car market for Maruti Vehicles. This approach can be extended to other brands and listings on the cars24 platform, offering a robust method for collecting and analyzing used car data.
