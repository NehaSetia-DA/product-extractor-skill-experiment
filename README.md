# Product Extractor Skill

An experimental skill to explore how to use Zyte API with Claude Skills. This skill extracts structured product data (price, currency, availability) from e-commerce URLs using Zyte AI.

## Overview

The Product Extractor skill is designed to fetch and extract product information from e-commerce websites. It uses the Zyte API to scrape product data including prices, currency, availability, and other product details from any product URL.

## Features

- 🛍️ Extract product data from e-commerce URLs
- 💰 Retrieve price and currency information
- 📦 Check product availability/stock status
- 🔍 Get product descriptions and details
- 🌐 Uses browser rendering for JavaScript-heavy sites
- 📄 Saves browser HTML as fallback for manual inspection

## Prerequisites

- Python 3.x
- Zyte API Key ([Get one here](https://www.zyte.com/))
- `requests` library

## Installation

1. Clone this repository:
```bash
git clone https://github.com/NehaSetia-DA/product-extractor-skill-experiment.git
cd product-extractor-skill-experiment
```

2. Install required dependencies:
```bash
pip install requests
```

3. Set your Zyte API key as an environment variable:
```bash
export ZYTE_API_KEY="your-api-key-here"
```

Or on Windows:
```bash
set ZYTE_API_KEY=your-api-key-here
```

## Usage

### Command Line

Run the script with your Zyte API key and product URL:

```bash
python scripts/fetch_price.py $ZYTE_API_KEY "https://example.com/product"
```

Or with the API key directly:
```bash
python scripts/fetch_price.py "your-api-key" "https://example.com/product"
```

### Output

The script will:
1. Print a JSON object containing the extracted product details to stdout
2. Save `browser_html.html` file containing the rendered HTML for fallback reference

### Example

```bash
python scripts/fetch_price.py $ZYTE_API_KEY "https://www.amazon.com/dp/B08N5WRWNW"
```

## Project Structure

```
product-extractor-skill-experiment/
├── README.md                 # This file
├── SKILL.md                  # Skill documentation for Claude
├── scripts/
│   └── fetch_price.py       # Main script for fetching product data
└── .gitattributes           # Git attributes configuration
```

## How It Works

1. The script sends a POST request to Zyte API's extract endpoint
2. Zyte API renders the page using a browser and extracts product data
3. The extracted product information is returned as JSON
4. The script prints the product data and saves the browser HTML for reference

## Requirements

- Python 3.x
- `requests` library (`pip install requests`)
- Valid Zyte API key set in `ZYTE_API_KEY` environment variable

## Integration with Claude Skills

This skill is designed to work with Claude Skills. When a user provides a product URL, the skill:

1. **Triggers** when the user asks for product details (price, stock, description)
2. **Executes** the Python script with the Zyte API key and product URL
3. **Processes** the JSON output and presents it in a clean format
4. **Falls back** to reading `browser_html.html` if JSON is incomplete

See `SKILL.md` for detailed integration instructions.

## Error Handling

The script includes basic error handling:
- Validates that both API key and URL are provided
- Exits with an error message if arguments are missing

## Contributing

This is an experimental project. Feel free to submit issues or pull requests!

## License

This project is experimental and provided as-is.

## Resources

- [Zyte API Documentation](https://docs.zyte.com/)
- [Zyte Website](https://www.zyte.com/)
