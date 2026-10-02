RimModManager is a desktop mod manager for **RimWorld**. It aims to consolidate mod scanning, sorting, backup, Workshop management, log troubleshooting, and common utility tools into a single interface, thereby eliminating the need to manually browse folders or constantly switch between windows.

## Key Features

- Mod scanning and list management
- Load order viewing, saving, backup, and comparison
- Rule editing, dependency handling, and issue alerts
- Workshop and Git repository content management
- Scanning and cleanup of residual mod files
- Texture optimization utilities
- Mod list export
- Game log viewing and troubleshooting assistance
- AI assistant capabilities

## Tech Stack

- Backend: Python 3.11
- Frontend: Vue 3 + Vite
- Desktop Shell: pywebview
- Dependency Management: uv
- Testing: pytest
- Packaging: PyInstaller

## Runtime Environment

The project is currently designed and validated primarily as a **Windows desktop application**. Prerequisites:

- Python 3.11+
- Node.js 18+
- `uv`
- **WebView2 Runtime** (for Windows)
- RimWorld base game and the mod environment to be managed

## Quick Start

### 1. Clone the repository

```powershell
git clone <your-repo-url>
cd RimModManager
```

### 2. Install Python dependencies

```powershell
uv sync
```

### 3. Install frontend dependencies

```powershell
cd frontend
npm install
cd ..
```

## Launch Methods

### Method 1: Frontend Development Mode

Start the frontend development server first:

```powershell
cd frontend
npm run dev
```

Then return to the project root directory to launch the desktop application:

```powershell
cd ..
uv run python main.py
```

Notes:

- When the frontend development server (`http://localhost:5173`) is available, the application will prioritize connecting to it.
- This method is suitable for daily frontend UI development and integration testing.

### Method 2: Launch After Local Build

Build the frontend static files first:

```powershell
cd frontend
npm run build
cd ..
```

Then launch the application:

```powershell
uv run python main.py
```

Notes:

- When the frontend development server is not running, the application will attempt to load `frontend/dist/index.html`.
- This method more closely resembles the runtime behavior of the actual released application.

### Method 3: Browser Mode

In cases where desktop mode is affected by WebView2 or the local environment, you can also try:

```powershell
uv run python main.py --browser
```

## Testing

It is recommended to prioritize running the official test directory:

```powershell
uv run pytest -q tests
```

Notes:

- The repository contains some experimental local content; running `pytest` without arguments (scanning all directories) is not recommended.
- If you plan to open the project for collaboration later, it is recommended to organize the default test entry point into a stable state where tests pass reliably.

## Packaging

### PyInstaller

```powershell
uv run python pack_pyinstaller.py
```

### Nuitka

```powershell
uv run python pack_nuitka.py
```

Note:

- The packaging scripts are currently tailored to the author's local environment; adjustments may be required before reusing them on other machines.

## Project Structure

```text
backend/    Python backend, business logic, data, and managers
frontend/   Vue frontend interface
tests/      Formal tests
main.py     Application entry point
```

## Current Status

The project has a fairly complete functional framework but is still undergoing rapid iteration. Before public release, it is recommended to prioritize the following:

- More comprehensive screenshots and feature descriptions in the README
- A stable default test entry point
- A clearer strategy for synchronizing version numbers and release notes
- A more detailed GitHub release process and templates for issues/PRs

## Development Plan

The following items are currently in the planning or development stages; priorities and specific implementation methods are subject to change. ### Recent Improvements

- Added multilingual support, gradually filling in interface text, prompts, and feature descriptions.
- Optimized error messages, particularly for external tools, network requests, and AI-related errors.
- Improved window scaling and responsiveness; checked for overflow issues in pop-ups, panels, and text after scaling.
- Added "in-progress" states for buttons and asynchronous operations to reduce duplicate clicks and state ambiguity.
- Enhanced path and environment detection, including support for Steam, Workshop, user data directories, and auto-enable logic.
- Improved local storage security for sensitive configurations like passwords.
- Fixed usability issues such as rules not applying immediately after generation and accidental deletion of default environments during database resets.
- Refined local mod update detection, version difference logging, and synchronization timestamps.
- Improved interaction details for coexisting mods, duplicate mods, disabled lists, tag input, context menus, and group navigation.
- Optimized export capabilities, including game versioning, language pack filtering, supplementary info, and animated image support.

### Structural Evolution

- Unified front-end and back-end data models to reduce redundant fields and conversion logic, enhancing reusability.
- Adjusted code and directory structures to clarify functional boundaries and lower future maintenance costs.
- Gradually transitioned from a "file-stacking" organization to a more stable modular/plugin-based architecture.
- Optimized runtime memory usage to alleviate pressure caused by large lists, caching, and image-related features.
- Advancing capabilities such as patch parsing, community data display, and name-translation linking in conjunction with data model restructuring.
- Planning general features like settings search, new setting notifications, and default value validation.
- Exploring MCP integration to facilitate future connections with external tools or automation capabilities.

### AI & Translation Enhancements

- AI-assisted completion for organizing search recommendations, groups, and tags.
- Expanded mod description translation to key areas such as mod details and Workshop search results.
- Added fallback support to use Workshop descriptions as AI input when local mod descriptions are insufficient. Mod translation language pack generation, supporting one-click structure generation, initial AI translation, and collaborative human proofreading
- The language pack analysis/generation editor is designed for independent management while maintaining synchronization with the main manager

### Feature Extensions

- Continued enhancement of save file management capabilities, including export, modification, organization, and cleanup
- Visualization of mod dependencies, presenting relationships—such as dependencies, prerequisites, and conflicts—via an intuitive star-map diagram
- Visualization of definition dependencies, providing unified tracking across vanilla definitions, new mod additions, overrides, and patch modifications
- Analysis of definition issues, checking for problems such as modification order conflicts, missing dependencies, and invalid references, while assisting in rule generation or optimizing automatic sorting
- Mod definition editor, supporting the browsing and editing of common internal mod definitions and properties
- Enhanced definition editor, supporting the creation of simple definition mods and patch mods, as well as content extensions based on dependency mods
- Added support for multiplayer compatibility rules

### Notes

- Some items in the plan above are interconnected—such as definition visualization, issue analysis, sorting rule optimization, and editor capabilities—and essentially belong to the same broader feature stream
- Certain items are better suited for implementation after refactoring, rather than being added piecemeal as scattered patches
- Consequently, actual development will prioritize features that offer the greatest improvements to stability, maintainability, and user experience


## License

MIT
Send feedback
Translation results available
