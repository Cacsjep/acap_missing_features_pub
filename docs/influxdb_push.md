# InfluxDB Push Configuration

!!! example "Complex Feature"
    This feature leverages a highly dynamic approach for exporting and pushing data, making it inherently more complex than standard functionalities. It requires a understanding of InfluxDB and its operational concepts, as InfluxDB may not be part of the day-to-day toolkit for many users. While setting up InfluxDB and connecting it with Missing Feature ACAP is straightforward for those with basic technical skills, it does demand some prior experience and familiarity with these systems.

#### Overview

This feature introduces two distinct approaches for data collection:

- **Metrics:**  
  All non metadata metrics have an interval-based configuration. You can specify how frequently each metric should be collected, making it easy to monitor performance indicators such as CPU usage, memory, or temperature on a regular schedule.

- **Metadata:**  
  Metadata is now event-based. Unlike metrics, metadata is not collected on a fixed interval but is triggered by specific events. Moreover, you can add as many metadata events as you want, allowing you to capture detailed information exactly when it matters.

---

#### Interval-Based Settings
Each non metadata metric includes an interval setting where you can define the frequency of data capture (e.g., every 5 seconds, 10 seconds, etc.).


#### Use it with Grafana

The primary idea behind this feature is to use it with Grafana, allowing you to build any dashboard you can imagine. By leveraging Grafana's powerful visualization capabilities alongside your InfluxDB data, you can create insightful and dynamic dashboards tailored to your needs.

---

#### Prerequisites

- **InfluxDB:** A running InfluxDB instance. If you don't have one, follow the [InfluxDB Get Started guide](https://docs.influxdata.com/influxdb/v2/get-started/setup/).
- **InfluxDB API Token:** ACAP uses token-based authentication with InfluxDB. Please create an API token by following the instructions in the [InfluxDB Create Token guide](https://docs.influxdata.com/influxdb/v2/get-started/setup/#create-an-all-access-api-token).
- **InfluxDB Bucket:** You need an InfluxDB bucket.
- **InfluxDB Org:** You need the name of your InfluxDB organization.


#### Configure non Metadata Metrics

Enable or disable the metric via the switch, and open the configuration via the vertical 3 dots.
[![](images/configenable.PNG)](images/configenable.PNG)

- **Set Interval:**  
    For each metric, define the desired interval at which data should be pushed to InfluxDB.
- **Save Settings:**  
    Confirm and save your interval configurations for each metric.

#### Configure Metadata Events

Enable or disable the metadata via the switch, and open the configuration via the vertical 3 dots.
[![](images/configenable.PNG)](images/configenable.PNG)

- **Add Metadata Event:**  
    Click on the option to add a new metadata event.
- **Select Trigger:**  
    Choose the event that will trigger the metadata capture (e.g., sensor threshold exceeded, error event, etc.).
- **Define Metadata Fields:**  
    Specify which metadata fields should be included in the payload.
- **Define Datapoint Name:**  
    The datapoint name is the key, with which we store the data in InfluxDB.
- **Repeat:**  
    Add as many metadata events as needed.
- **Save Configuration:**  
    Save your metadata settings once you have added all desired events.

##### Metadata Day Night Example 
Push the Day Night metadata event
[![](images/ov.PNG)](images/ov.PNG)

##### Metadata AXIS Object Analytics - Area Count Humans Example
Push the Day Night metadata event
[![](images/human.PNG)](images/human.PNG)
