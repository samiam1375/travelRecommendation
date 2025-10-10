// travel_recommendation.js

// Global variable to store fetched data
let allTravelData = null;

// Function to fetch data from the JSON file
async function fetchTravelData() {
    try {
        const response = await fetch('travel_recommendation_api.json'); // Path to your JSON file
        if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
        }
        allTravelData = await response.json(); // Store data globally
        console.log("Fetched Travel Data:", allTravelData); // Log the data to the console
        return allTravelData;
    } catch (error) {
        console.error("Error fetching travel data:", error);
        return null;
    }
}

// Function to display recommendations
function displayRecommendations(recommendations) {
    const resultsContainer = document.getElementById('recommendationResults');
    resultsContainer.innerHTML = ''; // Clear previous results
    resultsContainer.style.display = 'flex'; // Show the results section using flex for card layout

    if (recommendations.length === 0) {
        resultsContainer.innerHTML = '<p style="text-align: center; width: 100%; font-size: 1.2em; color: #555;">No recommendations found for your search. Try "beach", "temple", a country like "Japan", or a city like "Sydney".</p>';
        return;
    }

    // Sort by name for consistent display (optional, but good for UX)
    recommendations.sort((a, b) => a.name.localeCompare(b.name));

    recommendations.forEach(item => {
        const card = document.createElement('div');
        card.classList.add('recommendation-card');

        const img = document.createElement('img');
        img.src = item.imageUrl;
        img.alt = item.name;
        card.appendChild(img);

        const name = document.createElement('h4');
        name.textContent = item.name;
        card.appendChild(name);

        const description = document.createElement('p');
        description.textContent = item.description;
        card.appendChild(description);

        resultsContainer.appendChild(card);
    });
}

// Function to handle search logic
async function handleSearch() {
    // Ensure data is fetched before searching
    if (!allTravelData) {
        await fetchTravelData();
        if (!allTravelData) {
            console.error("Could not fetch travel data. Cannot perform search.");
            return;
        }
    }

    const searchInput = document.getElementById('searchInput');
    const query = searchInput.value.toLowerCase().trim();
    let filteredResults = [];

    if (!query) {
        displayRecommendations([]); // Clear results if query is empty
        return;
    }

    // --- Search Logic ---

    // 1. Check for general category keywords first and prioritize them
    if (query.includes('beach') || query.includes('beaches')) {
        filteredResults = filteredResults.concat(allTravelData.beaches || []);
    } else if (query.includes('temple') || query.includes('temples')) {
        filteredResults = filteredResults.concat(allTravelData.temples || []);
    } else if (query.includes('country') || query.includes('countries')) {
        // If "country" is searched, return all cities from all countries
        allTravelData.countries.forEach(country => {
            filteredResults = filteredResults.concat(country.cities || []);
        });
    }

    // If we found results based on a general category keyword, display them and stop.
    // This ensures that typing "beach" shows ALL beaches, "temple" shows ALL temples, etc.
    if (filteredResults.length > 0) {
        // Remove duplicates in case some items were added through multiple paths (e.g., "Japan beach" might match "country" and "beach")
        const uniqueResultsMap = new Map();
        filteredResults.forEach(item => {
            uniqueResultsMap.set(item.name, item);
        });
        displayRecommendations(Array.from(uniqueResultsMap.values()));
        return;
    }


    // 2. If no general category keyword matched, proceed with specific name searches
    // Search for specific country names or city names
    allTravelData.countries.forEach(country => {
        if (country.name.toLowerCase().includes(query)) {
            // If country name matches, add all its cities
            filteredResults = filteredResults.concat(country.cities || []);
        } else {
            // Check for city name match within the country
            country.cities.forEach(city => {
                if (city.name.toLowerCase().includes(query)) {
                    filteredResults.push(city);
                }
            });
        }
    });

    // Search for specific temple names
    allTravelData.temples.forEach(temple => {
        if (temple.name.toLowerCase().includes(query)) {
            filteredResults.push(temple);
        }
    });

    // Search for specific beach names
    allTravelData.beaches.forEach(beach => {
        if (beach.name.toLowerCase().includes(query)) {
            filteredResults.push(beach);
        }
    });


    // Remove duplicates from filteredResults (if a city/place was matched multiple ways)
    const uniqueResultsMap = new Map();
    filteredResults.forEach(item => {
        uniqueResultsMap.set(item.name, item);
    });
    const uniqueResults = Array.from(uniqueResultsMap.values());


    displayRecommendations(uniqueResults);
}

// Function to handle clear logic (renamed from handleReset)
function handleClear() {
    document.getElementById('searchInput').value = ''; // Clear search input
    document.getElementById('recommendationResults').innerHTML = ''; // Clear results display
    document.getElementById('recommendationResults').style.display = 'none'; // Hide results section
}

// Event Listeners
document.addEventListener('DOMContentLoaded', async () => {
    // Fetch data once on load
    await fetchTravelData();

    const searchButton = document.getElementById('searchButton');
    const clearButton = document.getElementById('clearButton'); // Get the clear button element

    if (searchButton) {
        searchButton.addEventListener('click', handleSearch);
    }
    if (clearButton) {
        clearButton.addEventListener('click', handleClear); // Attach event listener to clearButton
    }
});
