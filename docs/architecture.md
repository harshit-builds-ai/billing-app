# BillVault architecture

## Components

| Part | Role |
|---|---|
| Android WebView shell (Java) | Native wrapper that opens the camera/gallery and hosts the web UI |
| React UI | Screens for scanning, reviewing and settings, running inside the WebView |
| Gemini API | Reads the bill photo and returns the extracted fields as structured data |
| Google Apps Script Web App | Receives the extracted data and photo, writes a row to Google Sheets and saves the photo to Google Drive |
| Google Colab notebook | Generates the app files and builds the APK |

## Data flow

1. The user photographs a bill in the app.
2. The image is sent to the Gemini API with a prompt asking for structured fields.
3. The app posts the extracted data and the photo to the Apps Script Web App.
4. Apps Script appends a row to the Google Sheet and stores the photo in Drive.

## Design choices

- **Apps Script as backend:** no server to run or pay for, and the data stays inside the user's own Google account.
- **WebView + React:** the UI can change without rebuilding native screens.
- **Model discovery:** the app looks up an available Gemini model instead of hard-coding one, so a retired model name does not break it.
- **Colab build:** the APK can be produced without installing Android tooling locally.

## Known trade-offs

- Apps Script has quotas and no versioned API contract, so it suits personal use rather than many users.
- The API key is supplied by the person who builds the APK, so each build carries that person's key; do not share built APKs publicly.
- Extraction quality depends on photo quality and bill format; fields should be reviewed before they are relied on.
