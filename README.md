# Monobank Open API (v2303)

## Overview
Monobank Open API provides access to account statements and the status of personal and sole proprietorship accounts. This API is designed to facilitate the integration of Monobank's banking services into your applications, providing capabilities such as retrieving exchange rates, client information, and transaction statements.

### Features
- **Exchange Rates**: Get the latest currency exchange rates.
- **Client Information**: Retrieve detailed information about clients, including account and bank details.
- **Transaction Statements**: Access detailed transaction history for specified periods.

## Prerequisites
To use this API, you need to:
- Have a Monobank account.
- Obtain an API access token by logging into your personal account at [Monobank API Portal](https://api.monobank.ua/).

## Getting Started
To get started with the Monobank Open API, follow these steps:
1. Ensure you have a Monobank account.
2. Log in to your account at [https://api.monobank.ua/](https://api.monobank.ua/) and navigate to the API section to obtain your personal API token.
3. Use the token as the `X-Token` header for all your requests to the API.

## API Usage

### Exchange Rates
- **Endpoint**: `GET /bank/currency`
- **Description**: Retrieves basic currency exchange rates. Data is cached and updated every 5 minutes.
- **Example Request**:
  ```bash
  curl -X GET "{{BASE_URL}}/bank/currency" -H "Content-Type: application/json"
  ```

### Client Information
- **Endpoint**: `GET /personal/client-info`
- **Required**: `X-Token` header for authentication.
- **Description**: Fetches information about the client, including accounts and associated banks. Can be called no more than once every 60 seconds.
- **Example Request**:
  ```bash
  curl -X GET "{{BASE_URL}}/personal/client-info" -H "X-Token: your_access_token"
  ```

### Transaction Statements
- **Endpoint**: `GET /personal/statement/{account}/{from}/{to}`
- **Required**: `X-Token` header for authentication.
- **Description**: Retrieves transaction statements for a specified period. The maximum period retrievable is 31 days plus 1 hour.
- **Example Request**:
  ```bash
  curl -X GET "{{BASE_URL}}/personal/statement/{account}/{from}/{to}" -H "X-Token: your_access_token"
  ```

## Support and Community
If you have questions about the API or encounter any issues, you are encouraged to join our community on Telegram. Additionally, the API documentation is available for more detailed information and troubleshooting tips.

## Contributing
We welcome contributions to improve the API documentation or client libraries. Please feel free to fork the repository, make changes, and submit pull requests. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)

## Disclaimer
This API is not available to clients under 16 years of age. Information on children's accounts is accessible from the parent's account. The bank reserves the right to impose sanctions if misuse of the API is detected.

### Notes:
- **BASE_URL** and other placeholders should be replaced with actual values or variables defined in your environment setup.
- The examples provided use `curl` for API calls, which is standard for command-line HTTP requests. You may need to adjust these examples based on your specific implementation needs or programming environment.
- Ensure that any endpoints, parameters, or details specific to your version of the API are updated accordingly in the README.