# Profiles Directory App

**Student Name:** [YOUR NAME HERE]  
**Student ID:** [YOUR STUDENT ID HERE]  
**Course:** Mobile Programming - Lab 10 / React Native Lab 5

## 📱 Project Overview

This project is a real-world React Native application that demonstrates networking, API integration, and asynchronous operations. The app communicates with a local Express.js server to fetch, display, and manage user profile data.

Key concepts implemented in this project:
* **Networking:** Fetching data using `Axios` from a REST API.
* **Pagination:** Efficiently loading data in chunks using `FlatList` and `onEndReached`.
* **Navigation:** Using `React Navigation` (Native Stack) to move between list and detail views.
* **Error Handling:** Robust handling of network errors, timeouts, and 404 states with "Retry" functionality.
* **Environment Variables:** Securely managing API endpoints using `.env` files.

---

## 🚀 Features

* **Paginated List:** Displays a list of profiles that loads more data as you scroll down.
* **Pull-to-Refresh:** Users can pull down the list to reload data from the server.
* **Dynamic Detail Screen:** Tapping a user navigates to a details page where full profile data is fetched dynamically based on the ID.
* **Loading States:** Visual feedback (Spinners) during data fetching.
* **Error Management:** * Handles "Network Error" (e.g., server down).
    * Handles "404 Not Found" (invalid profile).
    * Provides a "Retry" button for failed requests.

---

## 🛠️ Prerequisites

Before running the application, ensure you have the following installed:
* **Node.js** and **npm**
* **Expo Go** app installed on your physical device (iOS or Android).
* **ProfilesServer**: The local Express.js server provided for this lab.

---

## ⚙️ Setup & Installation

### Step 1: Start the Backend Server
This app requires the local API server to be running first.

1.  Navigate to the `ProfilesServer` folder (provided separately).
2.  Install server dependencies:
    ```bash
    npm install
    ```
3.  Start the server:
    ```bash
    node server.js
    ```
    > **Note:** The server will run on port **3000**. Keep this terminal window open.

### Step 2: Setup the React Native App
1.  Clone or download this repository.
2.  Navigate to the project directory:
    ```bash
    cd ProfilesApp
    ```
3.  Install dependencies:
    ```bash
    npm install
    ```

---

## 🔌 Configuration (IP Address)

Since the app runs on your phone and the server runs on your computer, they must be on the **same WiFi network**. You cannot use `localhost`.

1.  **Find your Computer's Local IP Address:**
    * **Windows:** Run `ipconfig` in a terminal (Look for IPv4 Address).
    * **Mac/Linux:** Run `ifconfig` or `ip addr show`.
    * *Example IP:* `192.168.1.35`

2.  **Configure Environment Variables:**
    * Create a new file named `.env` in the root of `ProfilesApp`.
    * Copy the format from `.env.example`:
    ```env
    EXPO_PUBLIC_API_BASE_URL=http://<YOUR_COMPUTER_IP>:3000
    ```
    * **Replace `<YOUR_COMPUTER_IP>` with your actual IP address.**

    > **Example:** `EXPO_PUBLIC_API_BASE_URL=http://192.168.1.105:3000`

---

## ▶️ Running the App

1.  Ensure the **Server** is running (Step 1).
2.  Start the **Expo** development server:
    ```bash
    npx expo start
    ```
    * If you changed the IP in `.env`, you may need to run: `npx expo start --clear`
3.  Scan the QR code displayed in the terminal using the **Expo Go** app on your phone.

---

## 📂 Project Structure
ProfilesApp/ ├── api/ │ └── client.js # Axios configuration & Error Interceptors ├── screens/ │ ├── ProfilesListScreen.js # Paginated FlatList & Pull-to-Refresh logic │ └── ProfileDetailScreen.js # Detailed view fetching specific ID ├── App.js # Navigation Stack Setup ├── .env # API Configuration (Not in repo) └── .env.example # Template for API Configuration
## ❓ Troubleshooting

* **Network Request Failed / Timeout:** * Ensure your phone and computer are on the same WiFi.
    * Check if the IP address in `.env` is correct.
    * Ensure your firewall is not blocking port 3000.
* **App crashes on start:**
    * Try clearing the cache: `npx expo start --clear`.