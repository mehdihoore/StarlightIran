# SABAAT: Intelligent Search and Information Hub

SABAAT is a powerful Cloudflare Worker application designed to provide users with a comprehensive search experience and a wealth of information, all in one place.

## Features

- **Multi-Engine Search:** SABAAT aggregates search results from various engines, including:
    - Google (Custom Search)
    - DuckDuckGo (Web and News)
    - Wikipedia
    - Stanford Encyclopedia of Philosophy (SEP)
    - Qwant
    - The New York Times Article Search

- **AI-Powered Response Generation:**
    - Uses Google's Gemini model to generate informative and concise answers to user queries, directly referencing the search results.
    - Adds relevant links to search result in the answer (at least one link required).
    - Emphasizes providing accurate information and avoids revealing its AI nature in responses.

- **Date and Time Information:**
    - Displays the current date and time in both Gregorian and Shamsi (Persian) calendars.
    - Shows a list of today's events in the Iranian calendar.

- **NASA's Astronomy Picture of the Day (APOD):**
    - Fetches and displays NASA's APOD.
    - Provides both English and Persian explanations of the image (translated using Gemini).

- **Planetarium View:**
    - Offers a real-time view of the planets visible in the sky from Tehran, Iran, using data from `api.visibleplanets.dev`.
    - Displays planet names in Persian.

- **Image Generation:**
    - Uses the `@cf/runwayml/stable-diffusion-v1-5` model to generate images based on user prompts.

- **Theme Toggle:**
    - Allows users to switch between light and dark themes.

- **Navigation Bar:**
    - Provides quick links to other useful resources, such as:
        - VPN list
        - Steel tables
        - Weather news
        - AI chat
        - Philosophy chat
        - Night sky map

- **Proxy Functionality:**
    - Includes a proxy endpoint (`/proxy`) to bypass restrictions and access websites that might be blocked.

## Setup

1. **Prerequisites:**
    -   A Cloudflare account.
    -   The `wrangler` CLI installed and configured.

2. **Clone the Repository:**
    ```bash
    git clone https://github.com/mehdihoore/StarlightIran
    cd StarlightIran
    ```

3. **Environment Variables:**
    -   Create a `.dev.vars` file in the root of your project.
    -   Add the following environment variables (replace with your actual keys):

    ```
    GOOGLE_API_KEY = "YOUR_GOOGLE_API_KEY"
    GOOGLE_CSE_ID = "YOUR_GOOGLE_CSE_ID"
    GEMINI_API_KEY = "YOUR_GEMINI_API_KEY"
    NASA_API_KEY = "YOUR_NASA_API_KEY"
    NYT_API_KEY = "YOUR_NYT_API_KEY"
    ```

    -   **Important:** You need to obtain API keys from Google, Gemini, NASA, and The New York Times to use their respective services.

4. **Install Dependencies:**
    ```bash
    npm install
    ```

5. **Deploy to Cloudflare:**
    ```bash
    wrangler deploy
    ```

## Usage

-   **Search:** Enter your query in the search bar and click "جستجو". The results will be displayed from multiple search engines, and the AI will generate a comprehensive answer.
-   **Date and Time:** The current date and time in Gregorian and Shamsi calendars are displayed prominently, along with Iranian events for the day.
-   **NASA APOD:** View the daily astronomy picture from NASA, with explanations in English and Persian. Click the tabs to switch between languages.
-   **Planetarium:** See which planets are currently visible in the sky from Tehran. The planetarium updates every 5 minutes.
-   **Image Generation:** Enter a text prompt to generate an image using Stable Diffusion.
-   **Theme:** Toggle between light and dark themes using the button in the top left corner.
-   **Navigation:** Use the navigation bar at the top to access other services like VPN list, steel tables, weather news, AI chat, philosophy chat, and night sky map.
-   **Proxy:** To access a website through the proxy, use the `/proxy` endpoint with the `url` parameter:

    ```
    https://nse.aihoore.ir/
    ```

  
## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests to enhance the project.

## License

This project is licensed under the [MIT License](LICENSE) - see the `LICENSE` file for details.
