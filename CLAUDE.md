# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **single-file HTML WYSIWYG Editor** - a complete web-based rich text editor with multi-page support, built entirely in vanilla HTML, CSS, and JavaScript without any external dependencies or build process.

## Architecture

### Single-File Design
- **Everything in `index.html`**: The entire application (HTML structure, CSS styles, and JavaScript logic) is contained in one self-contained file
- **No build process**: Simply open `index.html` in a web browser to run the application
- **No dependencies**: Uses only vanilla web technologies - no frameworks, libraries, or external resources

### Core Components
1. **Page Management System**: Multi-page website editor with create/rename/delete functionality
2. **Triple-View Editor**: Visual WYSIWYG editor, HTML code editor, and live preview modes
3. **Rich Text Toolbar**: Full formatting controls (bold, italic, headings, lists, links, images)
4. **Project Persistence**: Local storage auto-save + JSON export/import
5. **HTML Export**: Generates complete static websites with navigation

### Key Data Structures
- `pages` object: Stores all page content keyed by page ID
- `currentPage`: Tracks the active page being edited
- `currentTab`: Tracks current editor view (visual/code/preview)
- Auto-sync between visual and code editors via `syncVisualToCode()` and `syncCodeToVisual()`

### Core Functions (`index.html:477-994`)
- **Page Management**: `createNewPage()`, `renamePage()`, `deletePage()`, `switchToPage()`
- **Editor Sync**: `syncVisualToCode()`, `syncCodeToVisual()`, `updatePreview()`
- **Text Formatting**: `formatText()` using `document.execCommand()`
- **HTML Formatting**: `formatHTML()` with custom indentation logic
- **Project I/O**: `saveProject()`, `loadProject()`, `exportProject()`
- **Local Storage**: `saveToLocalStorage()`, `loadFromLocalStorage()`

## Development Workflow

### Testing Changes
1. Open `index.html` directly in a web browser
2. Test all editor functions (formatting, page management, export)
3. Verify auto-save and project load/save functionality
4. Test responsive design on mobile devices

### Making Modifications
- Edit the single `index.html` file
- CSS is in `<style>` tags (lines 7-333)
- JavaScript is in `<script>` tags (lines 477-994)
- HTML structure is lines 335-476

### No Build Commands Needed
This project requires no build process, package managers, or development servers. All functionality is self-contained in the single HTML file.

## Development Constraints

**IMPORTANT**: This project must ONLY use vanilla HTML, CSS, and plain JavaScript. Do not introduce:
- External libraries or frameworks (React, Vue, jQuery, etc.)
- Package managers (npm, yarn, etc.)  
- Build tools (webpack, vite, etc.)
- TypeScript or other transpiled languages
- External CSS frameworks (Bootstrap, Tailwind, etc.)

All code must remain in the single `index.html` file to maintain the project's self-contained nature.