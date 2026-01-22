# NTA (National Transport Authority, Ireland)

NTA provides access to Irish public transport data through the GTFS-Realtime API.

## Coverage Area

- All of Ireland
- Dublin Bus
- Bus Éireann
- Go-Ahead Ireland
- Luas (Dublin Tram)
- Iarnród Éireann (Irish Rail)

## API Details

| Property | Value |
|----------|-------|
| **Base URL** | `https://api.nationaltransport.ie/gtfsr` |
| **API Key** | Required (free) |
| **Timezone** | Europe/Dublin |
| **Data Format** | GTFS-Realtime (JSON) |

## API Key

### Getting an API Key

1. Register at [developer.nationaltransport.ie](https://developer.nationaltransport.ie)
2. Subscribe to the "GTFS-Realtime" API
3. You will receive a **Primary** and **Secondary** API key
4. Enter the Primary API key during integration setup (required)
5. Optionally enter the Secondary API key (used as fallback)

!!! tip
    The Secondary API key is optional but recommended as a fallback if the Primary key fails.

### API Key Usage

- **Primary Key**: Required for all API calls
- **Secondary Key**: Automatic fallback if Primary returns 401

## Transport Types

| GTFS Route Type | Type | Description |
|-----------------|------|-------------|
| 0, 5, 6 | tram | Tram/Light Rail (Luas) |
| 1 | subway | Subway/Metro |
| 2, 7 | train | Rail (Iarnród Éireann) |
| 3 | bus | Bus services |
| 4 | ferry | Ferry |

## Configuration

### Setup Steps

1. Select **NTA** as provider
2. Enter your Primary API key (and optionally Secondary key)
3. Enter the stop ID (see below)
4. Configure departure count and filters

### Finding Stop IDs

NTA uses GTFS stop IDs. To find a stop ID:

1. Visit [Transport for Ireland](https://www.transportforireland.ie/)
2. Search for your stop
3. The stop ID is in the URL or stop information

Common stop ID formats:

- Dublin Bus: `8220DB000001`
- Luas: `LUAS1`, `LUAS2`, etc.
- Irish Rail: Station codes

### Example Stops

- Dublin Connolly Station
- Heuston Station
- Dublin Bus stops (by stop number)
- Luas stops

## Special Features

### GTFS-Realtime Format

NTA uses the GTFS-Realtime standard, which provides:

- Trip updates with delays
- Real-time arrival predictions
- Service alerts (future feature)

### Multiple Operators

The integration handles data from all Irish operators:

- **Dublin Bus**: City and suburban buses
- **Bus Éireann**: Regional and intercity buses
- **Go-Ahead Ireland**: Dublin commuter buses
- **Luas**: Dublin light rail (Red and Green lines)
- **Iarnród Éireann**: National rail services

### Delay Calculation

Delays are calculated from GTFS-RT `trip_update.stop_time_update.departure.delay` field, provided in seconds and converted to minutes.

## API Information

### Endpoint

```
https://api.nationaltransport.ie/gtfsr/v2/TripUpdates?format=json
```

### Authentication

API key is passed via the `x-api-key` header:

```
x-api-key: YOUR_PRIMARY_API_KEY
```

### Response Structure

```json
{
  "header": {
    "gtfs_realtime_version": "2.0",
    "timestamp": 1234567890
  },
  "entity": [
    {
      "id": "trip_id",
      "trip_update": {
        "trip": {
          "trip_id": "...",
          "route_id": "..."
        },
        "stop_time_update": [
          {
            "stop_id": "8220DB000001",
            "departure": {
              "delay": 120,
              "time": 1234567890
            }
          }
        ]
      }
    }
  ]
}
```

## Troubleshooting

### API Key Issues

If you get a 401 error:

1. Verify your Primary API key is correct
2. Check that you've subscribed to the GTFS-Realtime API
3. Try the Secondary key if configured

### No Departures Found

If no departures are returned:

1. Verify the stop ID is correct
2. Check that the stop has active services at this time
3. Enable debug logging to see API responses
