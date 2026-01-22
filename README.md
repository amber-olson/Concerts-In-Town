# Concert Notification System

A personal backend system that monitors upcoming concerts for your favorite artists using the Ticketmaster Discovery API. The system tracks artist metadata, upcoming events in your preferred locations, and notification status for new shows.

---

## 🔐 Setup Instructions

1. **Install Dependencies**
   ```bash
   pip install python-dotenv requests geopy
   ```

2. **Configure Your API Key**
   ```bash
   cp .env.example .env
   ```
   - Get your free Ticketmaster API key: https://developer.ticketmaster.com/
   - Add it to your `.env` file
   - **Never commit your `.env` file** (it's in .gitignore)

3. **Read [SECURITY.md](SECURITY.md) for best practices**

---

## Features

- Track multiple artists and support multiple Ticketmaster IDs per artist.
- Store genre information and upcoming events count.
- Compute pagination for API requests to retrieve all events.
- Filter events by configurable locations and radius.
- Track the next upcoming event and notification status.
- Optional integration for Apple Music listening scores in the future.

---

## Artist Metadata Structure

Each artist is stored in a dictionary keyed by artist name. Example structure:

- `ids`: List of Ticketmaster IDs associated with the artist.
- `genre_name`: Primary genre of the artist.
- `genre_id`: Genre ID from Ticketmaster.
- `ticketmaster_upcoming_events_number`: Total number of upcoming events.
- `pagination`: Dictionary containing page size and number of pages needed to retrieve all events.
- `listening_score`: Optional numeric score from Apple Music (future integration).
- `next_event_date`: Date of the next upcoming event.
- `total_notified_events`: Count of events the user has already been notified about.
- `last_checked`: Timestamp of the last metadata check.
- `events`: List of upcoming events with details:

  - `id`: Ticketmaster event ID.
  - `name`: Event name.
  - `date`: Event date.
  - `time`: Event start time.
  - `venue`: Venue name.
  - `city`: City of the event.
  - `state`: State of the event.
  - `ticket_url`: Direct link to purchase tickets.
  - `status`: Event status (e.g., on sale, sold out).
  - `min_price`: Minimum ticket price (if available).
  - `max_price`: Maximum ticket price (if available).
  - `distance_miles`: Distance from the user's location to the venue (if available).
  - `notified`: Boolean indicating whether a notification has been sent for this event.
  - `notification_count`: Number of times notifications have been sent.
  - `notifications`: List of notification records for the event.

---

## Example Artist Entry

```text
Artist Name: "Peter McPoland"

- ids: ["K8vZ917_hNf"]
- genre_name: "Alternative"
- genre_id: "KnvZfZ7vAvv"
- ticketmaster_upcoming_events_number: 25
- pagination: { page_size: 25, pages_needed: 1 }
- listening_score: 87
- next_event_date: "2026-03-05"
- total_notified_events: 0
- last_checked: "2025-11-16T11:00:00"
- events: [
    {
        id: "vv1kvYvN7zGAG08TE",
        name: "Peter McPoland: Big Lucky Tour",
        date: "2026-03-06",
        time: "20:00:00",
        venue: "Majestic Theatre",
        city: "Madison",
        state: "WI",
        ticket_url: "https://www.ticketmaster.com/...",
        status: "onsale",
        min_price: 45.0,
        max_price: 120.0,
        distance_miles: 5.2,
        notified: False,
        notification_count: 0,
        notifications: []
    }
]
