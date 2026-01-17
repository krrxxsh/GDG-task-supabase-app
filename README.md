# Dynamic Supabase Android App

## Resume Brief
**Android application with real-time backend integration using Supabase**  
Developed a native Android app that dynamically fetches and displays promotional content from Supabase backend with real-time updates. Implemented RESTful API integration, image loading with caching, and polling mechanism for live data synchronization.

## Project Overview
A production-ready Android application that demonstrates modern mobile development practices with cloud backend integration. The app connects to Supabase (an open-source Firebase alternative) to fetch and display promotional banners with text and images in real-time.

## Key Features
- **Real-time Data Updates**: Automatic polling mechanism that refreshes content every 5 seconds
- **RESTful API Integration**: Direct integration with Supabase REST API for data retrieval
- **Dynamic Content Display**: Fetches promotional messages, subtitles, and images from cloud database
- **Efficient Image Loading**: Glide library implementation for smooth image loading and caching
- **Error Handling**: Comprehensive error handling for network failures and data parsing
- **Clean UI/UX**: Material Design principles with responsive layouts

## Technologies & Libraries
- **Language**: Java
- **Platform**: Android SDK (API 26+)
- **Backend**: Supabase (PostgreSQL database with REST API)
- **Networking**: OkHttp 4.9.3
- **Image Loading**: Glide 4.12.0
- **Build System**: Gradle
- **Architecture**: MVC pattern with async callback handling

## Technical Implementation

### Architecture
- **SupabaseClient**: Singleton client for managing API requests to Supabase REST endpoints
- **MainActivity**: UI controller with lifecycle-aware polling mechanism
- **Real-time Sync**: Handler-based polling that respects activity lifecycle (pauses when app is in background)

### Key Components
1. **Data Fetching**: Asynchronous HTTP requests with OkHttp callbacks
2. **UI Updates**: Thread-safe UI updates using `runOnUiThread()`
3. **Concurrency Control**: Atomic boolean flag to prevent overlapping network requests
4. **Image Pipeline**: Glide with placeholder and center-crop transformations

### API Integration
- Connects to Supabase REST API with authentication headers
- Queries the `promo` table with sorting and limiting
- Parses JSON response and updates UI dynamically

## Setup Instructions

### Prerequisites
- Android Studio Arctic Fox or newer
- JDK 11 or higher
- Android SDK with API level 26 or higher
- Supabase account (for backend setup)

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/krrxxsh/GDG-task-supabase-app.git
   cd GDG-task-supabase-app
   ```

2. Open the project in Android Studio

3. Configure Supabase credentials in `SupabaseClient.java` (replace existing hardcoded values):
   ```java
   private static final String SUPABASE_PROJECT_URL = "your-project-url";
   private static final String SUPABASE_ANON_KEY = "your-anon-key";
   ```
   **Note**: The repository contains demo credentials. Replace them with your own Supabase project credentials.

4. Sync Gradle dependencies

5. Build and run on an emulator or physical device

### Database Setup
Create a `promo` table in your Supabase project with the following schema:
```sql
CREATE TABLE promo (
  id SERIAL PRIMARY KEY,
  message TEXT,
  subtitle TEXT,
  image_url TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);
```

## Skills Demonstrated
- Native Android development with Java
- RESTful API integration and consumption
- Asynchronous programming and threading
- Backend-as-a-Service (BaaS) integration
- JSON parsing and data handling
- Image loading optimization
- Lifecycle-aware component development
- Network error handling and user feedback
- Material Design implementation

## Future Enhancements
- WebSocket integration for true real-time updates
- Offline caching with Room database
- Push notifications for new promotions
- Admin panel for content management
- Analytics integration
- Multiple promo carousel

## License
This project was developed as part of GDG (Google Developer Groups) learning initiative.

---

**Developed by**: krrxxsh  
**Purpose**: Demonstrating Android development skills with modern backend integration  
**Tech Stack**: Android (Java) + Supabase + OkHttp + Glide
