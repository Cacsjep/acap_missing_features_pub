# InfluxDB Push

## Overview

This feature introduces two distinct approaches for data collection:

- **Metrics:**  
  All non metadata metrics have an interval-based configuration. You can specify how frequently each metric should be collected, making it easy to monitor performance indicators such as CPU usage, memory, or temperature on a regular schedule.

- **Metadata:**  
  Metadata is now event-based. Unlike metrics, metadata is not collected on a fixed interval but is triggered by specific events. Moreover, you can add as many metadata events as you want, allowing you to capture detailed information exactly when it matters.

---

#### Interval-Based Settings
Each non metadata metric includes an interval setting where you can define the frequency of data capture (e.g., every 5 seconds, 10 seconds, etc.).

---

#### How to Configure

##### Access the Configuration Panel

- Navigate to the metrics and metadata configuration section within the application.

##### Configure Metrics

- **Set Interval:**  
    For each metric, define the desired interval at which data should be captured.
- **Save Settings:**  
    Confirm and save your interval configurations for each metric.

##### Add and Configure Metadata Events

- **Add Metadata Event:**  
    Click on the option to add a new metadata event.
- **Select Trigger:**  
    Choose the event that will trigger the metadata capture (e.g., sensor threshold exceeded, error event, etc.).
- **Define Metadata Fields:**  
    Specify which metadata fields should be included in the payload.
- **Set Conditions (Optional):**  
    Define any conditions that must be met for the event to trigger metadata capture.
- **Repeat:**  
    Add as many metadata events as needed.
- **Save Configuration:**  
    Save your metadata settings once you have added all desired events.