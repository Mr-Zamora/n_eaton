# AI Coding Workspace Rules (RULES.md)

**Important:**
- Always refer to [BEGINNER_ROADMAP.md](BEGINNER_ROADMAP.md) for the step-by-step beginner roadmap and incremental implementation steps.
- Always refer to [PRD.md](PRD.md) for the single source of truth on requirements, features, and technology stack.
- Use this file for core rules and standards, but check BEGINNER_ROADMAP.md and PRD.md before making decisions or coding.

**Purpose:** This file provides essential, persistent rules and context for the AI assistant building the "NBA Player Stat Viewer & Simulator" project. Refer to the full `PRD.md` for complete details when needed. Adhere strictly to these rules unless explicitly overridden.

---

## 1. Core Project Goal

*   **Build:** A Python Flask web application.
*   **Functionality:**
    *   View NBA player stats & profiles (2024-25 season).
    *   Compare selected players side-by-side.
    *   Simulate basic matchups (1v1 to 5v5) based on stats.
    *   Generate AI commentary for simulations using Google Gemini API.
*   **Primary Reference:** The detailed `prd.md` file is the **single source of truth** for requirements, features, and scope.

## 2. Strict Technology Stack (**Use ONLY These**)

*   **Language:** Python (3.9+)
*   **Framework:** Flask
*   **Database:** JSON file (e.g., `players.json`)
*   **Database Toolkit:** Python's built-in `json` module for reading/writing data.
*   **Frontend:** HTML5, CSS3, Vanilla JavaScript (if needed, keep minimal), Jinja2 (Flask templating)
*   **AI Service:** Google Gemini API
*   **API Calls:** Python `requests` library or Google's official client library.
*   **Environment:** `venv`
*   **Dependencies:** `requirements.txt`
*   **Secrets:** `python-dotenv` for `.env` file.
*   **Version Control:** Git

## 3. Core Coding Rules & Standards

*   **Adherence:** Strictly follow instructions and requirements in `prd.md`.
*   **Scope:** **Only** implement features specified in `prd.md` (Section 5: Functional Requirements). **Do NOT** implement anything listed in Section 7 (Boundaries). Do not add extra features without explicit instruction.
*   **Incremental:** Generate code **incrementally** based on specific requests (e.g., "Create the player detail route"). Do not generate the whole application at once unless asked.
*   **Python:** Follow PEP 8 guidelines. Use clear variable/function names.
*   **Modularity:** Use functions. Follow the project structure outlined in `prd.md` (Section 11).
*   **Comments:** Add comments for complex logic or non-obvious code sections.
*   **Error Handling:** Implement basic `try-except` blocks for DB operations, file I/O, and API calls. Provide user-friendly error messages where appropriate.
*   **Security:** **NEVER** hardcode API keys or other secrets. Use `os.getenv()` to load from a `.env` file (ensure `.env` is in `.gitignore`).

## 4. Key Files & Structure

*   **Main Reference:** `prd.md` (for all details).
*   **This File:** `RULES.md` (for core, persistent context).
*   **Development Plan:** `ROADMAP.md` (for incremental development steps).
*   **Project Structure:** Follow the directory layout specified in `prd.md` (Section 11). Place files (app.py, players.json, templates, static) in their correct locations.
*   **Data Model:** Use the JSON structure for players defined in `prd.md` (Section 9). Each player is represented as a JSON object in a list.

## 5. Development Roadmap

Follow the incremental development process outlined in `ROADMAP.md`:

1. **Setup & Foundation**: Project structure, sample data, dependencies
2. **Core Flask App**: Basic app, templates, static files
3. **Player Data Features**: JSON data handling, player listings and details
4. **Comparison & Simulation**: Player comparison, team selection, simulation logic
5. **AI Integration**: Gemini API for game commentary
6. **Non-Functional & Polish**: Responsive design, performance, error handling

## 6. AI Integration (Gemini API)

*   **Purpose:** Generate text commentary for simulations (FR7 in `prd.md`).
*   **Trigger:** After simulation results are available.
*   **Input:** Send structured data (teams, players, score, winner) as defined in `prd.md` (Section 10).
*   **Output:** Display the returned text commentary. Handle API errors gracefully.
*   **API Key:** Must be loaded securely from `.env`.

## 7. Progress Tracking

*   Update the Progress Tracking Table in `ROADMAP.md` after completing each major step.
*   Mark completed tasks with [x] in the checklist.
*   Add notes about implementation decisions or challenges encountered.

---

**Reminder:**
- This `RULES.md` provides high-level, persistent guidance and coding standards.
- For specific implementation details, requirements, data structures, and scope boundaries, always consult the full `PRD.md` document.
- For incremental steps and progress tracking, always refer to `BEGINNER_ROADMAP.md`.