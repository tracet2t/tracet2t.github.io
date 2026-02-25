# Theory to Trade (T2T) by TRACE

## Running Locally

To serve the site locally, run:

```sh
npx serve .
```

Then open http://localhost:3000

## Contributing

### Maintaining Events

The events showcased on the main site are loaded dynamically. Instead of updating the `index.html`, all event data should be maintained inside `data/events.json`.

**Order Rule:**
When adding new events to the JSON array, ensure they are ordered **chronologically from oldest to newest** (i.e., older events at the top of the file, and the newest/latest events appended to the very bottom). The frontend automatically reverses the array before rendering so that the most recent events are always displayed first.

**Event JSON Structure:**
Each event in the array should follow this structure:

```json
{
  "image": "events/your-event-image.jpg",
  "title": "Your Event Title",
  "date": "Day, DD Mon YYYY",
  "meta": "Short summary \u2022 Categories",
  "description": "Full details about the event.",
  "buttons": [
    {
      "text": "Register Now",
      "link": "https://example.com/register",
      "class": "btn",
      "target": "_blank",
      "rel": "noopener"
    },
    {
      "text": "Closed",
      "title": "Registration closed",
      "class": "btn disabled",
      "isButton": true
    }
  ]
}
```

**Key Points:**
- `image`: Supported event images will be rendered with `object-fit: contain` to prevent truncation. Place new images in the `events/` or `images/` directory.
- `date`: Clearly specified dates (e.g., "Wed, 17 Dec 2025").
- `buttons`: An array of buttons to render for the event.
  - If it's a clickable link, specify the `link`, `target`, and `rel`.
  - If it's an inactive or regular `<button>` tag instead of an anchor `<a>` tag, set `"isButton": true`.
  - Button styling uses CSS classes such as `"btn"`, `"btn secondary"`, or `"btn disabled"`.