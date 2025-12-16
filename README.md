# Client Map Visualization Template

A customizable, interactive map for visualizing client locations with filtering capabilities and 3D revenue visualization.

![Map Preview](https://img.shields.io/badge/Mapbox-GL%20JS-blue) ![License](https://img.shields.io/badge/license-MIT-green)

## Features

**Interactive Visualization**
- Color-coded markers by industry/sector
- 3D extrusion bars representing revenue (visible when zoomed in)
- State/region boundary highlighting

**Filtering System**
- Filter by industry/sector
- Filter by state/region
- Real-time updates without page reload

**Responsive Design**
- Works on desktop and mobile
- Collapsible filter panel
- Hover effects on markers

## Quick Start

### 1. Get a Mapbox Access Token

1. Create a free account at [mapbox.com](https://account.mapbox.com/)
2. Navigate to your account dashboard
3. Copy your default public token or create a new one

### 2. Configure the Map

Open `index.html` and find the configuration section near line 180:

```javascript
// ============================================
// CONFIGURATION - UPDATE THESE VALUES
// ============================================

// Get your free Mapbox token at: https://account.mapbox.com/
mapboxgl.accessToken = 'YOUR_MAPBOX_ACCESS_TOKEN_HERE';

// Map center coordinates [longitude, latitude]
const MAP_CENTER = { lng: -98.5795, lat: 39.8283 }; // Center of USA

// Initial zoom level (lower = more zoomed out)
const INITIAL_ZOOM = 4;
```

### 3. Add Your Client Data

Edit `client_list.csv` with your data. Required columns:

| Column | Description | Example |
|--------|-------------|---------|
| Client | Company/client name | "Acme Corp" |
| Industry | Business sector | "Technology" |
| Color | Marker color | "Blue", "Green", "#FF5733" |
| Address | Full address | "123 Main St, City, ST 12345" |
| longitude | Longitude coordinate | -74.0060 |
| latitude | Latitude coordinate | 40.7128 |
| state | State/region name | "New York" |
| revenue | Annual revenue (number) | 500000 |

**Getting Coordinates:**
- Use [Google Maps](https://maps.google.com) - right-click any location to copy coordinates
- Use [latlong.net](https://www.latlong.net/) for address lookup
- Use geocoding APIs for bulk conversion

### 4. Update State Boundaries (Optional)

Edit `target_states.geojson` to highlight your target regions:

1. Download state boundaries from [Natural Earth](https://www.naturalearthdata.com/) or [US Census](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html)
2. Use [geojson.io](https://geojson.io/) to edit and combine regions
3. Replace the contents of `target_states.geojson`

### 5. Deploy

**Option A: Netlify (Recommended)**
1. Create account at [netlify.com](https://netlify.com)
2. Drag and drop your project folder to deploy

**Option B: GitHub Pages**
1. Push to a GitHub repository
2. Enable GitHub Pages in repository settings

**Option C: Any Static Host**
- Vercel, Cloudflare Pages, AWS S3, etc.

## File Structure

```
client-map-template/
├── index.html           # Main application
├── client_list.csv      # Client data (edit this)
├── target_states.geojson # State boundaries (optional)
└── README.md            # This file
```

## Customization

### Change Map Style

Find this line in `index.html`:
```javascript
style: 'mapbox://styles/mapbox/dark-v11',
```

Available styles:
- `mapbox://styles/mapbox/dark-v11` (dark theme)
- `mapbox://styles/mapbox/light-v11` (light theme)
- `mapbox://styles/mapbox/streets-v12` (street map)
- `mapbox://styles/mapbox/satellite-v9` (satellite)

### Change Highlight Color

Find the layer configuration:
```javascript
"fill-outline-color":'limegreen',
"line-color":'limegreen'
```

Change `limegreen` to any CSS color.

### Adjust 3D Bar Height

Find this line to change how revenue affects bar height:
```javascript
height: parseInt(entry.revenue) / 200
```

Lower divisor = taller bars, higher divisor = shorter bars.

### Change Marker Size

Find in the CSS section:
```javascript
el.style.width = '16px';
el.style.height = '16px';
```

## Technologies Used

- [Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/) - Map rendering
- [Turf.js](https://turfjs.org/) - Geospatial analysis
- [PapaParse](https://www.papaparse.com/) - CSV parsing
- [Montserrat Font](https://fonts.google.com/specimen/Montserrat) - Typography

## License

MIT License - Feel free to use for personal or commercial projects.

## Support

For issues or feature requests, please open a GitHub issue.
