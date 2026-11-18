# Smartprix TWS Earbuds Scraper

Collects TWS earbuds specifications and prices from
https://www.smartprix.com/mobile_headphones

## How it works
1. **Selenium** opens the listing page, applies the earbuds filter, and clicks
   "load more" until the page height stops changing (3 unchanged checks in a row).
   The final page source is saved as `earbuds.html`.
2. **BeautifulSoup** parses `earbuds.html` and extracts each product card.
3. **pandas** builds a DataFrame and saves it as `earbuds.csv`.

## Requirements
- Python 3.9+
- Google Chrome and a matching [chromedriver](https://chromedriver.chromium.org/)
- `pip install -r requirements.txt`

## Usage
1. Put `chromedriver.exe` next to `scraper.ipynb` (or edit the `Service(...)` path).
2. Run the notebook cells in order.
3. When the browser finishes loading, press Enter in the prompt to close it.
4. Output: `earbuds.csv`

## Output columns
product_name, price, rating, design_type, fit_style, connectivity,
bluetooth_version, anc, microphone, wireless_range, battery_life

Missing values are stored as `Not mentioned` (or NaN for price).

## Notes
- The XPaths and CSS class names match the site layout at the time of scraping
  (November 2026). If Smartprix changes its HTML, the script will need updating.
- The scraper waits 2-5 seconds between actions to avoid overloading the site.

## Links
- Dataset: https://www.kaggle.com/datasets/samirlakhe/smartprix-tws-earbuds-dataset
- Cleaning notebook: https://www.kaggle.com/code/samirlakhe/data-cleaning-of-the-earbud-dataset

## Disclaimer
The data belongs to smartprix.com. This project is for educational purposes only.
Please review the site's terms of service and robots.txt before scraping.
