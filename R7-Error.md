# Rapid7 Insight Agent Troubleshooting

## Location of Log

### Windows
```
C:\Program Files\Rapid7\Insight Agent\components\insight_agent\common\config
```

### Mac and Linux
```
/opt/rapid7/ir_agent/components/insight_agent/common/config
```

## Installation and Configuration
- **Installation Guide:** [Rapid7 Insight Agent Installation](https://docs.rapid7.com/insight-agent/install)
- **Configuration:** [Rapid7 Insight Agent Configuration](https://docs.rapid7.com/insight-agent/configure)
- **Troubleshooting:** [Rapid7 Insight Agent Troubleshooting](https://docs.rapid7.com/insight-agent/troubleshoot)

## Agent Log Error (OFFLINE)
```
[WARNING] [agent.agent_socket.HAS.139684169844240] : BeaconThread no servers available yet
[WARNING] [agent.agent_beacon]: Failed to send beacon: No server available
[WARNING] [agent.agent_beacon]: Beacon did not run successfully!
```

**Potential Causes and Solutions**

1. **Network and Server Connectivity**  
   - The agent may fail to beacon if there are no available servers to communicate with.  
   - Ensure the network connection is properly configured.  
   - Verify that the servers listed in the agent's configuration are reachable.  
   - [Network Traffic and Connectivity Requirements](https://docs.rapid7.com/insight-agent/network-traffic-and-connectivity-requirements)

2. **Proxy or Collector Configuration**  
   - If the agent is configured to communicate through a proxy or collector, ensure the proxy configuration is set up correctly.  
   - Allow necessary traffic through the proxy.  
   - [Network Traffic and Connectivity Requirements](https://docs.rapid7.com/insight-agent/network-traffic-and-connectivity-requirements)

3. **SSL/Deep Packet Inspection**  
   - SSL or deep packet inspection can interfere with the agent’s communication.  
   - Ensure these are not blocking the agent’s traffic.

4. **Agent Service Status**  
   - Ensure the agent service has not stopped or was installed correctly.  
   - Restarting the agent service may resolve the issue if it was in a stopped state.

5. **Endpoint Protection or Interference from Security Software**  
   - Endpoint protection software might block the agent from communicating with necessary URLs.  
   - Whitelist the entire agent directory and subdirectories.  
   - Certain endpoint protection and anti-virus software might prevent the agent from functioning properly.  
   - [EPP Software Requirements](https://docs.rapid7.com/insight-agent/epp-software-requirements)

## 🕵️‍♂️ If Agent is Still Not Visible

1. ✅ **Check Diagnostic Status**
   - Run the diagnostic tool from the agent’s install directory:
     ```bash
     ./ir_agent -diagnose
     ```
   - Ensure the output status is **PASSED**.

2. 🔄 **If PASSED but Still Not Visible**
   - Restart the Rapid7 service:
     ```bash
     sudo systemctl restart ir_agent
     ```
     *(Command may vary depending on system setup)*

3. ♻️ **If Issue Persists**
   - Retry by reinstalling the Rapid7 agent.

4. 🛠️ **After Second Reinstall and Still Not Viewable**
   - If diagnostics still show **PASSED** but the agent is not visible:
     - **Raise the issue to Rapid7 Support** with all the collected information.

# 🕵️‍♂️ How to get AgentID in the machine if still not visible on dashboard

Follow these steps to investigate when a Rapid7 Insight Agent is not appearing on the Insight Platform dashboard.
---
## 1️⃣ Check the Host in Insight Platform
Use a query to look up the agent by hostname or IP address:
```sql
agent.hostname = "HOSTNAME"
OR
agent.primaryIpAddress = "##.##.##.##"
```
## 2️⃣ If Not Found, Check the Local Agent Logs
Check the log file on the machine:
``` 
cat /opt/rapid7/ir_agent/components/insight_agent/common/agent.log
```
Look for any connection issues, errors, or anomalies.
## 3️⃣ Locate the Agent UID in Logs
Search in the agent.log file for the agent’s unique identifier (UID). Look for a line similar to:
``` 
Agent Info -- ID: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
- [INFO] [agent.agent_beacon]: Agent Info -- ID: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
🐧 Linux (with grep, head, tail)
```
grep '\[INFO\] \[agent.agent_beacon\]: Agent Info -- ID' agent.log
```
```
grep 'Agent Info -- ID' agent.log | head -n 5
```
```
grep 'Agent Info -- ID' agent.log | tail -n 5
```
🪟 Windows (with CMD findstr, Powershell Select-String)
```
findstr "Agent Info -- ID" filename.log
```
```
findstr /I "agent info -- id" agent.log
```
```
Select-String -Path "agent.log" -Pattern "\[INFO\] \[agent\.agent_beacon\]: Agent Info -- ID"
```
Copy the UID.
## 4️⃣ Search by Agent ID in the Platform
Back in the Insight Platform, run a query to search for the agent by its ID:
``` 
agent.agentId = "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

