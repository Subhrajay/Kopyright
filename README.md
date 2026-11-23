# Kopyright

**Royalty Management Software**

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](LICENSE)
[![GitHub Repository](https://img.shields.io/badge/GitHub-Kopyright-181717?logo=github)](https://github.com/Subhrajay/Kopyright)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react&logoColor=white)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Flask](https://img.shields.io/badge/Flask-Python-000000?logo=flask&logoColor=white)](https://flask.palletsprojects.com/)

Kopyright is a royalty management platform for creators and investors. It provides role-based dashboards, content marketplaces, file uploads, account authentication, and purchase tracking.

**Live application:** https://kopyright.vercel.app

## Features

- Separate artist and investor accounts
- Secure signup and login
- Password strength validation
- Creator content uploads with thumbnails
- Creator upload history
- Marketplace for browsing available content
- Content purchasing and investor content tracking
- MongoDB-backed Express API
- React-based responsive interface
- Experimental Flask API server

## Technology Stack

### Frontend

- React 18
- React Router
- React Bootstrap
- Axios
- Auth0 React
- React Scripts

### Backend

- Node.js
- Express
- MongoDB
- Mongoose
- bcrypt
- Express Session
- Multer
- CORS

### Experimental Flask Server

- Flask
- Werkzeug
- In-memory content storage
- Local file uploads

## Project Structure

```text
Kopyright/
├── client/                 # React frontend
│   ├── public/
│   └── src/
│       ├── pages/          # Application pages
│       └── pages_styles/   # Page-specific styles
├── server/                 # Express and MongoDB backend
│   ├── server.js
│   └── package.json
├── flask-server/           # Experimental Flask server
│   └── app.py
├── LICENSE
└── README.md
```

## Prerequisites

Install the following before running the project:

- Node.js and npm
- MongoDB
- Python 3
- Flask

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/Subhrajay/Kopyright.git
cd Kopyright
```

### 2. Set up MongoDB

Start a local MongoDB instance. The Express server currently uses:

```text
mongodb://localhost/royalty_management
```

### 3. Set up the Express backend

```bash
cd server
npm install
npm run dev
```

The API server runs on `http://localhost:3000` by default.

### 4. Set up the React frontend

Open another terminal from the repository directory:

```bash
cd client
npm install
npm start
```

The React application will normally run on `http://localhost:3001` or the next available port.

## Environment Configuration

The backend currently contains local configuration directly in `server/server.js`. For production use, move sensitive values out of source control and configure them through environment variables.

### Suggested environment variables

```dotenv
PORT=3000
MONGODB_URI=mongodb://localhost/royalty_management
SESSION_SECRET=replace-with-a-secure-random-secret
```

Update `server/server.js` to use these variables. For example:

```javascript
mongoose.connect(process.env.MONGODB_URI);

app.use(session({
  secret: process.env.SESSION_SECRET,
  resave: false,
  saveUninitialized: false,
}));
```

This is an illustrative configuration snippet; make sure the application loads the environment variables before using them.

## Main API Endpoints

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/api/signup` | Create a user account |
| `POST` | `/api/login` | Authenticate a user |
| `POST` | `/api/logout` | End the current session |
| `GET` | `/api/loggedIn` | Check whether a session is active |
| `GET` | `/api/userRole` | Retrieve the logged-in user's role |
| `POST` | `/api/content` | Upload content |
| `GET` | `/api/uploadHistory` | Retrieve content uploaded by the user |
| `GET` | `/api/allContent` | Retrieve all marketplace content |
| `POST` | `/api/buyContent/:id` | Purchase or record a content transaction |
| `GET` | `/api/investorContent` | Retrieve content owned by an investor |

## Frontend Routes

| Route | Page |
| :--- | :--- |
| `/` | Home |
| `/Login` | Login |
| `/SignUp` | Account registration |
| `/Marketplace` | Marketplace |
| `/CreatorDashboard` | Creator dashboard |
| `/InvestorDashboard` | Investor dashboard |
| `/about` | About |
| `/contact` | Contact |
| `/terms-and-conditions` | Terms and conditions |

## Running Tests

Run the frontend test suite:

```bash
cd client
npm test
```

The repository does not currently include a configured backend test suite.

## Production Build

Create an optimized React production build:

```bash
cd client
npm run build
```

The generated files will be placed in `client/build/`.

## Security Notes

The current implementation is a prototype and should not be deployed directly to production without additional hardening:

- Replace the hard-coded session secret.
- Store database URLs and secrets in environment variables.
- Configure secure cookies and HTTPS sessions.
- Implement server-side authorization for every protected operation.
- Avoid returning password data or internal user records.
- Validate file types and sizes.
- Use object storage or a file database instead of Base64 strings in MongoDB documents.
- Add payment-provider integration for real purchases.
- Set restrictive CORS configuration.
- Add rate limiting and request validation.

## Experimental Flask Server

The Flask implementation is located in `flask-server/app.py`. It provides basic file upload and marketplace endpoints using temporary in-memory storage.

Run it from the project directory:

```bash
cd flask-server
pip install flask
python app.py
```

Create the required upload directory first, from within `flask-server/`:

```bash
mkdir uploads
```

The Flask server is not the primary backend and may not remain fully compatible with the React application.

## Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes.
4. Push the branch.
5. Open a pull request.

## License

This project is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for details.
