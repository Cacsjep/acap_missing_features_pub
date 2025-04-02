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



#### Grafana and InfluxDB Integration

This guide shows you how to integrate Grafana with InfluxDB using the **Flux** query language. Follow the steps below to set up your datasource and create a dashboard for visualizing metrics such as CPU usage.

---

##### Prerequisites

!!! info 
    You should already have everything in place, as it’s configured identically to the Missing Feature ACAP setup.

- **Missing Feature ACAP:** InfluxDB Push enabled, and configured.
- **InfluxDB:** A running InfluxDB instance. 
- **InfluxDB API Token:** ACAP uses token-based authentication with InfluxDB.
- **InfluxDB Bucket:** You need an InfluxDB bucket.
- **InfluxDB Org:** You need the name of your InfluxDB organization.

---

##### Add InfluxDB Datasource in Grafana

First, navigate to your Grafana instance and add a new InfluxDB datasource.

![New Datasource](images/new_source.PNG)

---

##### Configure Datasource Settings

- **Datasource Name:** Set a name for your datasource.
- **Query Language:** Select **Flux** as the query language.

![Select Flux](images/flux.PNG)

---

##### Set Your InfluxDB HTTP URL

Specify your InfluxDB HTTP URL in the settings.

![InfluxDB Endpoint](images/endpoint.PNG)

---

##### Enter InfluxDB Credentials

Fill in your InfluxDB Organization, Token, and Default Bucket.

![InfluxDB Credentials](images/ifdb.PNG)

---

##### Create a Dashboard

Navigate to the dashboard section in Grafana and add a new visualization. For example, create a panel to monitor the **Missing Features CPU usage**.

[![](images/example_cpu_mf.PNG)](images/example_cpu_mf.PNG)

---

##### Extracting Flux Scripts from InfluxDB Data Explorer for Grafana

Use the InfluxDB Data Explorer to inspect the metrics and use the query builder in combinitation, to switch afterwards to script editor mode to copy the flux script for grafana.
[![](images/explore.PNG)](images/explore.PNG)

For example, let's locate our metadata event **device_io_virtualport** that we previously configured and executed to ensure an entry exists in the database:

- Select the bucket.
- Choose `metadata`.
- Set the filter to `name`.
- Select `device_io_virtualport`.
- Uncheck the `AGGREATE Function` on the right side (it's a boolean value).
- Enable the `View Raw Data` mode to display our entries in a table.


[![](images/io_metadata.PNG)](images/io_metadata.PNG)

- Click on the **Script Editor** button to view the Flux script.
- You can now use this Flux script in Grafana.

[![](images/io_script.PNG)](images/io_script.PNG)

##### Public Tutorials and Additional Resources

For further learning and more detailed tutorials, consider the following public resources:

- **Grafana Tutorials:**  
  [Official Grafana Tutorials](https://grafana.com/tutorials) – Learn more about creating dashboards, panels, and advanced visualizations.

- **InfluxDB Documentation:**  
  [Official InfluxDB Docs](https://docs.influxdata.com/influxdb/) – Detailed guides on installation, configuration, and usage of InfluxDB.

- **Flux Language Guide:**  
  [InfluxDB Flux Documentation](https://docs.influxdata.com/flux/latest/) – In-depth information on the Flux query language and its capabilities.

