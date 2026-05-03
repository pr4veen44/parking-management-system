# Parking Management System

A full-stack web application for managing parking slots, vehicle entry/exit, and charges calculation — built with a **Python backend** and a **React + Vite frontend**.

---

## Features

- **Vehicle Check-In / Check-Out** — Register entry and exit of vehicles
- **Slot Management** — Track available, occupied, and reserved parking slots
- **Charges Calculation** — Automatically compute parking charges based on duration
- **Interactive Map** — Visualize parking locations and slot positions using Leaflet.js
- **Dashboard** — View real-time parking status and occupancy
- **Search & Filter** — Look up vehicles or slots by number/status
- **History Logs** — View past parking records

---

## Tech Stack

| Layer     | Technology                              |
|-----------|-----------------------------------------|
| Frontend  | React, Vite, JavaScript, CSS            |
| Maps      | Leaflet.js (`react-leaflet`)            |
| Backend   | Python (Flask / FastAPI)                |
| Database  | SQLite / JSON (file-based)              |

---

## Project Structure

```
parking-management-system/
├── backend/
│   ├── app.py               # Main application entry point
│   ├── models.py            # Data models
│   ├── routes.py            # API route definitions
│   ├── database.py          # Database connection & helpers
│   └── requirements.txt     # Python dependencies
│
├── frontend/
│   ├── public/              # Static assets
│   ├── src/
│   │   ├── components/      # Reusable React components
│   │   ├── pages/           # Page-level components
│   │   ├── assets/          # Images, icons, etc.
│   │   ├── App.jsx          # Root component
│   │   └── main.jsx         # Vite entry point
│   ├── index.html           # HTML template
│   ├── vite.config.js       # Vite configuration
│   └── package.json         # Node dependencies
│
└── README.md
```

---

## Getting Started

### Backend Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/pr4veen44/parking-management-system.git
   cd parking-management-system
   ```

2. **Navigate to the backend folder:**

   ```bash
   cd backend
   ```

3. **Install dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

4. **Run the server:**

   ```bash
   python app.py
   ```

   The backend will start at `http://localhost:5000` (or the configured port).

---

### Frontend Setup

1. **Navigate to the frontend folder:**

   ```bash
   cd frontend
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Start the development server:**

   ```bash
   npm run dev
   ```

   The app will be available at `http://localhost:5173`.

4. **Build for production:**

   ```bash
   npm run build
   ```

> Make sure the backend server is running before using the frontend.

---

## Usage

1. Start the **backend** server.
2. Run the **frontend** with `npm run dev`.
3. Use the interface to:
   - **Add a vehicle** — enter the vehicle number and assign a slot.
   - **Check out a vehicle** — select the slot and confirm exit; the system will calculate the charges.
   - **View the map** — see parking slot locations rendered on the Leaflet.js interactive map.
   - **View the dashboard** — see occupied and free slots at a glance.
   - **Browse history** — check logs of past entries and exits.

---

## API Endpoints

| Method | Endpoint                | Description                              |
|--------|-------------------------|------------------------------------------|
| GET    | `/slots`                | Get all parking slots and status         |
| GET    | `/slots/available`      | Get all currently available slots        |
| POST   | `/checkin`              | Check in a vehicle                       |
| POST   | `/checkout`             | Check out a vehicle & compute charges    |
| GET    | `/history`              | Get all parking history records          |
| GET    | `/history/<vehicle>`    | Get history for a specific vehicle       |

> Refer to `backend/routes.py` for the complete and exact API definitions.

---

## Environment Variables

Create a `.env` file inside the `frontend/` folder for any environment-specific config:

```env
VITE_API_BASE_URL=http://localhost:5000
VITE_MAP_CENTER_LAT=13.0827
VITE_MAP_CENTER_LNG=80.2707
VITE_MAP_DEFAULT_ZOOM=13
```

> Leaflet.js uses OpenStreetMap tiles by default — **no API key required**.

---

## Maps Integration

This project uses **[Leaflet.js](https://leafletjs.com/)** via the [`react-leaflet`](https://react-leaflet.js.org/) wrapper for all map functionality.

### Features powered by Leaflet

- Display parking lot locations on an interactive map
- Click on markers to view slot availability
- Zoom and pan across the parking area

### Installation (already included via `package.json`)

```bash
npm install leaflet react-leaflet
```

### Required CSS import in `main.jsx` or `App.jsx`

```js
import 'leaflet/dist/leaflet.css';
```

### Basic usage example

```jsx
import { MapContainer, TileLayer, Marker, Popup } from 'react-leaflet';

<MapContainer center={[13.0827, 80.2707]} zoom={13}>
  <TileLayer
    url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
    attribution='&copy; OpenStreetMap contributors'
  />
  <Marker position={[13.0827, 80.2707]}>
    <Popup>Parking Lot A — 5 slots available</Popup>
  </Marker>
</MapContainer>
```
