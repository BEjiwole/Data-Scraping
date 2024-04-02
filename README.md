import requests
from bs4 import BeautifulSoup
url = "https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue"
response = requests.get(url)
html_content = response.text
soup = BeautifulSoup(html_content, "html.parser")
table = soup.find("table", class_="wikitable")
for row in table.find_all("tr")[1:]:
    columns = row.find_all("td")
    rank = columns[0].text.strip()
    company_name = columns[1].text.strip()
    industry = columns[2].text.strip()
    revenue = columns[3].text.strip()
    revenue_growth = columns[4].text.strip()
    headquarters = columns[5].text.strip()
    
    # Do something with the extracted data (e.g., print it)
    print(f"Rank: {rank}, Company Name: {company_name}, Industry: {industry}, Revenue: {revenue}, Revenue Growth: {revenue_growth}, Headquarters: {headquarters}")
