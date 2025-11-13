---
layout: post
title: UFO Sightings Analysis
---

# UFO Sightings in the United States (1950-2014)

## Visualization 1: Geographic Distribution of UFO Sightings

<vegachart schema-url="{{ site.baseurl }}/assets/json/ufo_map.json" style="width: 100%"></vegachart>

### Description
This visualization displays a sample of 5,000 UFO sightings across the United States, showing the geographic distribution of reported encounters. Each point represents a sighting location, with colors indicating the shape of the UFO observed.

### Design Choices

**Encoding Types**: I used a geographic scatter plot with longitude and latitude encodings to plot sighting locations. The AlbersUSA projection provides an accurate representation of the continental United States, Alaska, and Hawaii. Color encoding is used to distinguish between different UFO shapes, while tooltips provide additional context including city, state, shape, year, and duration.

**Color Scheme**: I selected the 'category20' color scheme to differentiate between the various UFO shapes. This qualitative color palette provides sufficient visual distinction between the 20+ different shape categories in the dataset, making it easy to identify patterns in shape distribution across different regions.

### Data Transformations
Several transformations were applied in the Python notebook:
- Filtered data to include only US sightings (country == 'us')
- Removed records with missing latitude, longitude, shape, or year values
- Filtered geographic coordinates to reasonable ranges for the US (latitude: 20-72°, longitude: -180° to -65°)
- Limited the time range to 1950-2014 to focus on the modern UFO phenomenon era
- Sampled 5,000 random sightings from the 63,410 US sightings to optimize visualization performance and reduce overplotting

---

## Visualization 2: UFO Sightings Over Time by Shape

<vegachart schema-url="{{ site.baseurl }}/assets/json/ufo_timeseries.json" style="width: 100%"></vegachart>

### Description
This interactive line chart shows the trend in UFO sightings from 1950 to 2014, broken down by the shape of the observed object. The visualization reveals a dramatic increase in reported sightings beginning in the mid-1990s, with a peak around 2010-2012.

### Design Choices

**Encoding Types**: I used a line chart with year on the x-axis (quantitative) and count of sightings on the y-axis (quantitative). Each line represents a different UFO shape (nominal), with point markers at each year to emphasize individual data points. The temporal encoding allows viewers to easily track trends over the 64-year period.

**Color Scheme**: The 'category10' color scheme differentiates the top 10 most common UFO shapes. When a shape is selected via the dropdown, its line remains fully colored and opaque, while unselected shapes fade to light gray with reduced opacity, allowing for focused comparison while maintaining context of overall trends.

### Data Transformations
Additional transformations for this visualization:
- Parsed datetime strings into proper datetime objects using pandas
- Extracted year from the datetime field for temporal aggregation
- Filtered to include only the top 10 most common shapes to avoid visual clutter
- Grouped data by year and shape, counting the number of sightings for each combination
- This aggregation reduced the dataset from 63,410 individual sightings to manageable time series data

---

## Interactivity: Shape Selection Dropdown

The time series visualization includes an interactive dropdown menu that allows users to select specific UFO shapes or view all shapes simultaneously. When a shape is selected, its trend line is highlighted while others are dimmed, making it easier to focus on specific patterns without losing the broader context. 

This interactivity enhances the visualization by allowing users to:
- Compare specific shapes against the overall trend
- Identify which shapes became more or less common over time
- Focus on shapes of particular interest (e.g., "triangle" or "fireball") without creating separate charts

The dramatic rise in sightings across all shapes from the mid-1990s onward likely correlates with increased internet usage and online reporting platforms, making it easier for people to document and share their experiences. The interactivity makes this pattern clear while allowing exploration of shape-specific trends.

---

## Links

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/ufo-scrubbed-geocoded-time-standardized-00.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/itsbhoomika/itsbhoomika.github.io/blob/main/Workbook.ipynb" text="The Analysis" %}
</div>
