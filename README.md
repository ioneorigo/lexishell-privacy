# LexiShell

LexiShell is a powerful and versatile Android dictionary application designed for language learners and researchers. It allows users to consolidate multiple offline dictionary databases and online resources into a single, unified search interface.

## Key Features

- **Unified Search**: Search across multiple dictionaries simultaneously with parallel lookup logic.
- **Linked Dictionaries (Zero-copy)**: Use dictionaries directly from their original location without importing them into the app's internal storage, saving significant device space.
- **Offline Support**: Powerful indexing and high-performance querying for large offline dictionary databases.
- **Advanced Navigation**: 
    - **Redirection**: Full support for MDict `@@@LINK` and heuristic "SEE" link detection across all formats.
    - **Breadcrumbs**: Automatic navigational breadcrumbs for hierarchical dictionary entries.
    - **Navigation History**: Back and forward navigation through your search result stack.
- **Media & Audio Excellence**: 
    - **Speex Support**: Native support for high-quality compressed Speex (`.spx`) audio.
    - **Multi-source Audio**: Play audio from internal ZIPs, MDD records, LSD overlays, and external ZIP files.
    - **TTS Fallback**: Integrated Text-to-Speech fallback when recorded audio is not available.
- **Smart Search & Suggestions**: 
    - **Word Normalization**: Advanced normalization for improved hit rates across different capitalization and accents.
    - **Fuzzy Search**: Smart suggestions when an exact match is not found.
- **Web Integration**: Add custom web dictionary templates (e.g., Wikipedia, Wiktionary) for seamless online lookups.
- **Library Management**: Reorder, rename, and toggle individual dictionaries to prioritize your preferred sources.
- **History & Favorites**: Keep track of your searches and bookmark important words.
- **Modern UI**: Full support for **Dark Mode** and **Material You** adaptive coloring.

## System Requirements

- **Minimum Android Version**: Android 7.0 (API Level 24 "Nougat") or newer.
- **Target Android Version**: Android 15 (API Level 36).

## Supported Formats & Versions

LexiShell supports a wide range of popular dictionary formats and their various versions:

- **ABBYY Lingvo**:
    - **Source (`.dsl`)**: Supports standard and compressed (`.dsl.dz`, `.dsl.gz`) DSL files.
    - **Compiled (`.lsd`)**: Supports a wide array of compiled versions across several product generations.
    
    | Internal ID | Human Readable Version | Notes |
    | :--- | :--- | :--- |
    | `0x110001` | **Lingvo 11** | System dictionary |
    | `0x120001` | **Lingvo 12** | System dictionary |
    | `0x131001` | **Lingvo x3** | System dictionary |
    | `0x132001` | **Lingvo x3** | User/Custom dictionary |
    | `0x141004` | **Lingvo x5** | System dictionary |
    | `0x142001` | **Lingvo x5** | User/Custom dictionary |
    | `0x145001` | **Lingvo x5** | Abbreviation dictionary |
    | `0x151005` | **Lingvo x6** | System dictionary |
    | `0x152001` | **Lingvo x6** | User/Custom dictionary |
    | `0x155001` | **Lingvo x6** | Abbreviation dictionary |

    - **Extras**: Handles abbreviation files (`*_abrv.dsl`) and media packages (`.zip`).
- **MDict**:
    - **Dictionary Data (`.mdx`)**: Full support for MDict versions **1.2** and **2.0**.
    - **Resource Data (`.mdd`)**: Supports resource packages for images and audio.
    - **Linking**: Support for linking MDict files directly from storage.
- **StarDict & DICTD**:
    - **Core Support**: Handles `.idx` (including gzipped), `.dict` (including dictzip/gzipped), `.ifo`, and `.syn` file sets.
    - **DICTD**: Compatible with DICTD `.index` files.
    - **Metadata**: Preserves rich metadata including author, email, and dictionary descriptions.
- **Web Templates**:
    - Custom URL search patterns (e.g., `https://en.m.wikipedia.org/wiki/%s`) to integrate any website or MediaWiki instance as a dictionary source.

## Project Architecture

LexiShell follows the **MVVM (Model-View-ViewModel)** architectural pattern to ensure a clean separation of concerns and maintainability.

### High-Level Structure

- **UI Layer (Jetpack Compose)**:
    - `MainActivity.kt`: The main entry point and UI orchestrator.
    - `SearchScreen`: The primary interface with collapsible article cards and navigation history.
    - `LibraryScreen`: Management of installed dictionaries, linking, and metadata editing.
    - `SavedScreen`: Access to favorites and search history.
- **ViewModel Layer**:
    - `DictionaryViewModel.kt`: Manages application state, parallel search logic, and coordinates imports/linking.
    - `SettingsViewModel.kt`: Manages user preferences including Theme Mode and Adaptive Coloring.
- **Data Layer**:
    - **Room Database**: `AppDatabase.kt` stores headwords, history, and favorites.
    - **Optimized Storage**: Definitions are stored in a high-speed binary `.dat` file to ensure the database remains lightweight and responsive.
    - **Repository**: `DictionaryRepository.kt` acts as a single point of access for all data operations, including linked dictionary resolution.
    - **Modular Parsers**: Specialized parsers for Lingvo, MDict, and StarDict handle complex data extraction and rendering.

## Getting Started

1.  **Install the App**: Build and run the project on your Android device.
2.  **Add Dictionaries**: Navigate to the **Library** tab and use the import or link buttons to add your `.dsl`, `.lsd`, `.mdx`, or StarDict files.
    - *Tip*: Use **Direct Link** to save storage space by using files directly from your Downloads or SD card.
3.  **Search**: Go to the **Search** tab and start looking up words!
