# Event Countdown Configuration

#### Access the Configuration Page

- **Open your AXIS camera’s web interface.**
- **Navigate to the APP section.**
- **Find Missing Feature ACAP:**  
  Open it and enable **Event Countdown** from the feature list to launch its configuration panel.

---

#### Set the Countdown Duration

- **Countdown Seconds:**  
  Enter the total number of seconds to count down once the start event is triggered.

---

#### Configure Start and Stop Events

- **Start Event:**  
  Choose the input or trigger that initiates the countdown (e.g., Virtual Input, Motion Detection, Device I/O). When this event occurs, the countdown immediately begins.

- **Stop Event:**  
  Select the event or condition that stops the countdown. This can be a separate Virtual Input, a specific device output, or a software trigger. When this event fires—or when the timer reaches zero—the countdown stops.

---

#### Optional On-Screen Overlay

- **Enable Overlay:**  
  Toggle On if you want to display the countdown on-screen.

- **Position:**  
  Choose where on the video feed the countdown overlay should appear (e.g., top-left, bottom-right).

- **Text Color & Format:**  
  Select the text color, font size, and other formatting options to ensure the countdown is clearly visible.

- **Refresh Rate:**  
  Adjust how frequently the on-screen timer updates.

- **Use Realtime Clock:**  
  Use this option to display the real clock instead of the countdown time.

- **Datetime Format:**  
  Specify the format to be used for the time overlay.

---

#### Precision and Latency

- **Latency:**  
  The countdown is designed to stop within 50ms of receiving its stop event—making it ideal for industrial or high-precision workflows.

- **Event Integration:**  
  While the Event Countdown feature itself doesn’t capture images, it can trigger actions (like image captures or notifications) in real time.


#### Manually Start / Stop
For testing purposes, you can manually start or stop the countdown by using the two buttons located to the left of the save button.

[![](images/manual.PNG)](images/manual.PNG)

#### Use with AXIS Rule System

To utilize the countdown events from Missing Feature ACAP in your AXIS camera’s rule system, follow these steps:

1. **Add a New Rule**  
      - In the AXIS camera’s web interface, go to **System** > **Events** > **Rules** and click **Add Rule**.

2. **Specify the Rule Name**  
      - Give your rule a descriptive name, for example, **Record during countdown**.

3. **Set the Condition**  
      - From the dropdown, select **Missing Features: Countdown**.  

4. **Configure the Action**  
      - Choose **Record video while rule is active** (or any other desired action).
      - Set the **Storage**.
      - Set the **Camera**.

5. **Save the Rule**  
      - Click **Save** to apply your settings.


[![](images/rule.PNG)](images/rule.PNG)