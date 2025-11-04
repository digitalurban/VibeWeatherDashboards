
Weather Dashboards made with Vibe Coding

First Example:

# Weather Model Dashboard

This is a single-page, self-contained weather dashboard that displays current conditions, an hourly outlook, and a 7-day forecast.

It is built as a single HTML file with no external dependencies other than free CDNs. It uses **Tailwind CSS** for styling and **Chart.js** for data visualization.

## 🚀 Key Features

* **Current Conditions:** Displays temperature, "feels like" temp, precipitation, pressure (with a 3-hour trend icon), wind gusts, visibility, and cloud cover.
* **Hourly Forecast:** Shows the next 5 hours of weather, including icon, temperature, and precipitation probability.
* **7-Day Forecast:** A full weekly forecast with daily icons, max/min temps, and total precipitation.
* **Interactive Charts:** Features two 7-day charts on separate tabs:
    1.  Temperature (Max/Min) & Precipitation
    2.  Wind Gusts & Pressure
* **Auto-Refresh:** The weather data automatically fetches new data every 5 minutes.
* **Dark Mode:** The design is fully responsive and supports both light and dark modes.

## 📊 How It Works & Data Sources

This dashboard is 100% client-side, meaning it runs entirely in your browser with no backend required.

### 1. Data Source: Open-Meteo API

The dashboard is powered entirely by the free [Open-Meteo API](https://open-meteo.com/).

* When the page loads, the `fetchWeather` JavaScript function is called.
* This function makes an API call to `https://api.open-meteo.com/v1/forecast` with specific coordinates (`latitude=52.60`, `longitude=0.37`) and requests current, hourly, and daily data.
* The API returns a single JSON file containing all the necessary forecast data.
* JavaScript functions (like `displayCurrentWeather`, `displayWeeklyForecast`) then parse this JSON and update the text and icons on the page.

### 2. Charting: Chart.js

The two graphs on the page are rendered using **Chart.js**, a popular JavaScript charting library.

* The `displayCharts` function takes the JSON data from Open-Meteo.
* It creates two `Chart.js` instances: one for temperature/precipitation and one for wind/pressure.
* These charts are destroyed and rebuilt every time the data refreshes.

### 3. Other Dependencies (via CDN)

This page relies on a few other services, all loaded remotely via CDN:

* **Styling:** **Tailwind CSS** (for the responsive layout and utility classes).
* **Fonts:** **Google Fonts** (specifically the "Inter" font family).
* **Icons:** **Weather Icons** (used by the `getWeatherIcon` helper function to translate API weather codes into icon classes like `wi-day-sunny`).

## ⚙️ How to Use or Customize

### Hosting

Because this is a single, self-contained file, you can host it on any static site service, including **GitHub Pages**. You only need to upload the `weathermodel.html` file.

### Changing the Location

To change the forecast location from Downham Market to somewhere else:

1.  Open `weathermodel.html` in a text editor.
2.  Find the `fetchWeather` function in the `<script>` block (around line 140).
3.  Change the `latitude` and `longitude` variables to your new coordinates:
    ```javascript
    async function fetchWeather() {
        const latitude = 52.60;  // <-- Change this
        const longitude = 0.37; // <-- Change this
        const apiUrl = `https...`;
        // ...
    }
    ```
4.  You may also want to change the hard-coded location title near the top of the file (around line 50):
    ```html
    <h1 class="text-2xl font-bold ...">Downham Market</h1>
    <p class="text-gray-500 ...">Norfolk</p>
    ```
