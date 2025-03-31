# Metadata to HTTPS Configuration

This section describes how to configure Missing Feature ACAP to send metadata over HTTP/HTTPS. The metadata payload is sent to a specified endpoint when a trigger event occurs.

---

#### Access the Configuration Page

- **Open your AXIS camera’s web interface:**  
    Enter your camera’s IP address in your browser.
- **Navigate to the APP section:**  
    Locate the APP section in the interface.
- **Enable Metadata to HTTPS:**  
    Find **Missing Feature ACAP**, open it, and enable **Metadata to HTTPS** from the feature list. This will open the configuration panel.

---

#### Configure the Trigger Event

- **Trigger Event:**  
    Select the source event that will trigger the HTTPS call.
- **Additional Parameters:**  
    Depending on the chosen event, you may need to configure extra parameters (e.g., a port number for virtual input).

---

#### Specify the HTTPS/HTTP Endpoint

- **HTTP Protocol:**  
    Choose between **HTTP** or **HTTPS**.
- **HTTPS/HTTP URL:**  
    Enter the URL of the server that will receive the metadata.  
    _Example:_ `https://yourserver.com:3333`
- **Skip Verify SSL (When using HTTPS):**  
    Check this option to bypass SSL certificate validation.  

!!! note

    The HTTP method used is **POST**

---

#### Authentication

- **Authentication Mode:**  
    Select the mode that best suits your web server:
    - **None:** No authentication.
    - **Basic:** Basic authentication as specified in RFC 7617.
    - **Digest:** Digest authentication as defined in RFC 7616.
    - **Bearer:** Bearer token authentication as outlined in RFC 6750.
    - **Plain:** Sends the username and password in the JSON payload (non-standard; use with caution).

- **HTTP Headers:**  
    Optionally add one or more HTTP headers to include in the POST request.
  
- **Include Image:**  
    If enabled, a Base64-encoded image will be included in the metadata payload when the event is triggered (e.g., a snapshot relevant to the event).

- **History Mode:**  
    Enable History Mode to store the last received event in memory. When a trigger event occurs, the system reuses this event instead of requiring a new one.  
    _Example:_ When using AXIS License Plate Verifier events, if a license plate is detected, the event is stored and later used when an input trigger (like an inductive loop sensor) is activated. This ensures that the previously detected license plate information is still available for access control, even if the detection occurred slightly earlier.

---

#### Save and Test

- **Save:**  
    Click **Save** to store your configuration. A test POST request is automatically made to ensure that the web server is reachable.
- **Trigger the Event:**  
    Cause the trigger event to occur (e.g., toggle the virtual input or trigger motion detection).
- **Check Your Endpoint:**  
    Verify that your external service or server receives the HTTPS POST with the JSON payload. If images are included, confirm that the payload contains the Base64-encoded data.


#### Payload Information

<p>
  As described in the
  <a href="https://developer.axis.com/vapix/network-video/event-streaming-over-websocket/#event-streaming-1"
      target="_blank" rel="noopener noreferrer">
      VAPIX Library
  </a>, the payload for the Metadata event is contained within the <code>notification</code>
  parameter (i.e. <code>params.notification</code>).
</p>
<p>
  When sending the POST request to the HTTPS endpoint, the Metadata notification JSON object is
  assigned to the key <code>event</code>. This <code>event</code> key encapsulates the
  following properties:
</p>
``` json
"event": {
  "topic": "tnsaxis:CameraApplicationPlatform/ObjectAnalytics/Device1Scenario1",
  "timestamp": "1741583919319",
  "message": {
    "data": {
      "active": "1",
      "classTypes": "human",
      "objectId": "622864",
      "scenarioType": "ObjectInArea",
      "triggerTime": "2025-03-10T05:18:39.319+0000"
    },
    "key": {},
    "source": {}
  }
}
```

``` json title="ObjectAnalytics Example"
"event": {
  "topic": "tnsaxis:CameraApplicationPlatform/ObjectAnalytics/Device1Scenario1",
  "timestamp": 1741583919319,
  "message": {
      "data": {
          "active": "1",
          "classTypes": "human",
          "objectId": "622864",
          "scenarioType": "ObjectInArea",
          "triggerTime": "2025-03-10T05:18:39.319+0000"
      },
      "key": {

      },
      "source": {

      }
  }
}
```

``` json title="VirtualInput Example"
"event": {
  "topic": "tns1:Device/tnsaxis:IO/VirtualInput",
  "timestamp": 1741584445118,
  "message": {
      "data": {
          "active": "1"
      },
      "key": {

      },
      "source": {
          "port": "1"
      }
  }
}
```

``` json title="Virtual Input with Image Example"
"event": {
      "topic": "tns1:Device/tnsaxis:IO/VirtualInput",
      "timestamp": 1741584445118,
      "message": {
          "data": {
              "active": "1"
          },
          "key": {

          },
          "source": {
              "port": "1"
          }
      }
  },
  "image": "/9j/4AAQSkZJRgABAQAAAQABAAD//gAFAAAA/9sAQwA.....NRuuRUtNIoApup"
```

``` json title="Parking Monitor - Overparked Example"
"event": {
    "topic": "tnsaxis:CameraApplicationPlatform/ax_msf/overparked",
    "timestamp": 1741778727035,
    "message": {
        "data": {
            "active": "1",
            "entryTime": "1741778233",
            "exitTime": "1741778727",
            "parkedMinutes": "8",
            "plate": "CAR005",
            "plateImage": "base64image"
        },
        "key": {

        },
        "source": {

        }
    }
}
```