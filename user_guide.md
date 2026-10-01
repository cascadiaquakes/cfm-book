# User Guide

:::{note}
Interim guide, carried over from the viewer's original guide page. It will be replaced by the full CFM Viewer user guide from Becky (TBD).
:::

## Overview

The Community Fault Model (CFM) Web Interface provides interactive 2D and 3D visualizations of fault traces and surfaces for the Cascadia Subduction Zone. This guide outlines the functionality and usage of the 2D and 3D Fault Viewers, including instructions for interacting with the maps and accessing the data.

## Community Fault Model (CFM) Web Interface (Repository)

Visit the CFM-Web interface files and tools repository at [github.com/cascadiaquakes/CRESCENT-CFM-WEB](https://github.com/cascadiaquakes/CRESCENT-CFM-WEB).

## 2D Fault Viewer (Homepage)

The Homepage includes a **2D Fault Viewer** as a map-based representation of fault traces and other geospatial datasets. It allows users to explore, filter, and analyze faults in a two-dimensional view.

### Key Features

- **Fault Trace Visualization**: Displays fault traces as lines on the map. Users can click on fault traces to view detailed descriptions.
- **Interactive Filtering**: Filter faults by latitude, longitude, or depth using range sliders. Apply custom colors to faults based on their attributes (e.g., depth, dip, or rake).

### How to Use

1. **Navigate to the 2D Viewer**: Open the CFM-Web's homepage.
2. **Filter Faults**: Use the sliders to set minimum and maximum values for latitude, longitude, and depth. The map on the right and the list of displayed faults under the control panel will update dynamically to show/list only the faults within the selected ranges.
3. **Customize Fault Colors**: Use the *Fault Color* dropdown to select how faults are colored. Adjust the numeric range for color mapping if applicable.
4. **Select/Deselect Faults for 3D View**: Use the *Select All/Deselect All* checkbox to quickly toggle all faults. Click individual faults on the map for more information.
5. **Navigate to the 3D Viewer**: Click the *View 3D* button to open the 3D fault viewer and display fault traces and surfaces for the selected faults on the 2D viewer.

## 3D Fault Viewer

The **3D Fault Viewer** provides an immersive, three-dimensional visualization of fault surfaces and traces. It includes additional geospatial features such as earthquake data, satellite imagery with terrain, and boundary lines.

### Key Features

- **Fault Surface Visualization**: View 3D fault surfaces with selectable depth ranges.
- **Earthquake Data**: Display earthquake epicenters (USGS ComCat, M ≥ 3 since 1970) as points sized proportionally to magnitude. Click an earthquake to see its ComCat ID, magnitude, location, depth, and time.
- **Subducting Plate Surfaces**: Use the *Subducting Plate Surfaces* selection box to display plate-interface models (select up to two surfaces at the same time). Selected surfaces are labeled in the bottom legend.
- **Satellite Imagery and Terrain**: Turn on *Satellite imagery* to show imagery draped on terrain. While it is on, *Hide below ground* hides faults and earthquakes beneath the terrain surface.

### How to Use

- **To View All Fault Surfaces**: Click the **3D Viewer** button in the header.
- **To View Selected Fault Surfaces**:
  1. **Navigate to the 2D Viewer**: Go to the homepage.
  2. **Filter Faults**: Use the sliders to limit faults to those of interest.
  3. **Select Faults for 3D View**: Use the checkbox next to each fault in the fault list table to select individual faults or use the top checkbox to select all faults. The viewer will highlight the selected faults.
  4. **Navigate to the 3D Viewer**: Click the *View 3D* button to open the 3D fault viewer and display fault traces and surfaces for the selected faults on the 2D viewer.
- **Select Subducting Plate Surface(s)**: Use the *Subducting Plate Surfaces* dropdown in the control panel to select up to two surfaces to display.
- **Toggle Features**: Use checkboxes to show/hide satellite imagery, earthquakes, and boundary lines.
- **Change View**: Use the *Center* button to focus on a specific region by entering longitude and latitude. Use the *Tilted* button to reset the map to its default orientation.
- **Explore Earthquake Data**: Toggle the *Earthquakes* checkbox to display epicenters. Adjust the circle size slider to change the marker size for earthquakes.
- **Measure Distance**: Tick *Measure distance* under *Camera*, then click two points on the map.

## Data Download

GeoJSON file downloads of the fault models are available on the [downloads page](https://cfm.cascadiaquakes.org/downloads). In the 2D viewer, *Download (1 km)* downloads the selected faults.

## General Tips

- Visit the **About** menu for documentation and project contacts.
- **Interaction**: Use your mouse or touchscreen to pan, zoom, and rotate the map. Hover over features to display tooltips with additional information.
- **Full-Screen Mode**: In the 3D viewer, click the full-screen icon in the bottom-right corner.
- **Legend and North Arrow**: In the 3D viewer, the legend button above the logo shows or hides the legend, and the north arrow can be dragged anywhere on screen.
- **Help and Support**: If you encounter any issues, contact the project team listed under **About**.

## Development and Branch Support

The CFM Web Interface supports configuration and deployment across multiple branches. By default, the interface uses the **main** branch. However, for development or testing purposes, the **dev** branch is also supported. To use the dev branch, access the interface with the following URL:

- `http://your-cfm-server-address/?branch=dev`

Using the **dev** branch allows you to load development-specific configuration files and resources, making it easy to test new features without affecting the main interface.

## Local Installation

If you plan to download and install this package locally:

1. Download the CFM-WEB code from the [GitHub repository](https://github.com/cascadiaquakes/CRESCENT-CFM-WEB/).
2. Download and install [Docker](https://www.docker.com/get-started/).
3. Go to the [Cesium site](https://cesium.com/ion/) and create an account and get a token.
4. Go to the downloaded CFM-WEB code directory and create a `.env` file containing `CESIUM_KEYS={"cesium_access_token": "<your token>"}`.
5. In the root directory (directory above `app/`) build the image: `docker build -t cfm_viewer .`
6. Run the package: `docker run --env-file .env -p 8080:80 cfm_viewer`
7. On your browser go to the CFM viewer at [http://localhost:8080](http://localhost:8080).

## References

- U.S. Geological Survey, FDSN Event Web Service, [earthquake.usgs.gov/fdsnws/event/1](https://earthquake.usgs.gov/fdsnws/event/1/)
- U.S. Geological Survey, Quaternary Fault and Fold Database of the United States, [earthquake.usgs.gov/cfusion/qfault](https://earthquake.usgs.gov/cfusion/qfault/query_main_AB.cfm)
