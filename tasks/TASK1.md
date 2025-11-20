# BookByte: MVP Infinite-Scroll Paragraph Feed for Public Domain Books

## Overview
Build an MVP web app that displays an infinite vertical scrolling feed of paragraphs from public-domain English and Chinese books. Each “card” is a single paragraph, randomly selected from all stored books. Users are anonymous but have a persistent identifier so their actions can be saved.

This is the first milestone of a longer-term codebase. Future milestones will add:
- Text-to-speech
- Comments
- Reactions
- Opening full books in context

---

## Core Reading Experience
- Vertical feed interface  
- Each feed item is one paragraph  
- Paragraphs selected randomly across all books  
- Short paragraphs fit on screen  
- Long paragraphs scroll horizontally  
- Scrolling up/down loads a new random paragraph  

---

## Supported Languages & Book Formats
- English and Chinese  
- Import books from public-domain sources (e.g., Project Gutenberg)  
- Support EPUB, TXT, or similar formats  

**Backend Parsing Produces:**
- Book records (title, author, language, source info)  
- Individual paragraph records  

---

## User Identity & Storage
- No login/signup  
- Generate unique ID stored in `localStorage`  
- ID used to associate events  
- Users can export/import the identifier  

---

## User Actions (Event-Based)
Each paragraph card includes:
- Heart  
- Like  
- Dislike  
- Bookmark  
- Copy  

**Event Details:**
- Every action stored with user identifier  
- Bookmarks support future bookmarked pages  
- Copy button copies paragraph text (MVP)  

---

## Backend Requirements (Django + SQLite)
Use Django; DRF optional but recommended.

### Models
- **Book**  
  - title, author, language, source, format  
- **Paragraph**  
  - text, book reference, optional location  
- **UserIdentifier**  
- **Event**  
  - user identifier  
  - paragraph  
  - event type (heart, like, dislike, bookmark, copy)  
  - timestamp  

### APIs
- Get Random Paragraph  
- Record Event  
- Get User Events (optional)  

### Data Import Tools
Provide script/management command to:
- Load EPUB/TXT files  
- Parse paragraphs  
- Populate Book + Paragraph tables  

---

## Frontend Requirements (React)
- Infinite scroll feed  
- Each card shows:
  - Paragraph text  
  - Book title + author  
  - Action buttons  
  - Short paragraphs fully visible  
  - Long paragraphs scroll horizontally  
- Store & manage unique user identifier  
- REST calls to fetch paragraphs + record events  
- Simple UI  

---

## Suggested Frontend Structure
- **src/**
  - **components/**
    - ParagraphCard.jsx  
    - ActionButtons.jsx  
    - IdentifierManager.jsx  
  - **pages/**
    - FeedPage.jsx  
  - **services/**
    - api.js  
  - App.jsx  
  - index.jsx  

---

## Suggested Backend Structure
- **project_root/**
  - manage.py  
  - **project/** (settings, urls)  
  - **core/**
    - models.py (Book, Paragraph, UserIdentifier, Event)  
    - views.py (API endpoints)  
    - serializers.py  
    - urls.py  
    - **management/commands/**
      - import_books.py  

---

## MVP Scope (This Task Only)

### Included
- Infinite random paragraph feed  
- English + Chinese  
- Anonymous identifier system (export/import)  
- Event tracking (heart/like/dislike/bookmark/copy)  
- Copy paragraph text  
- SQLite persistence  
- Scripts for importing/splitting books  
- Functional React frontend + Django backend  
- Clear local setup README  

### Not Included (future milestones)
- Text-to-speech  
- Comments  
- More reaction types  
- Reading paragraphs in full book context  
- Ask AI about paragraph  
- Auto-translation  
- Deployment  