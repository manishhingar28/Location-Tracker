# 🌍 Real-Time Location Tracker using MERN + Socket.io + Tailwind CSS

A full-stack real-time map application built with the MERN stack, Socket.io, Tailwind CSS, and Leaflet. This project tracks users' live locations, displays them on a map, and includes distance and ETA calculations between users.

---

## 🚀 Features

* Live location tracking of all connected users in real-time
* User permission prompt before accessing geolocation
* Distance between users in kilometers
* ETA (Estimated Travel Time) between users
* Fully responsive and modern UI with Tailwind CSS
* Socket.io powered real-time communication

---

## 🧰 Tech Stack

* **Frontend**: React, Tailwind CSS, React-Leaflet, Socket.io-client
* **Backend**: Node.js, Express, Socket.io
* **Database**: MongoDB (optional for user sessions)
* **APIs**: Google Distance Matrix API or OpenRouteService (for distance & ETA)

---

## 📦 Prerequisites

* Node.js >= 14
* MongoDB URI (local or Atlas)
* Distance Matrix API Key (Google or OpenRouteService)

---

## 🔧 Installation & Setup

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/realtime-map-tracker.git
cd realtime-map-tracker
```

### 2. Install Backend Dependencies

```bash
cd server
npm install
```

### 3. Install Frontend Dependencies

```bash
cd client
npm install
```

### 4. Environment Variables

Create a `.env` file in the root directory:

```env
PORT=5000
MONGO_URI=your_mongodb_uri
DISTANCE_API_KEY=your_distance_matrix_api_key
```

### 5. Run the Development Servers

In the root directory (server):

```bash
npm run server
```

In the `client/` directory (React app):

```bash
npm start
```

### 6. Access the Application

Visit: `http://localhost:3000`

---

## 🛠️ Project Structure

```
distance-tracker/
├── client/                  # React Frontend
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/      # Map, Sidebar, UserCard
│   │   ├── socket.js        # Socket.io client setup
│   │   ├── App.jsx
│   │   ├── index.js
│   │   └── styles.css
│   ├── tailwind.config.js
│   ├── postcss.config.js
│   ├── package.json
│   └── README.md
├── server/                 # Express Backend
│   ├── controllers/
│   │   └── locationController.js
│   ├── models/
│   │   └── User.js
│   ├── routes/
│   │   └── locationRoutes.js
│   ├── socketHandlers.js
│   ├── server.js
│   ├── package.json
│   └── README.md
├── .env
└── README.md
```

---

## 🔁 Socket Event Flow

### Client

* Connects via Socket.io
* Requests user location via `navigator.geolocation`
* Emits `location-update` with `{ lat, lng }`
* Receives updates from server about all users with `distance`, `eta`

### Server

* Listens for `location-update`
* Stores/updates user coordinates
* Calculates distance & ETA using external API
* Broadcasts updated location + distance to all connected clients

---

## 🌐 APIs Used

### Google Distance Matrix API

* Endpoint: `https://maps.googleapis.com/maps/api/distancematrix/json`
* Input: origin & destination lat/lng
* Output: distance in km, duration in minutes


---


## 📈 Future Enhancements

* Add JWT-based authentication
* Add user avatars/names via login
* Add a group chat via Socket.io
* Log location history with timestamps (MongoDB)

---


