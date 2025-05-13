# Development Roadmap: NBA Player Stat Viewer & Simulator

**Purpose:**
This roadmap is used by the AI assistant to code incrementally, track progress, and plan future development steps for the NBA Player Stat Viewer & Simulator project. It is updated as features are planned, started, and completed.

---

## 1. Setup & Foundation
- [x] **Create PRD.md**: Product requirements document as single source of truth.
- [ ] **Create ROADMAP.md**: Development tracking and planning (this file).
- [ ] **Project directory structure**: Create folders/files as per PRD.
- [ ] **Create sample `players.json`**: With a few example player records.
- [ ] **Create `.gitignore`**: Exclude `.env`, `__pycache__/`, etc.
- [ ] **Create `requirements.txt`**: Add Flask, python-dotenv, requests, etc.

## 2. Core Flask App Skeleton
- [ ] **Create `app.py`**: Basic Flask app, load config from `.env`.
- [ ] **Implement static file serving**: CSS, JS, images.
- [ ] **Create base template (`layout.html`)**: Navbar, footer, Bootstrap (if used).
- [ ] **Create home page (`index.html`)**: Welcome and navigation.

## 3. Player Data Features
- [ ] **Load player data from JSON**: Utility functions for CRUD.
- [ ] **List all players (`players.html`)**: Searchable/filterable.
- [ ] **Player detail page (`player_detail.html`)**: Show all stats, photo, etc.

## 4. Comparison & Simulation Features
- [ ] **Compare two players (`compare.html`)**: Select and view side-by-side.
- [ ] **Select teams for simulation (`simulate.html`)**: 1-5 per side, validate.
- [ ] **Simulate matchup logic**: Simple algorithm, output winner & score.
- [ ] **Show match results (`results.html`)**: Winner, score, top performers.

## 5. AI Integration
- [ ] **Gemini API integration**: Send simulation results, get commentary.
- [ ] **Display AI commentary**: On results page, handle errors gracefully.

## 6. Non-Functional & Polish
- [ ] **Responsive design**: CSS tweaks, mobile support.
- [ ] **Performance checks**: Fast page loads, efficient data access.
- [ ] **Error handling**: User-friendly messages for file/API errors.
- [ ] **Code cleanup/comments**: PEP 8, modularity, docstrings.

## 7. Future/Stretch Goals (Optional)
- [ ] **Player image uploads**
- [ ] **More advanced simulation logic**
- [ ] **Additional stats/filters**
- [ ] **Deployment (e.g., Netlify, Render, etc.)**

---

## Progress Tracking Table

| Step | Feature/Task | Status | Notes |
|------|--------------|--------|-------|
| 1    | PRD.md       | Done   | Complete as of 2025-05-13 |
| 2    | ROADMAP.md   | In Progress |  |
| ...  | ...          | ...    | ...   |

---

**How to Use:**
- The AI will update this file after each major coding step.
- Use the checklist and table to decide the next incremental coding task.
- Each new feature should be implemented in a separate, clearly described step.
- If priorities or requirements change, update this file and the PRD.md accordingly.
