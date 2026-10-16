# AL/GA Data Center Project Map

Interactive landing page mapping data center projects in Alabama and Georgia.

## Data
- Source of truth: data/compute-atlas-facilities.json (139 facilities, from compute-atlas.com)
- Each record has: name, operator, status, location{lat,lon,city,county,state},
  notes, statusHistory[], sources[]{url,label,publisher}, capacityMw, investmentUsd,
  announcedDate, lastUpdated, facilityType, community{status,notes}
- Default view: facilityType == "data_center" only (toggle for power/crypto later)

## Status legend (three colors, map from source `status` field)
- Proposed  (green)  <- proposed
- Approved  (amber)  <- permitted
- Active    (red)    <- under_construction, operational
- cancelled: gray, hidden by default

## UX
- Map on top (Leaflet + OpenStreetMap, centered on AL/GA). Legend always visible.
- Click a marker -> detail panel BELOW the map (not a popup) showing:
  headline (name + operator), status badge, city/county, one-paragraph summary
  from `notes`, timeline from `statusHistory`, planned MW / investment if present,
  then a "Related news" list from `sources` (label linked to url, publisher).
- Filters: state (AL/GA/both), status.
- Mobile-friendly. Single static site, no backend.

## Stack
Plain HTML/CSS/JS + Leaflet from CDN. No build step unless we outgrow it.
