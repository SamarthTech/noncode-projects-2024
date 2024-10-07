# Weather API Documentation

## Overview
The Weather API allows developers to access real-time weather data and forecasts for cities around the globe. It provides data such as temperature, humidity, wind speed, and weather conditions. Use this API to build weather-based applications, dashboards, or integrations.

### Use Cases:
- Display real-time weather information on websites or mobile apps.
- Integrate weather data into smart home applications.
- Use weather forecasts for logistics and planning applications.

### Versioning
- **Current Version**: v1.0

---

## Authentication/Authorization

To interact with the Weather API, you must authenticate your requests. The API uses **API keys** for authentication.

### Requesting an API Key
1. Sign up at [weatherapi.example.com/signup](#) to get your free API key.
2. After signing up, you can find your API key on your dashboard.

### Authorization Header Example:
Include the API key in the header of your request as shown below:

```bash
curl -X GET "https://api.weatherapi.com/v1/current" \
-H "Authorization: Bearer your_api_key"
```

---

## Available Endpoints

### Endpoint Overview
| Endpoint                         | Method | Description                          |
|-----------------------------------|--------|--------------------------------------|
| `/v1/current/{city}`              | GET    | Retrieve current weather for a city  |
| `/v1/forecast/{city}`             | GET    | Retrieve weather forecast for a city |
| `/v1/search`                      | GET    | Search for cities by name            |

---

### Endpoint Details

#### `GET /v1/current/{city}`
**Description**: Retrieve the current weather conditions for a specific city.

- **Method**: GET
- **Path Parameter**: 
  - `city` (string, required): The name of the city for which to retrieve the weather.
- **Response**:
  - `200 OK`: Weather data returned successfully.
  - `404 Not Found`: City not found.
  
**Example Request**:
```bash
curl -X GET "https://api.weatherapi.com/v1/current/london" \
-H "Authorization: Bearer your_api_key"
```

**Example Response**:
```json
{
  "city": "London",
  "temperature": 15,
  "units": "Celsius",
  "humidity": 70,
  "wind_speed": 5,
  "condition": "Partly Cloudy"
}
```

---

#### `GET /v1/forecast/{city}`
**Description**: Retrieve a 7-day weather forecast for a specific city.

- **Method**: GET
- **Path Parameter**:
  - `city` (string, required): The city name for which to retrieve the forecast.
- **Query Parameter**:
  - `days` (integer, optional): Number of days for the forecast (default: 7).
- **Response**:
  - `200 OK`: Forecast data returned successfully.
  - `404 Not Found`: City not found.

**Example Request**:
```bash
curl -X GET "https://api.weatherapi.com/v1/forecast/london?days=5" \
-H "Authorization: Bearer your_api_key"
```

**Example Response**:
```json
{
  "city": "London",
  "forecast": [
    {
      "date": "2024-10-06",
      "temperature": {
        "min": 12,
        "max": 18
      },
      "condition": "Rainy"
    },
    {
      "date": "2024-10-07",
      "temperature": {
        "min": 10,
        "max": 16
      },
      "condition": "Cloudy"
    }
  ]
}
```

---

#### `GET /v1/search`
**Description**: Search for cities by name.

- **Method**: GET
- **Query Parameters**:
  - `q` (string, required): Search term (city name).
- **Response**:
  - `200 OK`: List of matching cities returned.

**Example Request**:
```bash
curl -X GET "https://api.weatherapi.com/v1/search?q=london" \
-H "Authorization: Bearer your_api_key"
```

**Example Response**:
```json
[
  {
    "city": "London",
    "country": "United Kingdom"
  },
  {
    "city": "London",
    "country": "Canada"
  }
]
```

---

## Error Handling and Status Codes

The API uses standard HTTP response codes to indicate the success or failure of an API request.

### Standard HTTP Status Codes
- `200 OK`: The request was successful, and the data is returned in the response.
- `400 Bad Request`: The request was malformed or invalid.
- `401 Unauthorized`: Invalid or missing API key.
- `404 Not Found`: The requested resource (e.g., city) could not be found.
- `429 Too Many Requests`: You have exceeded the API rate limit.
- `500 Internal Server Error`: A server error occurred. Retry your request later.

### Custom Error Codes
| Error Code | Description               |
|------------|---------------------------|
| `1001`     | Invalid API key            |
| `1002`     | Exceeded rate limit        |
| `1003`     | City not found             |

---

## Rate Limits and Quotas

To prevent abuse, the API enforces rate limits based on your plan.

- **Rate Limit**: 100 requests per minute.
- **Throttling Behavior**: If you exceed the rate limit, you will receive a `429 Too Many Requests` error.

### Monitoring Usage:
You can monitor your usage and remaining quota through your [API dashboard](#).

---

## API Versioning

The Weather API follows a versioning strategy to ensure backward compatibility.

### Version Strategy:
- The version is defined by the URI (e.g., `/v1/` for version 1).

### Changelog:
- **v1.0**: Initial release.

### Migration Guide:
If breaking changes occur, please refer to the [Migration Guide](#).

---

## Code Snippets

### Python Example:
```python
import requests

url = "https://api.weatherapi.com/v1/current/london"
headers = {"Authorization": "Bearer your_api_key"}

response = requests.get(url, headers=headers)
print(response.json())
```

### JavaScript Example (Node.js):
```javascript
const axios = require('axios');

axios.get('https://api.weatherapi.com/v1/current/london', {
  headers: {
    Authorization: 'Bearer your_api_key'
  }
}).then(response => {
  console.log(response.data);
}).catch(error => {
  console.error(error);
});
```

### Curl Example:
```bash
curl -X GET "https://api.weatherapi.com/v1/current/london" \
-H "Authorization: Bearer your_api_key"
```

---

## SDKs and Libraries

We provide SDKs for multiple programming languages to simplify integration with the Weather API.

- [Python SDK](#)
- [JavaScript SDK](#)

Refer to the SDK documentation for installation instructions and usage examples.

---

## Testing and Interactive Tools

You can test the Weather API in our interactive [API Explorer](#) or download our [Postman Collection](#) to test the endpoints locally.

---

## Best Practices

- **Efficient Data Retrieval**: Use caching to reduce the number of API calls for frequently requested cities.
- **Error Handling**: Implement retry logic for `500` errors and handle rate limit errors (`429 Too Many Requests`).
- **Security**: Always use HTTPS to secure API requests and never expose your API key in client-side code.

---

## Glossary

- **OAuth**: An open standard for access delegation used for token-based authentication.
- **Rate Limits**: The number of API calls allowed within a specific time period (e.g., per minute).
- **Forecast**: A prediction of future weather conditions based on data models.

---

## Appendix

- **Further Reading**: [Google’s API Design Guide](https://cloud.google.com/apis/design)
- **Related APIs**: [Air Quality API](https://openweathermap.org/api/air-pollution)

---