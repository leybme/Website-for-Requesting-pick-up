# Gọi Xe Cứu Thương

This is a web application for requesting ambulance pickup. The application uses Firebase for backend services and integrates geolocation to capture the user's location.

## Features

- Display user ID from the URL.
- Capture the user's current location using the browser's geolocation API.
- Send a pickup request to Firebase Firestore.
- Monitor the status of the request in real-time.
- Display driver information once the request is accepted.

## Project Structure

```
index.html
```

- **`index.html`**: The main HTML file containing the UI and JavaScript logic.

## Technologies Used

- **HTML/CSS**: For the user interface.
- **JavaScript**: For client-side logic.
- **Firebase**: For backend services (Firestore database).
- **Geolocation API**: To capture the user's location.

## Setup Instructions

1. Clone the repository:
   ```sh
   git clone <repository-url>
   cd Website-for-Requesting-pick-up
   ```

2. Open `index.html` in a browser.

3. Add a `userID` parameter to the URL:
   ```
   http://localhost/index.html?userID=<your-user-id>
   ```

4. Click the "Gửi yêu cầu" button to send a pickup request.

## Example of Correct User Input

To use the application, you need to provide a `userID` parameter in the URL. For example:

```
http://localhost/index.html?userID=12345
```

Here, `12345` is the `userID` that will be displayed and used in the application.

## Firebase Configuration

The Firebase configuration is already included in the `index.html` file. If you need to use your own Firebase project, replace the `firebaseConfig` object with your project's configuration.

```javascript
const firebaseConfig = {
  apiKey: "your-api-key",
  authDomain: "your-auth-domain",
  databaseURL: "your-database-url",
  projectId: "your-project-id",
  storageBucket: "your-storage-bucket",
  messagingSenderId: "your-messaging-sender-id",
  appId: "your-app-id",
  measurementId: "your-measurement-id"
};
```

## Deployment Instructions

### Uploading to a Website

1. **Prepare the Files**:
   Ensure that all necessary files (e.g., `index.html`, `README.md`) are in the same directory.

2. **Choose a Hosting Service**:
   You can use any static hosting service such as GitHub Pages, Netlify, or Firebase Hosting. Below are instructions for Firebase Hosting:

   - Install Firebase CLI:
     ```sh
     npm install -g firebase-tools
     ```

   - Login to Firebase:
     ```sh
     firebase login
     ```

   - Initialize Firebase Hosting:
     ```sh
     firebase init hosting
     ```
     - Select your Firebase project.
     - Set `public` as the directory to deploy.
     - Choose `No` for single-page app configuration.

   - Deploy the Website:
     ```sh
     firebase deploy
     ```

3. **Access Your Website**:
   After deployment, Firebase will provide a hosting URL where your website is live.

### Setting Up Firebase

1. **Create a Firebase Project**:
   - Go to the [Firebase Console](https://console.firebase.google.com/).
   - Click on "Add Project" and follow the setup instructions.

2. **Enable Firestore**:
   - In the Firebase Console, navigate to "Firestore Database".
   - Click "Create Database" and choose the appropriate settings.

3. **Add Collections**:
   - Create a collection named `ride_requests` to store user requests.
   - Create a collection named `drivers` to store driver information.

4. **Update Firebase Configuration**:
   - Replace the `firebaseConfig` object in `index.html` with your Firebase project's configuration. You can find this in the Firebase Console under "Project Settings" > "General" > "Your apps".

   ```javascript
   const firebaseConfig = {
     apiKey: "your-api-key",
     authDomain: "your-auth-domain",
     databaseURL: "your-database-url",
     projectId: "your-project-id",
     storageBucket: "your-storage-bucket",
     messagingSenderId: "your-messaging-sender-id",
     appId: "your-app-id",
     measurementId: "your-measurement-id"
   };
   ```

## How It Works

1. The application extracts the `userID` from the URL and displays it on the page.
2. When the "Gửi yêu cầu" button is clicked:
   - The user's location is captured using the Geolocation API.
   - A pickup request is sent to the Firestore database.
3. The application listens for updates to the request's status in Firestore.
4. Once a driver accepts the request, the driver's phone number is displayed.

## Notes

- Ensure that location permissions are enabled in your browser.
- The application requires an active internet connection to interact with Firebase.

## License

This project is licensed under the MIT License.