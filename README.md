Flipkart Phone Data Analysis
This project involves web scraping Flipkart for phone data and analyzing the extracted data. The analysis includes data cleaning, feature extraction, and visualization to gain insights into various phone attributes.

Prerequisites
Make sure you have Python 3.x installed. The project uses the following libraries:

numpy
pandas
matplotlib
seaborn
requests
beautifulsoup4
selenium
Install the required packages using pip:

bash
Copy code
pip install numpy pandas matplotlib seaborn requests beautifulsoup4 selenium
Script Overview
Data Scraping:

Fetches phone data from Flipkart using BeautifulSoup and Requests.
Extracts product details such as name, price, rating, specifications, and number of ratings/reviews.
Data Cleaning:

Converts scraped data into a DataFrame.
Cleans and formats data fields, including price and ratings.
Feature Extraction:

Extracts specific features from the specifications, such as processor, RAM, ROM, battery capacity, display size, and camera.
Data Analysis and Visualization:

Performs exploratory data analysis (EDA) using Seaborn and Matplotlib.
Creates various plots including bar plots, line plots, and histograms to visualize relationships between phone attributes and prices.
Usage
Run the Script:

Ensure all required packages are installed.
Execute the script in a Python environment:
bash
Copy code
python script_name.py
View Results:

The script outputs a CSV file Phones_Assesment.csv containing the cleaned and processed data.
It also generates visualizations saved as PNG files in the current directory.
Code Details
Data Scraping:

python
Copy code
URL = 'https://www.flipkart.com/search?q=phone'
page = requests.get(URL)
soup = BeautifulSoup(page.content, 'html.parser')
Data Extraction:

python
Copy code
name = soup.find('div', class_='_4rR01T').text
price = soup.find('div', class_='_30jeq3 _1_WHN1').text
rating = soup.find('div', class_='_3LWZlK').text
Data Cleaning and Feature Extraction:

python
Copy code
data['Price'] = data['Price'].str.replace('₹', '').str.replace(',', '').astype(float)
data['Processor'] = data.Features.apply(get_processor)
Visualization:

python
Copy code
plt.figure(figsize=(18,5))
sns.barplot(data=df, x='Brand', y='Price')
Notes
Update the script if the structure of the Flipkart page changes.
Make sure to handle any legal and ethical considerations when scraping data from websites.
