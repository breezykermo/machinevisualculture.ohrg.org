# Machine Visual Culture - Claude Context

## Project Overview
This is a Rheo-based website for Machine Visual Culture.

## Development Workflow

### Auto-compilation
A compilation loop typically runs in a separate terminal that auto-recompiles the site on file changes. When editing content files, the site will rebuild automatically.

### Important: Event Link Structure
Events in `content/index.typ` use the `#event()` function. Be aware of HTML nesting constraints:

- If an event has a `link:` parameter, the entire event is wrapped in an `<a>` tag
- The event description can also contain `#link()` calls
- **HTML does not permit nested `<a>` tags** - if an event's description already contains links, do NOT add a `link:` parameter

Example of correct usage:
```typst
// Event with internal links only - no link parameter
#event(
  "Event Title",
  "16 April 2026",
  [Description with #link("https://example.com")[internal links].],
  event_id: "2026-04-16"
)

// Event with single external link - use link parameter
#event(
  "Event Title",
  "4 June 2026",
  [Description text without internal links.],
  event_id: "2026-06-04",
  link: "https://example.com/event"
)
```

## Files
- `content/index.typ` - Main content file with events and other sections
- `build/html/index.html` - Generated HTML output
- `rheo.toml` - Rheo configuration
