# Filmpire

Filmpire is a sleek, intuitive movie search application that allows users to seamlessly discover movies. Whether you're looking for classics, blockbusters, or hidden gems, Filmpire provides a quick and visually appealing way to find exactly what you want!

---

## 🌟 General Overview (Non-Technical)

### What is Filmpire?
Filmpire is your personal movie discovery engine. Built with simplicity and user experience in mind, it allows you to easily search for any movie and instantly see its details, such as the release year, media type (movie, series, etc.), and original poster artwork. 

### Key Features
- **Instant Search:** Type any movie name into the search bar and hit enter or click the search icon to get instant results.
- **Visual Grid:** Movies are displayed in an aesthetic, responsive grid layout, highlighting the movie poster, title, and release year.
- **Default Showcase:** Opens with a default showcase of movies (e.g., "Batman") so you can get started immediately without an empty screen.
- **Fallback Imagery:** If a particular movie doesn't have an official poster available, Filmpire provides a clean placeholder image to ensure the visual layout remains intact.

---

## 💻 Technical Overview (For Developers)

### Tech Stack
- **Frontend Framework:** React 18 (Bootstrapped via Create React App)
- **Styling:** Custom Vanilla CSS (`App.css`) for a responsive, modern glassmorphism and grid-based interface.
- **API Integration:** Browser native `fetch` API making calls to external movie databases using an environment-provided root URL endpoint.
- **State Management:** React Hooks (`useState` for search terms and movie listings, `useEffect` for the initial data mount).

### Project Structure
```text
filmpire/
├── public/                # Public assets (e.g., index.html, favicon, robots.txt)
├── src/                   # Main application source code
│   ├── App.js             # Core application component and global search/fetch logic
│   ├── App.css            # Application global styles and grid layouts
│   ├── MovieCard.jsx      # Reusable UI stateless component for rendering individual movies
│   ├── index.js           # Entry point for the React application
│   └── search.svg         # SVG graphical asset for the search bar icon
├── .env                   # Environment variables (required for local development)
├── package.json           # Project metadata, scripts, and dependencies
└── README.md              # Project documentation
```

### Installation and Setup

To get a local instance of Filmpire up and running, follow these simple steps:

1. **Clone the repository:** Check out the source code to your local machine.
2. **Navigate into the project directory:**
   ```bash
   cd filmpire
   ```
3. **Install the dependencies:** Install all the required NPM libraries for React and testing.
   ```bash
   npm install
   ```
4. **Environment Variables:**
   You will need to set up an environment variable for the API URL in a `.env` file at the root of your project:
   ```env
   REACT_APP_API_URL="https://www.omdbapi.com?apikey=[YOUR_API_KEY]"
   ```
   *(Note: The app expects a search endpoint like OMDB API. Append your personal API key)*

5. **Start the development server:**
   ```bash
   npm start
   ```
   The application will automatically open in your default browser at `http://localhost:3000`.

### Deep Dive: Core Components
- **`App.js`:** The brain of the application. It stores the `searchTerm` string and the `movies` array state. The asynchronous `searchMovies` method handles the fetch request and catches any network errors, populating the global movie grid. It conditionally renders either a grid of populated `<MovieCard />` elements, or a "No movies found" fallback state.
- **`MovieCard.jsx`:** A presentational (dumb) component designed strictly to output HTML based on the `movie` object passed to it. It manages zero state, purely structuring the individual movie's poster image, type, title, and release year for the CSS grid.

### Available Scripts
- `npm start`: Runs the application in development mode with hot-reloading.
- `npm run build`: Bundles the React application for production deployment.
- `npm test`: Launches the interactive test runner.
