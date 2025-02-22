# reit2csv - Canadian REIT Price Scrape + Cache

## Overview

reit2csv is a Python script that fetches real-time stock prices for Canadian REITs using Yahoo Finance. It ensures data integrity by maintaining timestamps for unchanged values and only queries Yahoo Finance during market hours (9:30 AM - 4:00 PM EST). The collected data is stored in a CSV file, which can be used as a data source for spreadsheets or applications.

## Copyright & Author

- **Copyright (c) 2025 Robbie Ferguson, Category5 Technology TV**
- **Website:** [Category5.TV](https://Category5.TV)
- **Blog:** [Bald Nerd](https://baldnerd.com/)
- **Author:** Robbie Ferguson // Bald Nerd

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Important Disclaimer

This script utilizes Yahoo Finance data via the `yfinance` library. Yahoo Finance does not provide official API access, and its data may be subject to rate limiting or service changes at any time. The data retrieved is for informational purposes only and should not be used for financial trading without verification from official sources.

## Dependencies

reit2csv requires the following dependencies:

- **Python 3.x**
- **yfinance** (Yahoo Finance API) - Install via `pip install yfinance`
- **pyyaml** (YAML parser) - Install via `pip install pyyaml` or `apt install python3-yaml`
- **pytz** (Timezone handling) - Install via `pip install pytz`

## Usage

reit2csv is designed to be run as a cron job to continuously update stock data while respecting market hours. The script will automatically handle whether the market is open or closed, so no additional logic is needed in your scheduling setup.

### Example Crontab Entry

To run the script every 15 minutes during weekdays:

```sh
*/15 * * * 1-5 /home/username/scripts/reit2csv/reit2csv > /dev/null 2>&1
```

### Loading Data into Google Sheets

To use the collected stock prices in Google Sheets, use the following formula:

```excel
=QUERY(IMPORTDATA("https://example.com/example_path/reits.csv"), "SELECT Col2 WHERE Col1='REI.UN'", 0)
```

Replace `https://example.com/example_path/reits.csv` with the actual URL where your CSV file is hosted. Replace `REI.UN` with the REIT you wish to lookup.

## Configuration

Modify the following configuration options to match your setup:

```python
CONFIG_FILE = '/home/username/scripts/reit2csv/reits_config.yaml'
CSV_FILE = '/var/www/html/example_path/reits.csv'
```

These paths should point to your YAML configuration file and the CSV output location, respectively.

## Enjoy!

If you find this script useful, feel free to contribute or provide feedback!
