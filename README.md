# reit2csv
Canadian REIT Price Scrape + Cache

This script fetches real-time stock prices for Canadian REITs using Yahoo Finance. It ensures data integrity by maintaining timestamps for unchanged values and only queries Yahoo Finance during market hours (9:30 AM - 4:00 PM EST).
It saves the collected data to a CSV file which can be used to source your spreadsheet or application.

Copyright (c) 2025 Robbie Ferguson, Category5 Technology TV
Website: https://Category5.TV
Blog: https://baldnerd.com/

Author: Robbie Ferguson // Bald Nerd

Licensed under the MIT License. See LICENSE file for details.

Dependencies:
- Python 3.x
- yfinance (Yahoo Finance API) - Install via `pip install yfinance`
- pyyaml (YAML parser) - Install via `pip install pyyaml` or `apt install python3-yaml`
- pytz (Timezone handling) - Install via `pip install pytz`

Note: The script will take care of whether the market is open or not (no need to worry about it running after-hours).

Example crontab (run every 15 minutes, only during weekdays). Change to your actual path to reit2csv.
# Calculate Investment Data
*/15 * * * 1-5 /home/username/scripts/reit2csv/reit2csv > /dev/null 2>&1

Here's how I load the data into Google Sheets:
=QUERY(IMPORTDATA("https://example.com/example_path/reits.csv"), "SELECT Col2 WHERE Col1='REI.UN'", 0)

You'll also need to modify these two config options:

`CONFIG_FILE = '/home/username/scripts/reit2csv/reits_config.yaml'`
`CSV_FILE = "/var/www/html/example_path/reits.csv"`

Enjoy!
