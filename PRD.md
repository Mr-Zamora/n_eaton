# PRD: NBA Player Stat Viewer & Simulator (AI Coding Guide)

**Version:** 1.1 (AI Focused)
**Date:** 2025-05-13
**Author:** [Your Name]

---

**IMPORTANT INSTRUCTIONS FOR AI ASSISTANT:**

1.  **Purpose:** This document is the **single source of truth** for building the "NBA Player Stat Viewer & Simulator" Flask application. Adhere to it strictly.
2.  **Scope Adherence:** Only implement features explicitly listed in the **Functional Requirements** (Section 5) and respect the **Boundaries** (Section 7). Do **NOT** add features not specified here unless explicitly asked later.
3.  **Technology Stack:** Use **ONLY** the technologies specified in the **Technology Stack** (Section 8). Do not introduce other frameworks, libraries, or databases without prior instruction.
4.  **Incremental Development:** Generate code **incrementally** when requested (e.g., "Help me create the Flask route for displaying all players," "Generate the HTML template for the player detail page"). Do not generate the entire application at once unless specifically asked.
5.  **Code Style & Standards:**
    *   Follow **PEP 8** guidelines for Python code.
    *   Use clear, meaningful variable and function names.
    *   Include comments for complex logic or non-obvious sections.
    *   Write modular code (use functions, potentially classes later if complexity increases).
    *   Implement basic error handling (e.g., `try-except` blocks for file I/O, API calls, database operations).
6.  **Placeholders:** Use clear placeholders for sensitive information (like API keys) or data that will be loaded later. For example: `API_KEY = os.getenv("GEMINI_API_KEY")` or `<!-- Player data will be loaded here -->`. Use dummy data for initial layout/testing where appropriate.
7.  **Database Schema:** Strictly follow the **Data Model / Schema** (Section 9) when generating database interaction code (e.g., using Flask-SQLAlchemy).
8.  **Project Structure:** Adhere to the **Project Structure** guidelines (Section 11) when creating files and organizing code.
9.  **Clarity:** If any requirement is unclear or seems contradictory, please ask for clarification before generating code.
10. **Focus on MVP:** Prioritize features marked as "Must Have" for the Minimum Viable Product (MVP).

---

## 1. Overview & Goal

*   **Application Name:** NBA Player Stat Viewer & Simulator
*   **Core Idea:** A Python Flask web application allowing users to:
    *   View NBA player profiles (stats, photos) for the 2024-2025 season.
    *   Compare selected players side-by-side.
    *   Simulate hypothetical matchups (1v1 to 5v5) based on player stats.
    *   Receive AI-generated (Google Gemini) text commentary for simulations.
*   **Primary Goal:** Create a simple, engaging, and functional tool for NBA fans focusing on data viewing, comparison, and basic AI-driven simulation.

## 2. Problem Statement

Users lack a simple, integrated web tool to view 2024-2025 NBA player stats, directly compare players, and simulate matchups with engaging AI commentary, all within one beginner-friendly interface.

## 3. Core Objectives / Success Criteria (MVP)

The application will be considered successful for its initial version (MVP) if:

*   [X] Users can navigate to a page listing all players from the loaded dataset. (FR1)
*   [X] Users can click a player to view their detailed profile (stats, photo, team, position). (FR2)
*   [X] Users can select two players and see their stats compared side-by-side. (FR3)
*   [X] Users can select players (1-5 per side) for a simulated matchup. (FR4)
*   [X] A basic simulation runs based on selected players' stats, producing a winner and score. (FR5)
*   [X] The simulation results (score, winner) are displayed clearly. (FR6)
*   [X] The system successfully calls the Gemini API with simulation results and displays the generated text commentary. (FR7)
*   [X] Basic navigation between Home, Players, Compare, and Simulate sections exists. (FR8)
*   [X] The application is reasonably responsive on desktop and mobile viewports. (NFR1)
*   [X] Core pages load within an acceptable time (< 3-4 seconds). (NFR2)

## 4. Target Audience

*   NBA Fans (13+)
*   Fantasy Basketball Players
*   Sports Data Enthusiasts
*   Beginner Python/Flask developers

## 5. Functional Requirements (FR)

| ID  | Requirement               | Description                                                                                                                               | Priority  |
| :-- | :------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------- | :-------- |
| FR1 | View all NBA players      | Display a searchable/filterable list or grid of players from the 2024-25 dataset. Each item should link to the player's detail page (FR2). | Must Have |
| FR2 | View single player profile | Display comprehensive details for one player: Name, Team, Position, Key Stats (Points, Rebounds, Assists etc.), Photo URL/Image.          | Must Have |
| FR3 | Compare two players       | Allow user selection of two players. Display their profiles (FR2 format) side-by-side for easy visual comparison of stats.                 | Must Have |
| FR4 | Select players for matchup | Provide a UI (e.g., checkboxes, drag-and-drop) for users to select 1 to 5 players for 'Team A' and 'Team B'. Must validate selections.   | Must Have |
| FR5 | Simulate a matchup        | **Input:** Selected player lists (Team A, Team B) and their relevant stats. **Process:** Run a *simple* algorithm comparing team aggregate stats (or simplified player interactions) to determine a winner and generate a plausible score. **Output:** Winner (Team A/B), Score (e.g., 105-101). **Keep logic simple initially.** | Must Have |
| FR6 | Show match results        | Display the simulation output (Winner, Score from FR5) clearly on a results page. Optionally highlight top performers based on input stats. | Must Have |
| FR7 | Generate AI commentary    | **Input:** Simulation results (teams, winner, score, key stats/players involved). **Process:** Send this data in a structured prompt to the Google Gemini API. **Output:** Display the returned text commentary below the match results (FR6). Handle API errors gracefully (e.g., show "Commentary unavailable"). | Must Have |
| FR8 | Basic navigation          | Implement a simple navigation bar (header/sidebar) with links to Home, Players (FR1), Compare (FR3), Simulate (FR4).                      | Must Have |

## 6. Non-Functional Requirements (NFR)

*   **NFR1: Responsive Design:** Must render legibly and be usable on standard desktop, tablet, and mobile screen sizes. Use relative units (%, vw) and CSS media queries.
*   **NFR2: Performance:** Aim for page load times under 3 seconds for core views. Simulation time should be quick (< 5 seconds). Optimize database queries.
*   **NFR3: Usability:** Clean, intuitive UI. Clear instructions. Consistent layout across pages.
*   **NFR4: Safe AI Integration:** Use environment variables for API keys (`python-dotenv`). Sanitize inputs sent to API (if applicable). Implement basic filtering or review of AI output if needed (though initially trust filtered Gemini output). Handle API rate limits/errors gracefully.
*   **NFR5: Maintainable Code:** Adhere to PEP 8. Use functions/modules logically. Follow project structure (Section 11). Add comments for complex logic.
*   **NFR6: Lightweight Setup:** Use SQLite for the database. Minimize external dependencies where possible.
*   **NFR7: Data Management:** Player data (stats, photos) needs loading into the DB. Plan for a script (`load_data.py`?) to populate the database from a source file (CSV/JSON). The exact source needs identification, but assume a structured file exists.

## 7. Boundaries (Out of Scope for MVP)

*   ❌ User Authentication (Login/Registration)
*   ❌ Saving user data (teams, comparisons, simulation history)
*   ❌ Real-time data updates during live NBA games
*   ❌ Betting or Fantasy League integration
*   ❌ Multiplayer or interactive simulation control
*   ❌ Complex statistical modeling or physics engine for simulation
*   ❌ User ability to *edit* player stats
*   ❌ Admin panel for managing data

## 8. Technology Stack (**Strictly Adhere**)

*   **Programming Language:** Python (3.9 or higher recommended)
*   **Web Framework:** Flask
*   **Database:** JSON file (e.g., `players.json`)
*   **Database Toolkit:** Python's built-in `json` module for reading/writing data.
*   **Frontend:** HTML5, CSS3 (Potentially Bootstrap 5 for faster styling/responsiveness - confirm if allowed/desired), Vanilla JavaScript (if needed for minor interactivity, avoid heavy JS frameworks).
*   **Templating Engine:** Jinja2 (comes with Flask)
*   **AI Service:** Google Gemini API
*   **API Interaction:** Python `requests` library or Google's official Python client library for Gemini.
*   **Environment Management:** `venv`
*   **Dependency Management:** `requirements.txt`
*   **Secrets Management:** `python-dotenv` (for API Keys)
*   **Version Control:** Git / GitHub (or GitLab)

## 9. Data Model / Schema (JSON)

**(Use a single JSON file, e.g., `players.json`)**

Each player will be represented as a JSON object in a list. Example player entry:

```json
{
  "id": 1,
  "name": "LeBron James",
  "team": "Lakers",
  "position": "SF",
  "image_url": "https://example.com/lebron.jpg",
  "pts_per_game": 27.5,
  "reb_per_game": 8.2,
  "ast_per_game": 7.9,
  "fg_pct": 0.51,
  "ft_pct": 0.72,
  "three_p_pct": 0.36,
  "other_stats": {"blocks": 0.8, "steals": 1.2}
}
```

*   **Note:** The `other_stats` field is an optional dictionary for extra stats.
*   **Assumption:** The app will read from and write to `players.json` for all player data CRUD operations.
*   **Data Loading:** A script (`load_data.py`) can convert from CSV/other formats to `players.json` if needed.

## 10. API Integration (Google Gemini)

*   **Purpose:** To generate engaging play-by-play text commentary for simulated games (FR7).
*   **Trigger:** After a simulation (FR5) completes and results (FR6) are generated.
*   **Input Data (to send to Gemini):**
    *   Team A player names/key stats
    *   Team B player names/key stats
    *   Final Score
    *   Winning Team
    *   (Optional) Key simulated events or top performers identified by the simple simulation logic.
*   **Prompt Structure (Example - Needs Refinement):**
    ```text
    You are an NBA commentator. Generate a short, exciting play-by-play summary for a simulated basketball game.
    Team A Players: [List Player Names/Key Stat]
    Team B Players: [List Player Names/Key Stat]
    Final Score: Team A [Score A] - Team B [Score B]
    Winner: Team [A/B]
    Focus on the final moments or key players based on the stats provided. Keep it under 150 words.
    ```
*   **Output Expected:** A single block of text containing the commentary.
*   **Error Handling:** If the API call fails (network error, API key issue, rate limit), display a default message like "AI commentary could not be generated at this time."
*   **Security:** The Gemini API key **MUST** be stored in a `.env` file and loaded using `python-dotenv`, never hardcoded in the source code.

## 11. Project Structure (Recommended)

nba-simulator/
│
├── app.py # Main Flask application file (routes, app setup)
├── players.json # Player data storage (main data source)
├── load_data.py # Script to convert/load data from CSV/other formats into players.json (optional)
├── requirements.txt # Python dependencies
├── .env # Environment variables (API Keys) - !!! Add to .gitignore !!!
├── .gitignore # Files/folders to ignore in Git (e.g., .env, pycache, instance/)
│
├── static/ # Static files (served directly by web server)
│ ├── css/
│ │ └── style.css # Custom CSS rules
│ ├── js/
│ │ └── script.js # Custom JavaScript (if needed)
│ └── img/
│ └── (placeholder_images etc.)
│
├── templates/ # Jinja2 HTML templates
│ ├── layout.html # Base template (navbar, footer)
│ ├── index.html # Home page
│ ├── players.html # List all players (FR1)
│ ├── player_detail.html # Show single player (FR2)
│ ├── compare.html # Player comparison UI (FR3)
│ ├── simulate.html # Matchup selection UI (FR4)
│ └── results.html # Display simulation results & commentary (FR6, FR7)
│
└── instance/ # SQLite database file will be stored here (often configured in Flask)
└── nba_data.db

*   **Note:** For simpler projects, routes might stay in `app.py`. If routes become numerous, consider a `routes/` blueprint structure later.

## 12. Coding Standards & Best Practices (Recap for AI)

*   **Language:** Python 3.9+
*   **Framework:** Flask
*   **Style:** PEP 8
*   **Comments:** Explain complex logic. Docstrings for functions preferable.
*   **Modularity:** Use functions. Keep routes focused. Use `models.py` for DB definitions.
*   **Error Handling:** Basic `try-except` blocks for I/O, DB, and API calls. Provide user-friendly feedback on errors.
*   **Security:** Use `.env` for secrets. Be mindful of data sent to external APIs. No hardcoded credentials.
*   **Dependencies:** List all in `requirements.txt`. Use a virtual environment (`venv`).
*   **Database:** Use a JSON file (`players.json`). Read/write data using Python's `json` module. No ORM or SQL models.
*   **Templates:** Use Jinja2 templating. Utilize template inheritance (`layout.html`). Keep logic minimal in templates.

---

**Conclusion:**

This document provides the blueprint for the NBA Player Stat Viewer & Simulator. AI assistant should refer to this document for all implementation details and constraints. Focus on delivering the MVP features first, ensuring adherence to the specified stack and best practices.
