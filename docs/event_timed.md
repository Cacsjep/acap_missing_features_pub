# Timed Event Sequence Configuration

This configuration allows you to trigger a follow‑up event only if it occurs within a specific time window after an initial event. Follow these steps to set it up:

---

#### Access the Configuration Page

- **Open your AXIS camera’s web interface:**  
  Navigate to the camera’s IP address using your preferred web browser.
- **Go to the APP Section:**  
  In the web interface, locate and click on the APP section.
- **Enable Timed Event Sequence:**  
  Find **Missing Feature ACAP**, open it, and enable the **Timed Event Sequence** from the feature list. This will launch its configuration panel.

---

#### Configure the Timed Event Sequence

- **Name:**  
  Enter the name that will appear in AXIS rule conditions.
- **Seconds:**  
  Set the maximum interval (in seconds) between the initial event and the follow‑up event before the condition times out.
- **Hold Time (ms):**  
  Specify how long the generated event remains active after it’s triggered.
- **Only One Instance:**  
  Enable this option to ensure that only one timer can run at a time—preventing new events from overlapping with an already active event.
- **Initial Trigger:**  
  Choose the event that will trigger the start of the sequence.
- **Follow-up Trigger:**  
  Select the event that must occur within the configured timeframe (in seconds) to complete the sequence.

---

#### 3. Save the Configuration

- **Save:**  
  Once you have entered all required settings, click **Save** to apply the configuration.

#### Use with AXIS Rule System

To utilize the Delay Complete event from Missing Feature ACAP in your AXIS camera’s rule system, follow these steps:

1. **Add a New Rule**  
      - In the AXIS camera’s web interface, go to **System** > **Events** > **Rules** and click **Add Rule**.

2. **Specify the Rule Name**  
      - Give your rule a descriptive name, for example, **Two Events in-time**.

3. **Set the Condition**  
      - From the dropdown, select **Missing Features: Timed Event Sequence**.  

4. **Configure the Action**  
      - Choose **Toggle I/O once** (or any other desired action).
      - Select the **Port**.
      - Set the **State**.
      - Set the **Duration**.

5. **Save the Rule**  
      - Click **Save** to apply your settings.

[![](images/rule.PNG)](images/rule.PNG)