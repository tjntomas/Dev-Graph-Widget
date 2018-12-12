# Dev Graph Widget for HADashboard

This is the dev section for the graph widget for HADasboard that can display data from 3 sources:
* Home Assistant history
* Influxdb
* No history, only display incoming updated data as long as the widget is loaded in a dashboard. This menas that the graph will be empty until at least one update has been received.

Which data source that is used depends on the widget setting
````
history_type: ha  # options are ha|influxdb|none
````

To use the widget, you need to:
1. copy the basehagraph folder to your custom_widgets folder
2. copy plotly-latest.min.js from the custom_css folder to your custom_css folder
3. add the following to the variables.yaml file of the skin you are using:
````yaml
graph_style: "border-radius: 0px; $background_style_graph"
graph_legend_text_color: "#cccccc"
graph_grid_color: "#888888"
graph_title_color: "#aaaaaa"
graph_x_axis_text_color: "#aaaaaa"
graph_y_axis_legend_color: "#aaaaaa"
graph_y_axis_text_color: "#aaaaaa"
graph_influxdb_path: http://path_to_your_influxdb_server:8086
graph_influxdb_path_local: http://local_path_to_your_influxdb_server:8086
graph_widget_style: "border-bottom-left-radius: 10px;border-bottom-right-radius: 10px;border-top-left-radius: 10px;border-top-right-radius: 10px;"
graph_trace_colors: "1.1"
graph_fill_colors: "1.1"
graph_bar_colors: "1.1"
graph_bar_multi: "1.1"
graph_user: YOUR_INFLUXDB_USER_NAME  # only needed if you have activated authentication for influxdb
graph_password: YOUR_INFLUXDB_PASSWORD  # only needed if you have activated authentication for influxdb
graph_degrees_celsius_text: "Degrees Celsius" # Adjust to your own language if needed.
graph_degrees_fahrenheit_text: "Degrees Fahrenheit" Adjust to your own language if needed.
graph_percent_text: "Percent"  Adjust to your own language if needed.
hagraph_path: http://path_to_your_home_assistance_instance:8123  # will change name to base_url or similar
hagraph_token: YOUR_LONG_LIVED_ACCESS_TOKEN # Can be created through the Home Assistant front end.
````

example dashboards for each of the possible history types:
````yaml
graph_ha:
    widget_type: hagraph
    max: 70
    min: 10
    time: 12h
    samples: 200
    title: "Värmesystemet"
    entities:
      - sensor.fibaro_system_fgbs001_universal_binary_sensor_temperature_2
      - sensor.fibaro_system_fgbs001_universal_binary_sensor_temperature
    titles:
      - Framledning
      - Varmvatten
    units: "°C"
    fill: "tozeroy"
    colorIndex: 7
    height: 300
    value_in_legend: 1
    log: 1
    history_type: ha

graph_influxdb:
    widget_type: hagraph
    max: 70
    min: 10
    time: 12h
    samples: 200
    title: "Värmesystemet"
    units: "°C"
    influxdb_units: 
      - "°C"
      - "°C"
    entities:
      - sensor.fibaro_system_fgbs001_universal_binary_sensor_temperature_2
      - sensor.fibaro_system_fgbs001_universal_binary_sensor_temperature
    titles:
      - Framledning
      - Varmvatten
    fill: "tozeroy"
    colorIndex: 7
    value_in_legend: 1
    height: 300
    history_type: influxdb

graph_latest:
    widget_type: hagraph
    max: 70
    min: 10
    time: 12h
    samples: 200
    title: "Värmesystemet"
    units: "°C"
    entities:
      - sensor.fibaro_system_fgbs001_universal_binary_sensor_temperature_2
      - sensor.fibaro_system_fgbs001_universal_binary_sensor_temperature
    titles:
      - Framledning
      - Varmvatten
    fill: "tozeroy"
    colorIndex: 7
    value_in_legend: 1
    height: 300
    history_type: none
````
