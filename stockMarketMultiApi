const express = require('express');
const yahooFinance = require('yahoo-finance2');

const app = express();
const PORT = process.env.PORT || 3000;

// Define an Express route to fetch news
app.get('/api/news/:query', async (req, res) => {
  try {
    const query = req.params.query;
    const result = await yahooFinance.search(query);

    // Extract news from the result
    const news = result.news;

    // Send the news as a response
    res.json(news);
  } catch (error) {
    // If an error occurs, send an error response
    console.error('Error fetching news:', error);
    res.status(500).json({ error: 'Internal Server Error' });
  }
});

// Define an Express route to fetch insights
app.get('/api/insights/:symbol', async (req, res) => {
  try {
    const symbol = req.params.symbol;
    const queryOptions = { lang: 'en-US', reportsCount: 2, region: 'US' };
    const result = await yahooFinance.insights(symbol, queryOptions);

    // Extract insights from the result
    const insights = result.insights;

    // Send the insights as a response
    res.json(insights);
  } catch (error) {
    // If an error occurs, send an error response
    console.error('Error fetching insights:', error);
    res.status(500).json({ error: 'Internal Server Error' });
  }
});

// Define an Express route to fetch options data
app.get('/api/options/:symbol', async (req, res) => {
  try {
    const symbol = req.params.symbol;
    const queryOptions = { lang: 'en-US', formatted: false, region: 'US' };
    const result = await yahooFinance.options(symbol, queryOptions);

    // Extract options data from the result
    const optionsData = result.options;

    // Send the options data as a response
    res.json(optionsData);
  } catch (error) {
    // If an error occurs, send an error response
    console.error('Error fetching options data:', error);
    res.status(500).json({ error: 'Internal Server Error' });
  }
});

// Start the Express server
app.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});
