# sherin-exp-7
from bokeh.io import show
from bokeh.models import ColumnDataSource, HoverTool
from bokeh.plotting import figure
from bokeh.layouts import column
import pandas as pd
import folium
# Load your data
data = pd.read_csv(r'C:\Users\sheri\Downloads\cities.csv.zip')
# Create a Bokeh figure
p = figure(width=800, height=400, tools='pan,wheel_zoom,reset')
# Create a ColumnDataSource to hold data
source = ColumnDataSource(data)
# Add circle markers to the figure
p.circle(x='longitude', y='latitude', size=10, source=source, color='orange')
# Create a hover tool for mouse rollover effect
hover = HoverTool()
hover.tooltips = [("Info", "@state_name"), ("Latitude", "@latitude"), ("Longitude", "@longitude")]
p.add_tools(hover)
# Display the Bokeh plot
layout = column(p)
show(layout)
# Create a map centered at a specific location
m = folium.Map(location=[Longitude,Latitude], zoom_start=10)
# Add markers for your data points
for index, row in data.iterrows():
    folium.Marker(
        location=[row['latitude'], row['longitude']],
        popup=row['Info'],  # Display additional info on mouse click
    ).add_to(m)
# Save the map to an HTML file
m.save('map.html')
![Screenshot (85)](https://github.com/user-attachments/assets/ed3b1692-3bc5-480e-8679-fb77b5c5d696)
![Screenshot (86)](https://github.com/user-attachments/assets/6ef270f4-e8f0-42d8-b4aa-cf80a0bcf25e)
