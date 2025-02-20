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
