import requests
from bs4 import BeautifulSoup
import pandas as pd

url = "http://books.toscrape.com/catalogue/category/books_1/index.html"
response = requests.get(url)
soup = BeautifulSoup(response.text, 'html.parser')

titles = []
prices = []
ratings = []

for book in soup.find_all('article', class_='product_pod'):
    titles.append(book.h3.a['title'])
    prices.append(book.find('p', class_='price_color').text)
    ratings.append(book.p['class'][1])  # e.g., "Three"

# Create DataFrame
df = pd.DataFrame({
    'Property Address': titles,
    'Listing Price': prices,
    'Bedrooms': ratings
})

df.to_csv('real_estate_listings.csv', index=False)
print("Scraping complete. CSV saved.")
