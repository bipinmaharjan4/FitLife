# FitLife


  
<div style="text-align: justify; text-justify: inter-word;">
A modern fitness tracking application built with Kotlin for Android. Features workout routine management, equipment checklists with SMS delegation, and gym location geotagging with a beautiful blue/purple gradient theme.

</div>

## Features

-   **Firebase Authentication** - Secure email/password authentication
-   **Workout Routines** - Create and manage weekly workout plans with day-based filtering
-   **Equipment Checklist** - Track equipment with SMS delegation capabilities
-   **Geotagging** - Save and navigate to your favorite workout locations using Google Maps
-   **Dark Mode** - Beautiful deep blue dark theme with purple accents
-   **Progress Tracking** - Linear progress indicators for weekly workout completion
-   **Offline Support** - Local Room database for offline access to routines and data

## Design & UI

### Color Scheme
- **Primary Color**: Deep Blue (`#1565C0`) - Professional and energetic
- **Secondary Color**: Vibrant Purple (`#7B1FA2`) - Modern and dynamic
- **Accent Color**: Purple (`#9C27B0`) - Eye-catching highlights
- **Background**: Light Blue-Gray (`#E3F2FD`) - Clean and fresh
- **Dark Theme**: Deep Blue (`#1A237E`) with lighter blue surfaces

### UI Styling
- **Material Design 3** with custom styling
- **Rounded Corners**: 24dp for cards, 16-20dp for buttons and inputs
- **Elevated Cards**: Modern card design with appropriate shadows
- **Linear Progress Bars**: Clean progress indicators for workout tracking
- **Custom Icons**: Gradient-based launcher icon with fitness theme

### Layout Organization
- **Home Screen**: Quick Actions → Weekly Progress → Today's Workout → Upcoming Routines
- **Routines Screen**: Routines list at top, day filters at bottom
- **Profile Screen**: Settings first, stats below
- **Bottom Navigation**: Home → Map → Routines → Checklist → Profile

## Getting Started

### Prerequisites

-   Android Studio (latest stable version)
-   JDK 11 or higher
-   Android SDK with minimum API level 24

### Installation

1. **Configure Google Maps API**

    - Navigate to [Google Cloud Console](https://console.cloud.google.com/google/maps-apis)
    - Create a new project or select an existing one
    - Enable "Maps SDK for Android"
    - Create an API key
    - Copy `local.properties.example` to `local.properties`
    - Add your API key:

        ```properties
        MAPS_API_KEY=your_actual_api_key_here
        ```

2. **Configure Firebase** ⚠️ **IMPORTANT**

    **You must create your own Firebase project** to avoid data conflicts and ensure security.
    
    Quick steps:
    - Navigate to [Firebase Console](https://console.firebase.google.com)
    - Create a new project
    - Add an Android app with package name: `com.example.fitlife`
    - Download `google-services.json`
    - Replace the existing file in the `app/` directory
    - Enable Email/Password sign-in method in Firebase Authentication

3. **Build and Run**

    ```bash
    ./gradlew assembleDebug
    ```

    Alternatively, open the project in Android Studio and run directly.

## Project Structure

```
app/src/main/
├── java/com/example/fitlife/
│   ├── data/
│   │   ├── dao/              # Room database DAOs
│   │   ├── model/            # Data models
│   │   └── repository/       # Repository pattern
│   ├── ui/
│   │   ├── auth/             # Login and Registration
│   │   ├── checklist/        # Equipment checklist
│   │   ├── home/             # Dashboard
│   │   ├── map/              # Geotagging
│   │   ├── profile/          # User profile
│   │   └── routines/         # Workout routines
│   └── utils/                # Utility classes
└── res/
    ├── layout/               # XML layouts
    ├── navigation/           # Navigation graph
    ├── drawable/             # Icons and graphics
    └── values/               # Colors, strings, themes
```

## Tech Stack

| Component      | Technology         |
| -------------- | ------------------ |
| Language       | Kotlin             |
| Min SDK        | 24 (Android 7.0)   |
| Target SDK     | 34 (Android 14)    |
| Architecture   | Repository Pattern |
| Local Database | Room               |
| Authentication | Firebase Auth      |
| Maps           | Google Maps SDK    |
| UI Framework   | Material Design 3  |
| Image Loading  | Glide              |

## Code Architecture

### Naming Conventions
- **View Binding**: `viewBinding` for type-safe view references
- **Session Manager**: `authSession` for authentication state
- **Adapters**: `workoutAdapter`, `workoutListAdapter` for list management
- **Methods**: Descriptive names like `initializeViews()`, `configureRecyclerView()`, `fetchWorkoutData()`

### Key Patterns
- **Repository Pattern**: Data access abstraction layer
- **View Binding**: Type-safe view references
- **Coroutines**: Asynchronous operations and background tasks
- **Flow**: Reactive data streams for real-time updates
- **Navigation Component**: Fragment-based navigation with type-safe arguments

## Themes

| Mode  | Name         | Background Color | Primary Color |
| ----- | ------------ | --------------- | ------------- |
| Light | Light Blue   | `#E3F2FD`       | `#1565C0`     |
| Dark  | Deep Blue    | `#1A237E`       | `#64B5F6`     |

### Theme Features
- **Light Mode**: Clean blue-gray background with deep blue primary
- **Dark Mode**: Deep blue background with lighter blue accents
- **Gradient Backgrounds**: Blue to purple gradients in launcher and cards
- **Rounded UI Elements**: 16-24dp corner radius for modern look

## Security

The following files contain sensitive information and must not be committed to version control:

-   `local.properties` - SDK path and API keys
-   `app/google-services.json` - Firebase configuration (contains API keys)
-   `.env` or `.env.local` - Environment variables
-   `*.keystore` or `*.jks` files - Signing keys

These files are included in `.gitignore` by default.

## Development Notes

### Firebase Configuration
- **Action Required**: Create your own Firebase project before deployment
- Replace the existing `google-services.json` with your project's configuration file
- Enable Email/Password authentication in Firebase Console

### API Keys
- Google Maps API key required in `local.properties`
- FreeImage API key (optional) for image uploads
- All keys should be stored in `local.properties` (not committed to git)

## License

This project is for educational purposes.

## Credits

- Material Design 3 components
- Firebase Authentication
- Google Maps SDK
- Room Database
- Glide for image loading
