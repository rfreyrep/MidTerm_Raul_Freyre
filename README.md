# MidTerm_Raul_Freyre
This repository is meant to be for the assignment of the Mid Term for the GIS web mapping course in Fall 2025

#  Web GIS MidTerm – McDonald’s and Shell Stations in Wyoming

## Overview
This project was created as part of Question 8 of the GIS quiz. The objective was to build an interactive Web GIS map using Leaflet that visualizes at least two datasets and includes a spatial analysis component.

I selected two point-based datasets:
- McDonald’s Restaurants (USA)
- Shell Gas Stations (USA & Canada)

Both datasets were originally downloaded from [POI Factory](https://www.poi-factory.com/).
---

## 1. Data Preparation and Cleaning
After downloading both datasets as .csv files, the data included hundreds of locations across the U.S. and Canada. To make the analysis manageable and meaningful, I decided to focus exclusively on the state of Wyoming.

Using Python (Pandas), I:
- Filtered the rows containing `"WY"` in their address or name fields.
- Cleaned up the column names and removed duplicates.
- Kept only the key attributes:
  - name – location name  
  - lat – latitude  
  - lon – longitude  
  - info – additional address or service info  

Finally, the cleaned datasets were exported as JSON files (mcdonalds_wy.json and shell_wy.json), which were then used directly in the Leaflet web map.

---

## 2. Web Map Development
The web map was built using Leaflet.js, for interactive maps.  
Both JSON datasets were loaded dynamically using fetch(), and the points were displayed with circle markers and popups containing location information.

The map includes:
- Two datasets as toggleable layers:  
  - McDonald’s Restaurants (orange markers)  
  - Shell Gas Stations (green markers)  
- Two basemap options:  
  - OpenStreetMap (Street view)  
  - Esri World Imagery (Satellite view)  
- A small control box summarizing the analysis results.

---

## 3. Analytical Approach
The analysis aimed to explore whether McDonald’s restaurants tend to be located near Shell gas stations — reflecting a potential clustering of services that cater to travelers.

To evaluate this, I implemented a simple proximity analysis using the Haversine distance formula, which calculates the great-circle distance between two coordinates on Earth.

For each Shell station, the code checks all McDonald’s locations and counts how many are within **2 kilometers**.  
This distance threshold was chosen to represent reasonable driving proximity along highways or within towns.

---

## 4. Results and Findings
- McDonald’s locations analyzed: 29  
- Shell gas stations analyzed: 16  
- Number of pairs within 2 km: (calculated dynamically on the map) 

The proximity analysis found multiple overlaps, especially around urban centers such as Cheyenne, Casper, and Laramie, where McDonald’s and Shell stations are commonly co-located or within short driving distance of each other.

---

## 5. Insights
The results suggest that both McDonald’s and Shell use similar location strategies that prioritize:
- High-traffic corridors (e.g., interstates and main highways)  
- Accessibility for drivers and travelers  
- Visibility and convenience in populated areas  

In smaller towns and rural regions, there are fewer overlaps, likely due to lower population density and limited commercial clustering.  
Overall, the spatial relationship highlights how fast-food and fuel retail chains tend to cluster near transportation routes, reinforcing their mutual dependence on road-based consumer behavior.

---

## 6. Files Included
| File | Description |
|------|--------------|
| index.html | Main web page with the interactive Leaflet map and analysis code |
| mcdonalds_wy.json | Cleaned JSON dataset of McDonald’s locations in Wyoming |
| shell_wy.json | Cleaned JSON dataset of Shell gas stations in Wyoming |

---

## 7. Deployment
The project can be hosted directly on GitHub Pages.  
Once uploaded, the map can be viewed online by navigating to:  

<https://rfreyrep.github.io/MidTerm_Raul_Freyre/>


---

## 8. Conclusion
This project demonstrates how open geospatial data can be processed, visualized, and analyzed directly on the web using modern client-side technologies.  
Even with simple proximity logic, Web GIS provides valuable insights into how businesses and infrastructure interact spatially, in this case, showing that fast food and fuel services often form part of the same travel network in Wyoming.
