# BillVault – AI Bill Scanner (Android)

Android app built from a Google Colab notebook. Scan electricity, property tax, water and LIC premium bills; Gemini AI extracts the fields; data and bill photos sync to Google Sheets and Drive.

## Tech stack
- Android WebView app (Java) + React UI
- Google Gemini API (auto model discovery)
- Google Apps Script (Sheets + Drive backend)
- Google Colab (builds the APK)

## Setup
1. Get a free Gemini API key from aistudio.google.com and paste it in Cell 1 (do not commit it).
2. Create a Google Sheet, then deploy the Apps Script (shown in the app's Settings) as a Web App.
3. Put your own Sheet ID in the script and your Web App URL in the HTML (`SHEET_URL`).
4. Run Cells 1 to 5 in order to build and download the APK.

## Privacy note
No personal data is included. Use your own Sheet ID, API key and Web App URL, and never commit them.
