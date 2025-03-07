# Evidence Collection After the Attack

## Connecting to Splunk and Querying Logs

To analyze the attack, connect to Splunk and execute the following queries:

### 1. Querying Failed Login Attempts
```splunk
index="endpoint" tinashe
```
*Note: Here, `tinashe` is the username that was targeted during the attack.*

- Check the **Event Code** and look for **Event ID 4625** (Account failed to log on).
- You can refine the query directly:
  ```splunk
  index="endpoint" tinashe EventCode=4625
  ```
- Examine the **timestamps**, and you'll notice multiple failed attempts occurring almost simultaneously. This pattern is expected due to brute force attack attempts.

### 2. Querying Successful Login Attempts
```splunk
index="endpoint" tinashe EventCode=4624
```
- This will display **successful login events**.
- Check the **time** to correlate with the failed attempts.
- Expand the event details to view **attacker information**, including:
  - **Attacker’s username**
  - **IP address**
  - **Login method used**

By analyzing these logs, you can determine when the attack was successful and gather forensic evidence of the attacker's actions.
