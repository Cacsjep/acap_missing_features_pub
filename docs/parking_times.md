# Parking Times Configuration

!!! note
    Only works with AXIS License Plate Verifier (ALPV)

#### Preparing AXIS License Plate Verifier

- **Configure ALPV:**  
  Ensure that your AXIS License Plate Verifier is set up with multiple Regions of Interest (ROIs) and a directional arrow. This configuration is essential for correctly detecting cars that enter or exit the parking area.

---

#### Access the Configuration Page

- **Open the Camera Web Interface:**  
  Navigate to your AXIS camera’s IP address using your web browser.
- **Navigate to the APP Section:**  
  Locate and click on the **APP** section.
- **Enable Parking Times:**  
  Find **Missing Feature ACAP**, open it, and enable **Parking Times** from the feature list to open its configuration panel.

---

#### Genaral Configuration

- **Max Parking Duration (Minutes):**  
  Specify the maximum number of minutes a vehicle is allowed to park.  
  > If a vehicle exceeds this duration, it is flagged as overparked.

- **Auto-Removal (Minutes):**  
  Define the duration for which a license plate record is retained in the database before it is automatically deleted.

- **LPR Event Types:**  
  - **New:** Indicates the first detection of a license plate.
  - **Update:**   Represents either a correction to a previously detected license plate (e.g.,
      character refinement), or when a direction is identified as the plate is
      tracked across the image.
  - **Lost:** Marks the last tracked position of the license plate before it leaves the
      image. This event also includes the direction in which the plate exited.

- **Save Changes:**  
  Click **Save** to store your configuration settings.

#### Parking Zones Configuration

Parking zones make it possible to support most parking scenarios, including setups with multiple zones or areas.

The system supports:

  - A **single camera**, acting as both **entry and exit**.
  - **Multiple cameras**, where each camera must be assigned a `Role` within the zone.

##### Configuration Rules (Roles)

To ensure correct behavior, the following rules must be respected:

- A zone **cannot have multiple cameras** with the role `ENTRY_AND_EXIT`.
- A zone that **does not contain a camera** with the role `ENTRY_AND_EXIT` **must include** at least one `ENTRY` and one `EXIT` role.
- A zone **with a camera** set to `ENTRY_AND_EXIT` **can also include** additional cameras with the `ENTRY` or `EXIT` roles.
- The same camera **cannot be assigned multiple times** to a single zone.

---

##### Configuration

!!! danger "All cameras must be online"
    After saving, a connection test is automatically performed for all external cameras  
    to verify accessibility and credentials.  
    **Make sure all cameras are online during configuration.**

!!! note "ACAP-Assigned Camera Restriction"
    The initial default zone cannot be deleted because it is assigned to the internal camera running the ACAP.
    Also, the internal camera entry **cannot be removed** from this zone.

!!! warning "Authentication Requirement"
    Only **Digest Authentication** is supported for external cameras.  
    Ensure that your cameras are running an **up-to-date firmware**, and that **digest authentication is enabled**.

###### Zone Buttons

**Edit Zone**

![](images/edit.PNG)

**Remove Zone**

![](images/rem.PNG)

---

###### Add New Zone

![](images/addzone.PNG)

Add a new zone by clicking the `ADD ZONE` button.

[![](images/new_zone.PNG)](images/new_zone.PNG)

After adding a new zone, you will see that the configuration is initially incomplete.  
Click on the `Zone Edit` button to configure the zone.
Configure the camera where ACAP is running or add new ones, and follow the `Configuration Roles`.

---

###### Camera Settings

- **Name**  
  Name of the camera.

- **IP Address**  
  Enter the IP address of the external camera.

- **Username**  
  Enter the username used to access the external camera.

- **Password**  
  Enter the password for the external camera.

- **Use HTTPS**  
  Enable this option to communicate securely with the external camera using HTTPS.

- **Role**  
  Specify the role of the camera within the zone (`Entry`, `Exit`, or `Entry and Exit`).



#### Monitoring Section

The monitoring section displays all currently detected vehicles and their parking details. Use the table below as a reference:

| **Column**              | **Description**                                                      |
|-------------------------|----------------------------------------------------------------------|
| **License Plate**       | Shows the recognized plate number.                                   |
| **Entry Time**          | Timestamp of when the vehicle entered the parking area.              |
| **Exit Time**           | Timestamp of when the vehicle exited.                                |
| **Zone**                | Zone Name.                                                           |
| **Camera**                | Camera Name.                                                           |
| **Parking Duration (min)** | Duration (in minutes) that the vehicle remained parked.           |
| **Exited**              | Indicates whether the vehicle has left the parking area.             |
| **Parking Time Exceeded**          | Indicates whether the vehicle exceeded the maximum parking duration. |

Additional controls in the monitoring interface include:

- **Table Freeze (Blue Pause Button):**  
  Stops the automatic refresh of the monitoring table, allowing you to review data without updates.

- **Show Only exceeded (Blue Car Icon):**  
  Filters the list to display only vehicles that are currently exceeded.

!!! tip
    You can either use the dynamically generated **Parking Time Exceeded**, **Car Entered**, **Car Exited** events in the AXIS event rule or use the Metadata to HTTPS feature to send all details regarding parking minutes and plate information to an external HTTPS server.
    
    [![](images/events.PNG)](images/events.PNG)

#### Connection Test

!!! danger "All cameras must be online"
    After saving, a connection test is automatically performed for all external cameras  
    to verify accessibility and credentials.  
    **Make sure all cameras are online during configuration.**

#### Use Live Logs for Troubleshooting

Open the **Live Logs** by clicking the logging button located in the bottom-left corner of the interface to view real-time log entries.

Use the logs to validate incoming **AXIS License Plate Verifier metadata messages**.  
This is especially helpful for troubleshooting.

[![](images/log.PNG)](images/log.PNG)