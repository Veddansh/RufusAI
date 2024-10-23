# RufusAI
Overview
This project is a Flask-based web scraping API that scrapes web pages, extracts relevant content, and filters it based on user-defined prompts. The API uses Selenium for web scraping, BeautifulSoup for content extraction, and OpenAI’s GPT-3.5 for content filtering.

Features
Web Scraping: Extracts content from the provided URL.
Content Filtering: Filters relevant content based on a prompt using OpenAI’s GPT-3.5.
Efficient Processing: Optimized to only pull the necessary data, limiting the scope to improve speed.
Asynchronous Operation: Runs Flask in a background thread.

Prerequisites
Python 3.x
ChromeDriver (ensure it's in your PATH or provide its path in the code)
Required Python libraries:
flask
threading
beautifulsoup4
selenium
requests
openai

1) Installation
Clone the repository:

bash
git clone <repository-url>
cd <repository-directory>

2) Install the dependencies:

bash
pip install flask selenium beautifulsoup4 requests openai
Download and set up ChromeDriver:

Ensure chromedriver is installed and placed in your PATH.

3) Set up OpenAI API key:

Replace the placeholder openai.api_key in the code with your OpenAI API key.


**Usage**

Run the Flask app:

bash
python app.py

Make a POST request to the /scrape endpoint: Use Postman, curl, or any HTTP client to make a request:

bash
POST http://127.0.0.1:5000/scrape
Body:

json
{
  "url": "https://en.wikipedia.org/wiki/Artificial_intelligence",
  "prompt": "Find information about artificial intelligence"
}

Response: The API will return a JSON response with the relevant content based on the prompt:

json
{
  "url": "https://en.wikipedia.org/wiki/Artificial_intelligence",
  "prompt": "Find information about artificial intelligence",
  "relevant_content": "..."
}


**Code Structure**
app.py: Main Flask application with scraping and filtering logic.
setup_driver(): Initializes the Selenium Chrome WebDriver in headless mode.
crawl_page(url): Scrapes the given URL and extracts the page's content.
extract_content(page_source): Extracts relevant <p> tags using BeautifulSoup.
filter_relevant_content(prompt, content_list): Filters the extracted content using OpenAI’s GPT-3.5.

**Known Issues**
Selenium ChromeDriver: Ensure chromedriver is compatible with your version of Chrome.
API Rate Limits: OpenAI’s API has rate limits; ensure your requests are within their quota.
