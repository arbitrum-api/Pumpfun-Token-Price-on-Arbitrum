# Pumpfun-Token-Price-on-Arbitrum
Pumpfun Token Price on Arbitrum

Instantly retrieve the real-time price of any Pumpfun token in both ETH and USD with a simple GET request to our Arbitrum API.

Easily access the current price of any Pumpfun token deployed on the Arbitrum network by sending a GET request to our dedicated API endpoint. The response provides the token price in ETH and USD, updated in real-time based on the token's bonding curve on Pumpfun.
API Endpoint:

https://arbitrum-api.co/price/$MINT
How It Works

When you send a request to this endpoint, the price of the token is calculated at the exact moment based on the token’s bonding curve status on Pumpfun. This ensures real-time price updates reflecting the dynamic nature of bonding curves.

Please note, this API only supports tokens currently listed on Pumpfun. If a token has migrated from Pumpfun to another platform (e.g., Uniswap or Sushiswap on Arbitrum), this endpoint will not return a price for that token. For tokens migrated off Pumpfun, use the appropriate price API from the platform the token has moved to.
Features:

    Real-Time Pricing: Get the latest token price at the time of your request.
    Currency Support: Prices available in both ETH and USD for better clarity.
    Bonding Curve Data: Token prices are dynamically calculated based on the current bonding curve of the token.

Important Notes:

    Only tokens currently listed on Pumpfun on Arbitrum will return valid pricing data.
    If the token has migrated to another platform like Uniswap or Sushiswap, refer to that platform’s API for price updates.
    The API relies on the real-time bonding curve data, so prices are always up-to-date at the moment of the request.

Example Code Using Node.js

Here's an example of how you can use the Pumpfun Token Price API with Node.js and the axios library to retrieve token prices.

const axios = require('axios');

// Function to test the price API
async function testPriceApi() {
  try {
    const response = await axios.get('https://arbitrum-api.co/price/Yngq1h5T6frA435CcP46a6emZuaqfs9bjPiPxAKpump');
    
    // Log the response data
    console.log('Price Data:', response.data);
  } catch (error) {
    // If there was an error, log it
    console.error('Error fetching price:', error.message);
  }
}

// Call the test function
testPriceApi();

Example Successful Response

{
  "ETH": "0.0000000897",
  "USD": "0.0000137945"
}

Example Error Response (If Bonding Curve Not Found)

{
  "status": "failed",
  "message": "BondingCurve Not Found",
  "error": "The bonding curve for this token is not available on Pumpfun."
}
