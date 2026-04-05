# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Spendly** is a Flask-based expense tracking web application. This is an educational project with incremental implementation steps (some routes are placeholders marked "coming in Step X").

## Development Commands

### Running the Application
```bash
# Activate virtual environment
source venv/bin/activate

# Run the Flask development server
python app.py
```
The app runs on http://localhost:5001 with debug mode enabled.

### Testing
```bash
# Activate virtual environment first
source venv/bin/activate

# Run all tests
pytest

# Run specific test file
pytest tests/test_filename.py

# Run with verbose output
pytest -v
```

### Database Operations
Database operations are handled in `database/db.py`:
- `get_db()` - Returns SQLite connection with row_factory and foreign keys enabled
- `init_db()` - Creates all tables (uses CREATE TABLE IF NOT EXISTS)
- `seed_db()` - Inserts sample data for development

The SQLite database file is `expense_tracker.db` (gitignored).

## Architecture

### Project Structure
```
app.py                  # Main Flask application and route definitions
database/
  __init__.py
  db.py                 # Database connection and initialization
templates/
  base.html             # Base template with navbar and layout
  landing.html          # Home page
  login.html            # Login page
  register.html         # Registration page
  terms.html            # Terms of service
  privacy.html          # Privacy policy
static/
  css/
    style.css           # Global styles
    landing.css         # Landing page specific styles
  js/
    main.js             # Client-side JavaScript
```

### Template System
- All templates extend `base.html` using Jinja2 template inheritance
- Base template includes navbar with "Spendly" branding and navigation links
- Uses Google Fonts: DM Serif Display and DM Sans

### Routes Architecture
The application has two categories of routes:

**Implemented Routes:**
- `/` - Landing page
- `/register` - User registration
- `/login` - User login
- `/terms` - Terms of service
- `/privacy` - Privacy policy

**Placeholder Routes** (to be implemented):
- `/logout` - Step 3
- `/profile` - Step 4
- `/expenses/add` - Step 7
- `/expenses/<int:id>/edit` - Step 8
- `/expenses/<int:id>/delete` - Step 9

### Key Implementation Notes
- Port 5001 is used to avoid conflicts with other services
- Debug mode is enabled for development
- SQLite database with row_factory for dictionary-like row access
- Foreign key constraints are enabled in the database
