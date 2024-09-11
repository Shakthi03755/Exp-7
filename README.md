# Exp-7
from bokeh.io import show
from bokeh.models import ColumnDataSource, HoverTool
from bokeh.plotting import figure
from bokeh.layouts import column
import pandas as pd
import folium
# Load your data
data = pd.read_csv(r'C:\Users\shakthi\Downloads\cities.csv.zip')
# Create a Bokeh figure
p = figure(width=800, height=400, tools='pan,wheel_zoom,reset')
# Create a ColumnDataSource to hold data
source = ColumnDataSource(data)
# Add circle markers to the figure
p.circle(x='longitude', y='latitude', size=10, source=source, color='orange')
# Create a hover tool for mouse rollover effect
hover = HoverTool()
hover.tooltips = [("Info", "@country_name"), ("latitude", "@latitude"), ("longitude", "@longitude")]
p.add_tools(hover)
# Display the Bokeh plot
layout = column(p)
show(layout)
# Create a map centered at a specific location
m = folium.Map(location=[latitude, longitude], zoom_start=10)
# Add markers for your data points
for index, row in data.iterrows():
    folium.Marker(
        location=[row['Latitude'], row['Longitude']],
        popup=row['Info'],  # Display additional info on mouse click
    ).add_to(m)
# Save the map to an HTML file
m.save('map.html')
![1000051993](https://github.com/user-attachments/assets/381c9a95-b204-4f57-beb2-9d37fa6d0e72)
![1000051995](https://github.com/user-attachments/assets/e006e703-b5b8-40b9-ab37-c9ded1ec34f1)
