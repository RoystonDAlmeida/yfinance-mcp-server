# Stock Price Server

A FastMCP-based server that provides real-time stock price data and historical information using the Yahoo Finance API.

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
  - [Starting the Server](#starting-the-server)
  - [Available Tools](#available-tools)
- [Dependencies](#dependencies)
- [Error Handling](#error-handling)
- [License](#license)
- [Contributing](#contributing)

## Features

- Get current stock prices for any ticker symbol
- Retrieve historical stock data
- Compare prices between two stocks

## Prerequisites

- Python 3.12 or higher
- uv (Python package installer and environment manager)

## Installation

1. Clone the repository:
```bash
git clone git@github.com:RoystonDAlmeida/yfinance-mcp-server.git
cd yfinance-mcp-server/
```

2. Create and activate a virtual environment using uv:
```bash
uv venv
source .venv/bin/activate  # On Linux/Mac
# or
.venv\Scripts\activate  # On Windows
```

3. Install dependencies using uv:
```bash
uv pip install -e .
```

## Usage

### Starting the Server

You can start the server in two ways:

1. Direct execution:
```bash
python main.py
```

2. Using MCP configuration:
Create or update your `.cursor/mcp.json` file with the following configuration:
```json
{
    "mcpServers": {
        "yfinance-mcp-server": {
            "command": "/path/to/your/venv/bin/python",
            "args": ["/path/to/your/main.py"]
        }
    }
}
```

Make sure to replace `/path/to/your/` with the actual paths to your virtual environment and project directory.

### Available Tools

1. **Get Stock Price**
   - Function: `get_stock_price(symbol: str) -> float`
   - Returns the current stock price for a given ticker symbol
   - Returns -1.0 if there's an error

2. **Get Stock History**
   - Function: `get_stock_history(symbol: str, period: str = "1mo") -> str`
   - Returns historical data in CSV format
   - Period options: "1d", "5d", "1mo", "3mo", "6mo", "1y", "2y", "5y", "10y", "ytd", "max"

3. **Compare Stocks**
   - Function: `compare_stocks(symbol1: str, symbol2: str) -> str`
   - Compares current prices of two stocks
   - Returns a formatted comparison message

## Dependencies

The project uses `uv` for dependency management with the following key dependencies:
- fastmcp >= 2.5.1
- yfinance >= 0.2.61

Dependencies are managed through `pyproject.toml` file.

## Error Handling

- The server returns -1.0 for stock prices when there's an error
- Error messages are provided in a user-friendly format
- Invalid symbols or network issues are handled gracefully

## License

This project is licensed under the MIT License - see the [LICENSE](https://opensource.org/licenses/MIT) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request