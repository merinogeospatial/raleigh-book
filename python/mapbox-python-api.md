---
description: 'https://www.mapbox.com/api-documentation/?language=Python'
---

# Mapbox Python API

```
import pandas as pd
```

Out\[1\]:

```text
{'feature_count': 610, 'filename': 'points.geojson', 'type': 'file'}
```

In \[3\]:

```text
# Generate data breaks and color stops from colorBrewer
color_breaks = [0,100,200,300,400,500]
color_stops = create_color_stops(color_breaks, colors='YlGnBu')

# Create the viz from the dataframe
viz = CircleViz('points.geojson',
                access_token=token,
                height='200px',
                color_property = "FID",
                color_stops = color_stops,
                label_property = 'FID',
                stroke_color = 'black',
                center = (-78.642451, 35.777777),
                zoom = 13,
                below_layer = 'waterway-label'
              )
viz.show()
```

