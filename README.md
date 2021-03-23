# charts

### 1. Custom a folium map
```python
m = folium.Map(location=[10.787884, 106.698402], zoom_start=12) # center on hcmc
fs = plugins.Fullscreen().add_to(m)

feature_group = folium.FeatureGroup("Locations")

for lat, lng, name in zip(df_map['lat'], df_map['long'], df_map['description']):
    # make icon changes with conditions
    if status == 2:
        icon = folium.Icon(color='green', icon_color='white', icon='glyphicon-star', size=(5,5))
    elif status == 1:
        icon = folium.Icon(color='orange', icon_color='white', icon='glyphicon-wrench', size=(5,5))
    else:
        icon = folium.Icon(color='red', icon_color='white', icon='glyphicon-send', size=(5,5))

    feature_group.add_child(folium.Marker(location=[lat,lng],popup=folium.Popup(name, max_width=500),icon=icon))

m.add_child(feature_group)

folium_static(m) # call to render Folium map in Streamlit
```

### 2. Hide a x-axis or y-axis labels
```python
xaxis = go.XAxis(title = 'Time', showticklabels=False)
```
