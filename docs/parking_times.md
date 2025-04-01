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

#### Configuration

- **Max Parking Duration (Minutes):**  
  Specify the maximum number of minutes a vehicle is allowed to park.  
  > If a vehicle exceeds this duration, it is flagged as overparked.

- **Max Plate Hold Time (Minutes):**  
  Define the duration for which a license plate record is retained in the database before it is automatically deleted.

- **Save Changes:**  
  Click **Save** to store your configuration settings.


#### Monitoring Section

The monitoring section displays all currently detected vehicles and their parking details. Use the table below as a reference:

| **Column**              | **Description**                                                      |
|-------------------------|----------------------------------------------------------------------|
| **License Plate**       | Shows the recognized plate number.                                   |
| **Entry Time**          | Timestamp of when the vehicle entered the parking area.              |
| **Exit Time**           | Timestamp of when the vehicle exited.                                |
| **Parking Duration (min)** | Duration (in minutes) that the vehicle remained parked.           |
| **Exited**              | Indicates whether the vehicle has left the parking area.             |
| **Overparked**          | Indicates whether the vehicle exceeded the maximum parking duration. |

Additional controls in the monitoring interface include:

- **Table Freeze (Blue Pause Button):**  
  Stops the automatic refresh of the monitoring table, allowing you to review data without updates.

- **Show Only Overparked (Blue Car Icon):**  
  Filters the list to display only vehicles that are currently overparked.

!!! tip
    You can either use the dynamically generated overparking event condition in the AXIS event rule or use the Metadata to HTTPS feature to send all details regarding parking minutes and plate information to an external HTTPS server.