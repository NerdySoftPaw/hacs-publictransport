# Trafiklab (Sweden)

Trafiklab provides access to Swedish public transport data through various APIs.

## Coverage Area

- All of Sweden
- All regional transit operators
- SJ (national rail)

## API Details

| Property | Value |
|----------|-------|
| **Base URL** | `https://realtime-api.trafiklab.se/v1/` |
| **API Key** | Required (free) |
| **Timezone** | Europe/Stockholm |

## API Key

### Getting an API Key

1. Register at [trafiklab.se](https://www.trafiklab.se)
2. Create a new project
3. Select the "Realtime API"
4. Copy the API key
5. Enter it during integration setup

!!! note
    The API key is free but required. Registration takes just a few minutes.

### API Key in Configuration

The API key is stored securely in your Home Assistant configuration and is used for:

- Stop/station search
- Fetching real-time departures

## Transport Types

| Mode | Type | Description |
|------|------|-------------|
| TRAIN | train | Commuter and regional trains |
| METRO | subway | Stockholm Metro (Tunnelbana) |
| TRAM | tram | Trams (Göteborg, Norrköping, etc.) |
| BUS | bus | All bus services |
| FERRY | ferry | Ferry services |
| TAXI | taxi | Taxi/On-demand |

## Configuration

### Setup Steps

1. Select **Trafiklab** as provider
2. Enter your API key
3. Search for your stop (e.g., "Stockholm Centralstation")
4. Select the stop from the list
5. Configure departure count and filters

### Example Stops

- Stockholm Centralstation
- Göteborg Centralstation
- Malmö Centralstation
- Uppsala Centralstation

## Special Features

### Nationwide Coverage

Trafiklab aggregates data from all Swedish transit operators, providing a unified view of:

- SJ (national rail)
- SL (Stockholm)
- Västtrafik (Gothenburg region)
- Skånetrafiken (Malmö region)
- And many more

### Real-time Data

Real-time data is available when the `is_realtime` flag is true in the API response. This indicates live tracking data rather than scheduled times.

## API URLs

### Stop Search

```
https://realtime-api.trafiklab.se/v1/stops/name/Stockholm%20Centralstation?key=YOUR_API_KEY
```

### Departures

```
https://realtime-api.trafiklab.se/v1/departures/STATION_ID?key=YOUR_API_KEY
```

## Troubleshooting

### API Key Issues

If you get a 401 error:

1. Verify your API key is correct
2. Check that the key is active in your Trafiklab project
3. Ensure you're using the Realtime API key (not another API)

### No Results

If searches return no results:

- Try different spellings
- Use the Swedish name for the location
- Check that the stop exists in Trafiklab's database
