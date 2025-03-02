# FMD User App Frontend

This is the React frontend for the FMD User Application. It provides the user interface for user authentication, user management, and project uploads.

## Getting Started

1. Install dependencies:
```bash
npm install
```

2. Set up environment variables:
   - Create a `.env` file in the root directory
   - Add any necessary environment variables

3. Start the development server:
```bash
npm run dev
```

## File Structure

```
/frontend
├── public/                  # Public assets
│   └── fmd.png
├── src/                     # Source files
│   ├── assets/              # Asset files
│   │   └── fmd.png
│   ├── components/          # React components
│   │   ├── FileUpload.jsx
│   │   ├── Layout.jsx
│   │   └── ModelUpload.jsx
│   ├── pages/               # Page components
│   │   └── Dashboard.jsx
│   ├── services/            # Service files
│   ├── store/               # State management
│   ├── utils/               # Utility functions
│   ├── App.jsx              # Main App component
│   ├── index.css            # Global CSS
│   └── main.jsx             # Entry point
├── .env                     # Environment variables
├── package.json
├── tailwind.config.js       # Tailwind CSS configuration
├── vite.config.ts           # Vite configuration
└── README.md
```

## Available Scripts

In the project directory, you can run:

### `npm run dev`

Runs the app in the development mode.
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.
You will also see any lint errors in the console.

### `npm run build`

Builds the app for production to the `dist` folder.
It correctly bundles React in production mode and optimizes the build for the best performance.

### `npm run preview`

Serves the production build locally.

## User Flow and Main Pages

### User Flow

1. **Login/Register**: 
   - Users start by either logging in or registering a new account. The `Login` and `Register` pages handle these actions.
   - Upon successful login, users are redirected to the `Dashboard`.

2. **Dashboard**:
   - The `Dashboard` page is the main landing page after login. It provides an overview of the user's projects and other relevant information.
   - Users can navigate to different sections from the dashboard.

3. **Profile**:
   - The `Profile` page allows users to view and update their personal information, including their profile picture.

4. **Project Management**:
   - Users can create, view, and manage their projects.
   - The `Upload` page allows users to upload new projects.
   - The `ProjectPreview` page provides a detailed view of a specific project.
   - The `Deploy` page is used for deploying projects.

5. **CheckDeployment**:
   - The `CheckDeployment` page is used to check the deployment status of any uploaded project.

### Main Pages

- **Login**: Handles user authentication.
- **Register**: Handles new user registration.
- **Dashboard**: Displays an overview of the user's projects and activities.
- **Profile**: Allows users to update their personal information.
- **Upload**: Facilitates project uploads.
- **ProjectPreview**: Provides a detailed view of a specific project.
- **Deploy**: Manages project deployment.
- **CheckDeployment**: This page checks the deployment staus of the uploaded project.

### Private Routes

The application uses private routes to protect certain pages. Only authenticated users can access these routes. If a user is not authenticated, they are redirected to the login page.

### Components

The application is structured with reusable components to ensure maintainability and scalability. Key components include:

- **Layout**: The main layout component that wraps around other components.
- **FileUpload**: Handles file uploads.
- **ModelUpload**: Manages model uploads.

### State Management

The application uses a store for state management, ensuring that user data and authentication status are managed efficiently across different components.

## Learn More

To learn React, check out the [React documentation](https://reactjs.org/).