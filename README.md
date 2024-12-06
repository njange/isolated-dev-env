# **Django Web Scraper**

A web scraping application built with Django that allows users to scrape data from websites and view the results in a user-friendly interface.

## **Features**
- Scrapes data (e.g., links and titles) from a specified website.
- Displays the scraped data in a web interface.
- Extensible and easy to customize.

---

## **Getting Started**

Follow these steps to set up and run the project on your local machine.

### **Prerequisites**
Ensure you have the following installed:
- Python 3.8+
- pip (Python package manager)
- Django 4.0+
- Docker (optional, for containerized setup)

---

### **Setup Instructions**

#### 1. Clone the Repository

``code
git clone https://github.com/njange/django-webscraper.git
cd django-webscraper

#### 2. Install Dependencies

``bash
pip install -r requirements.txt

#### 3. Apply Migrations

``bash
Copy code
python manage.py makemigrations
python manage.py migrate
#### 4. Run the Development Server

``bash
python manage.py runserver

Usage
Access the application in your browser at:

``bash
http://127.0.0.1:8000/scraper/scrape/

To scrape a different website, pass a url query parameter in the URL. For example:

``bash
http://127.0.0.1:8000/scraper/scrape/?url=https://example.com

#### Customization
Change the Scraping Logic
Modify the scraping logic in scraper/utils.py:

``bash

def scrape_website(url):
    response = requests.get(url)
    soup = BeautifulSoup(response.text, 'html.parser')

    data = []
    for item in soup.find_all('a', href=True):
        data.append({
            'title': item.text.strip(),
            'link': item['href'],
        })
    return data
    
#### Store Scraped Data
To save the scraped data to a database, use the ScrapedData model defined in scraper/models.py.

#### Running with Docker (Optional)

Build the Docker Image:
`bash
docker build -t django-webscraper .

#### Run the Container:

``bash
docker run -p 8000:8000 django-webscraper

#### Access the Application:

``bash
http://127.0.0.1:8000/scraper/scrape/
#### License
This project is licensed under the MIT License. See the LICENSE file for details.

#### Contributing
Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.
