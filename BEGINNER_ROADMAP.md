# BEGINNER_ROADMAP.md

**Important:**
- Always refer to [RULES.md](RULES.md) for coding standards, persistent rules, and project context.
- Always refer to [PRD.md](PRD.md) for the single source of truth on requirements, features, and technology stack.
- Use this roadmap as your step-by-step guide, but check RULES.md and PRD.md before making decisions or coding.

A step-by-step beginner-friendly roadmap for building the NBA Player Stat Viewer & Simulator. This plan focuses on UI, UX, and application flow first, with AI/API integration and environment variable setup left for a later stage. For detailed rules and requirements, see RULES.md and PRD.md.

---

## 1. Project Setup & Foundation

- [ ] Create your project folder structure:
  - `nba-simulator/`
    - `app.py`
    - `players.json`
    - `requirements.txt`
    - `templates/`
    - `static/`
    - `.gitignore`
- [ ] Set up a Python virtual environment (optional, but recommended).
- [ ] Add Flask and other basics to `requirements.txt` (Flask, requests, etc.).
  > **AI Prompt:**
  > Generate a requirements.txt for a beginner Flask project. Include Flask, requests, and any other essentials.
- [ ] Create a sample `players.json` file with 2-3 example players.
  > **AI Prompt:**
  > Give me a sample players.json file with 2-3 NBA player records, including name, team, position, points, rebounds, assists, and photo URL fields.
- [ ] Add `.gitignore` entries for `venv/`, `.env`, and `__pycache__/`.
  > **AI Prompt:**
  > What should I put in my .gitignore for a Python Flask project? Please include venv/, .env, and __pycache__/.

---

## 2. Build the UI/UX and Core Flow

- [ ] Create a basic Flask app in `app.py`.
  > **AI Prompt:**
  > Show me a minimal Flask app in app.py that runs and displays ‘Hello, NBA Simulator!’ on the home page.
- [ ] Add routes and templates for:
    - Home page (`/`)
    - List all players (`/players`)
    - Player detail view (`/player/<player_id>`)
    - Compare players (`/compare`)
    - Simulate matchup (`/simulate`)
  > **AI Prompt:**
  > Help me add Flask routes and Jinja2 templates for:
  > - Home page ('/')
  > - List all players ('/players')
  > - Player detail view ('/player/<player_id>')
  > - Compare players ('/compare')
  > - Simulate matchup ('/simulate')
- [ ] Use Jinja2 templates for all pages.
  > **AI Prompt:**
  > Give me a basic Jinja2 base template (layout.html) and an example page template that extends it for my Flask NBA app.
- [ ] Load player data from `players.json`.
  > **AI Prompt:**
  > How do I load player data from a JSON file (players.json) in Flask and use it in my routes?
- [ ] Use dummy data or placeholder messages for features not implemented yet (e.g., AI commentary).
  > **AI Prompt:**
  > How can I add a placeholder function in Flask for AI commentary, so my app shows ‘AI commentary will be added here’ until I’m ready to integrate the real API?

---

## 3. Focus on User Experience

- [ ] Make navigation clear and easy (navbar, links).
  > **AI Prompt:**
  > Show me how to add a navigation bar to my Flask/Jinja2 templates with links to all main pages.
- [ ] Use simple CSS or Bootstrap for basic styling and responsiveness.
  > **AI Prompt:**
  > How can I add Bootstrap to my Flask app for quick, responsive styling? Give me an example.
- [ ] Ensure forms and flows (selecting players, running a simulation) are intuitive.
  > **AI Prompt:**
  > Give me an example of a simple HTML form in Jinja2 for selecting players to compare or simulate.
- [ ] Display clear error messages if something goes wrong (e.g., missing player data).
  > **AI Prompt:**
  > How do I show user-friendly error messages in Flask if something goes wrong, like missing player data?

---

## 4. Version Control & Documentation

- [ ] Initialize a git repository and make your first commit.
  > **AI Prompt:**
  > What are the basic git commands to initialize a repo and make my first commit for this Flask project?
- [ ] Update this roadmap after each major step.
  > **AI Prompt:**
  > Suggest a format for updating my roadmap/checklist after I finish each step.
- [ ] Create and update a `CHANGELOG.md` after each significant change.
  > **AI Prompt:**
  > Give me a template for CHANGELOG.md and show how to add an entry after each significant change.

---

## 5. Prepare for Later AI/API Integration

- [ ] Where you would call an AI API (like Gemini), use a placeholder function:
    ```python
    def get_ai_commentary(simulation_data):
        # Placeholder for future AI integration
        return "AI commentary will be added here."
    ```
  > **AI Prompt:**
  > Write a Python function in app.py called get_ai_commentary that just returns a placeholder string for now.
- [ ] Display the output of this function in your simulation results page.
  > **AI Prompt:**
  > How do I display the output of my get_ai_commentary placeholder function in my Jinja2 template for simulation results?
- [ ] Do not worry about `.env` or API keys until you are ready for AI integration.
  > _(No AI prompt needed at this stage.)_

---

## 6. When Ready for AI/API Integration (Future)

- [ ] Add `python-dotenv` and set up a `.env` file for secrets.
  > **AI Prompt:**
  > Show me how to use python-dotenv in Flask to load API keys from a .env file.
- [ ] Replace your placeholder function with real API calls.
  > **AI Prompt:**
  > How do I connect my Flask app to the Gemini API to generate NBA commentary, using the API key from .env?
- [ ] Handle errors and security as described in the main documentation.
  > **AI Prompt:**
  > What’s the best way to handle errors and keep my API key secure when calling an external API in Flask?

---

**Tip:** Work in small steps, test often, and update this file as you go. Focus on getting the app flow and user experience right before adding advanced features.
