# Changelog

##### Legend  
- **I:** Improvement  
- **B:** Bugfix 
- **F:** New Feature  
- **C:** Change  


---

##### V0.6.10 – 04.04.2025
- **B:** Fix metadatapoint duplicated name validation
   
---

##### V0.6.9 – 04.04.2025
- **I:** Improve InfluxDB Feature configuration
- **I:** Fix InfluxDB connection test, org and bucket must belong
- **B:** Fix dataless events in when using in InfluxDB Feature
- **I:** Add version field to JSON configurations for futher upgrade between versions
   
---

##### V0.6.8 – 04.04.2025
- **I:** Add triggerd based deletion in parking times
  
---

##### V0.6.7 – 03.04.2025
- **I:** Live log, better visibility
  
---

##### V0.6.6 – 03.04.2025
- **I:** Switched to zone-based approach in the parking feature
- **I:** Add enter and exit events to parking feature
  
---

##### V0.6.4 – 02.04.2025
- **B:** Debug logging when loglevel is info
- **B:** False internal logging messages in InfluxDB metrics
- **B:** Remove old close channel on influxDB, prevent sometimes stopping 
- **B:** Skip procs that not more active when iterating it to get proc stats (short lived)
- **I:** Improve metrics error message
- **C:** Remove default dev config from InfluxDB 
  
---

##### V0.6.3 – 02.04.2025
- **I:** Dual camera mode for parking times
  
---

##### V0.6.2 – 01.04.2025
- **B:** InfluxDB Feature Stop 
  
---

##### V0.6.1 – 31.03.2025
- **C:** Change sunevents to statefull events.
- **C:** Change countdown event to statefull.
- **C:** Change timed seq. event to statefull.
  
---

##### V0.6.9 – 27.03.2025
- **F:** InfluxDB Push

---

##### V0.5.1 – 24.03.2025

- **C:** Merge sun events into one event instead of two separate events.
- **C:** Remove auto triggering of events because the new events engine does not need this.
- **I:** Use index-based timestamps for images for faster database operations.
- **C:** Separate images delete tickers.
- **I:** Improve image deletion and add information when in delete state.
- **F:** Timed event condition.
- **I:** WebSocket logging.
- **I:** Log level – settings.
- **I:** Internal overlay management improved.

---

##### V0.4.3 – 20.03.2025

- **B:** Sunrise/Sunset latitude out of range (-180, 180) fix.

---

##### V0.4.2 – 20.03.2025

- **I:** Sunrise/Sunset configuration simplified by using map.

---

##### V0.4.1 – 19.03.2025

- **F:** Rewrite of event system for better configuration of an event trigger.
- **I:** Improve event countdown time overlay when non-realtime clock is used.
- **I:** Add SD-card information to storage info.
- **I:** Restyle toast messages.
- **I:** Rename AX events to start with uppercase.
- **I:** Add sunrise/sunset time information to UI.
- **B:** Overlay removal bug (app crash) when disabling the countdown feature.

---

##### V0.3.2 – 16.03.2025

- **B:** EULA dialog persistence fixed.

---

##### V0.3.1 – 16.03.2025

- **I:** EULA / First usage.
- **I:** Metadata to HTTPS authentication methods generalized.
- **I:** Metadata to HTTPS, headers added.
