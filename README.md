# Dev Graph Widget for HADashboard

example dashboard for each of the possible history types:
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
