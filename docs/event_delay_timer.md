# Event Delay Timer Configuration

Configure the Event Delay Timer feature to introduce a delay between a trigger event and the execution of an action. 

---

#### Access the Configuration Page

- **Open your AXIS camera’s web interface.**
- **Navigate to the APP section.**
- **Locate Missing Feature ACAP:**  
  Open it and enable **Event Delay Timer** from the feature list to launch its configuration panel.

---

#### Set the Delay Duration

- **Delay (Seconds):**  
    Enter the number of seconds to wait after the trigger event occurs before executing the action.  

- **Hold Time (Seconds or Minutes/Days):**  
    Specify how long the dynamically registered event should remain active after the delay period completes. 

- **Prevent Overlap:**  
    When enabled, only one timer can run at a time. Any new events are ignored if a timer is already in its waiting period (the configured delay) or within its hold time. This prevents multiple triggers from overlapping, ensuring a clean, sequential workflow.

---

#### Configure the Trigger Event

- **Trigger Event:**  
  Choose the event source that will activate the delay timer. Examples include Device I/O Virtual Input, Motion Detection, or Video Analytics.

- **Source / Data Fields:**  
  Depending on the selected trigger event, additional details may be required—such as specifying the port number for a virtual input or a particular I/O channel.


[![](images/event_trigger.PNG)](images/event_trigger.PNG)

---

#### Save and Verify

- **Save the Configuration:**  
  Once all settings are configured, save your changes.
  
- **Integration with AXIS Rule System:**  
  The generated Event Condition can now be used within the AXIS Rule System to further automate workflows.

#### Use with AXIS Rule System

To utilize the Delay Complete event from Missing Feature ACAP in your AXIS camera’s rule system, follow these steps:

1. **Add a New Rule**  
      - In the AXIS camera’s web interface, go to **System** > **Events** > **Rules** and click **Add Rule**.

2. **Specify the Rule Name**  
      - Give your rule a descriptive name, for example, **LED Delay**.

3. **Set the Condition**  
      - From the dropdown, select **Missing Features: Delay Complete (10s)**.  

4. **Configure the Action**  
      - Choose **Flash status LED** (or any other desired action).
      - Select the **Color** (e.g., **Green**).
      - Set the **Duration** (e.g., **00:00:04**).

5. **Save the Rule**  
      - Click **Save** to apply your settings.

Once the delay completes, the rule will automatically trigger the configured action—allowing you to automate follow-up tasks (such as flashing an LED) after a timed delay.

[![](images/rule.PNG)](images/rule.PNG)