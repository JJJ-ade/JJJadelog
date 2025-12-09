+++
title = "OpenStreetMap"
weight = 1
+++

`openstreetmap`

- `openstreetmap`: Embeds an OpenStreetMap. It takes `bbox` as a required parameter and optionally `layer` and `marker`.
  - `bbox`: Bounding box coordinates (west,south,east,north)
  - `layer`: Map layer type (e.g., "mapnik")
  - `marker`: Marker position (lat,lon)

```jinja
{{/* openstreetmap(bbox="-122.613,37.431,-122.382,37.559", layer="mapnik", marker="37.495,-122.497") */}}
```

{{ openstreetmap(bbox="-122.613,37.431,-122.382,37.559", layer="mapnik", marker="37.495,-122.497") }}
