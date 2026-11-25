# Kiibi

A lightweight, mobile-friendly web application for real-time public transit routing, live stop departures, and live vehicle tracking across Bratislava, Šamorín, and surrounding regions in Slovakia.

🔗 **Live App:** [https://kiibi.fyi](https://kiibi.fyi)

## Features

* **Connection Planner:** Search point-to-point routes between stops with customizable transfer limits, transit modes (bus, tram, rail), accessibility filters, via stops, and walking/cycling speeds.
* **Live Departures:** View upcoming departures and real-time delay indicators for any stop.
* **Real-Time Vehicle Map:** Watch buses, trams, and trains move along their routes with smooth interpolation based on live timetable and delay data.
* **Trip Tracking & Alerts:** Follow a specific vehicle on the map and receive browser notifications if your trip is delayed.
* **Mobile-First & Themeable:** Responsive collapsible sheet interface optimized for touchscreens, with a quick dark/light mode toggle.

## Architecture & Deployment

Kiibi is built as a zero-dependency, single-file frontend (`index.html`) paired with an optional Cloudflare Worker edge-caching proxy (`worker.js`):

1. **Frontend (`index.html`):** Uses vanilla HTML, CSS, JavaScript, and [Leaflet](https://leafletjs.com/) for map rendering. Can be hosted on any static host (Cloudflare Pages, GitHub Pages, Netlify, etc.).
2. **Edge Proxy (`worker.js`):** Optional Cloudflare Worker that attaches a descriptive `User-Agent` header (`Kiibi/1.0 (+https://kiibi.fyi; ...)`) and caches identical API responses at the edge to minimize load on upstream servers.

### Running Locally

No build step is required. Clone the repository and open `index.html` in your browser, or serve it with any static file server:

```bash
git clone https://github.com/cathlyn-exe/Kiibi.git
cd Kiibi
npx serve .
```

*(Note: Update the repository URL, contact email, and `API` endpoint constant in `index.html` and `worker.js` to match your own domain if self-hosting.)*

## Data Sources & Attribution

* **Routing & Timetable Data:** Powered by the [Transitous](https://transitous.org/) public MOTIS API ([data sources](https://transitous.org/sources/)). Consider [supporting Transitous](https://transitous.org/donate/).
* **Map Tiles:** © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors.

## License

This project is open-source and available under the [MIT License](LICENSE).