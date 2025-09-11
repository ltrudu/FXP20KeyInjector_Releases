# 🌐 MQTT Integration Guide

Complete guide for setting up and using MQTT messaging with FXP20 Key Injector for enterprise integration.

---

## 📋 MQTT Overview

**MQTT (Message Queuing Telemetry Transport)** is a lightweight messaging protocol designed for IoT and enterprise applications. FXP20 Key Injector supports MQTT for:

- 📡 **Data Distribution**: Send tag data to multiple applications simultaneously
- 🎛️ **Remote Control**: Control the FXP20 from external applications
- 🏢 **Enterprise Integration**: Integrate with existing MQTT infrastructure
- 🔗 **Scalable Architecture**: Support multiple readers and applications

---

## 🏗️ MQTT Architecture

### System Components

```
┌─────────────────────┐    MQTT     ┌─────────────────┐    MQTT     ┌─────────────────────┐
│                     │ ◄────────── │                 │ ──────────► │                     │
│  Target             │  EPC Data   │  MQTT Broker    │  Control    │  Control            │
│  Applications       │   Topic     │  (Mosquitto)    │  Commands   │  Applications       │
│                     │             │                 │   Topic     │                     │
└─────────────────────┘             └─────────────────┘             └─────────────────────┘
                                            │
                                            │ Connect
                                            ▼
                                    ┌─────────────────┐
                                    │                 │
                                    │  FXP20 Key      │
                                    │  Injector       │
                                    │                 │
                                    └─────────────────┘
                                            │
                                            │ EPC Read
                                            ▼
                                    ┌─────────────────┐
                                    │     FXP20       │
                                    │   RFID Reader   │
                                    └─────────────────┘
```

### Data Flow
1. **🏷️ Tag Reading**: FXP20 reads RFID tags
2. **📤 Data Publishing**: FXP20 Key Injector publishes to data topic
3. **📡 Broker Distribution**: MQTT broker distributes to all subscribers
4. **📥 Application Consumption**: Target applications receive tag data
5. **🎛️ Remote Control**: Applications can send control commands

---

## ⚙️ MQTT Configuration

### Basic MQTT Settings
Configure these settings in Config.xml:

```xml
<Protocol>MQTT</Protocol>
<MQTTServer>127.0.0.1</MQTTServer>
<MQTTPort>1883</MQTTPort>
<MQTTUser>user</MQTTUser>
<MQTTPassword>password</MQTTPassword>
<MQTTSendTopic>fxp20/data</MQTTSendTopic>
<MQTTControlTopic>fxp20/control</MQTTControlTopic>
```

### Configuration Parameters

#### Connection Settings
- 🌐 **MQTTServer**: IP address or hostname of MQTT broker
  - `127.0.0.1` (localhost)
  - `192.168.1.100` (network IP)
  - `mqtt.example.com` (hostname)
- 🔌 **MQTTPort**: Broker connection port (default: 1883)
- 👤 **MQTTUser**: Authentication username
- 🔐 **MQTTPassword**: Authentication password (stored in plain text)

#### Topic Configuration
- 📤 **MQTTSendTopic**: Topic for publishing tag data
  - Example: `fxp20/data`, `warehouse/reader1/tags`
- 📥 **MQTTControlTopic**: Topic for receiving control commands
  - Example: `fxp20/control`, `warehouse/reader1/commands`

### Security Considerations
⚠️ **Important**: 
- Passwords are stored in plain text in Config.xml
- Use strong, unique passwords for MQTT authentication
- Consider file system permissions to protect Config.xml
- Use strong passwords and secure your MQTT broker

---

## 🔧 MQTT Broker Setup

### Option 1: Mosquitto MQTT Broker (Recommended)

#### Installation
1. **📥 Download**: Get Mosquitto from [mosquitto.org](https://mosquitto.org/download/)
2. **💻 Install**: Run installer with default settings
3. **🔧 Configure**: Set up authentication and topics
4. **▶️ Start**: Launch broker service

#### Basic Configuration
Create `mosquitto.conf`:
```conf
# Basic Configuration
listener 1883
allow_anonymous false
password_file passwd

# Logging
log_dest file mosquitto.log
log_type error
log_type warning
log_type notice
log_type information
```

#### User Management
Create user accounts:
```bash
# Create password file with user 'user' and password 'sko'
mosquitto_passwd -c passwd user
```

#### Running Mosquitto
```bash
# Start broker with configuration
mosquitto -c mosquitto.conf -v
```

### Option 2: Cloud MQTT Services

#### AWS IoT Core
- 🌐 **Endpoint**: Configure AWS IoT endpoint
- 🔐 **Authentication**: Use IoT certificates or IAM
- 📊 **Integration**: Connect to AWS services

#### Azure IoT Hub
- 🔗 **Connection**: Use IoT Hub connection string
- 🛡️ **Security**: Device authentication and encryption
- 📈 **Scaling**: Enterprise-grade scalability

#### HiveMQ Cloud
- ☁️ **Managed Service**: Fully managed MQTT broker
- 🔒 **Security**: TLS encryption and authentication
- 📊 **Monitoring**: Built-in analytics and monitoring

### Option 3: Docker Mosquitto
```dockerfile
# Docker Compose Example
version: '3.8'
services:
  mosquitto:
    image: eclipse-mosquitto:latest
    container_name: mosquitto
    ports:
      - "1883:1883"
      - "9001:9001"
    volumes:
      - ./mosquitto.conf:/mosquitto/config/mosquitto.conf
      - ./passwd:/mosquitto/config/passwd
    restart: unless-stopped
```

---

## 📡 MQTT Messaging

### Data Publishing

#### EPC Data Format
When tags are read, FXP20 Key Injector publishes the raw EPC data directly as the message payload:

```text
E20000123456789012345678
```

**Message Content:**
- 🏷️ **Raw EPC Data**: The EPC tag identifier as read from device, sent directly as payload
- 📊 **Simple Format**: Plain text EPC data, no JSON wrapper or metadata
- ⏱️ **Real-time**: Published immediately when tag is read

#### Topic Structure Examples
- **Basic**: `fxp20/data`
- **Hierarchical**: `warehouse/floor1/reader001/data`
- **Device-Specific**: `devices/fxp20-{serial}/tags`

### Control Commands

#### Available Commands
FXP20 Key Injector listens on the control topic for these commands:

##### Connection Control
- **`Connect`**: Connect to FXP20 device (equivalent to GUI Connect button)
- **`Disconnect`**: Disconnect from FXP20 device

##### Reading Control  
- **`StartReading`**: Begin tag reading (requires connected device)
- **`StopReading`**: Stop tag reading

##### Audio Control
- **`Beep`**: Trigger device beep using configured settings
- **`UnBeep`**: Force stop any ongoing beep

#### Command Examples
```bash
# Using mosquitto_pub to send commands
mosquitto_pub -h localhost -p 1883 -u user -P password -t "fxp20/control" -m "Connect"
mosquitto_pub -h localhost -p 1883 -u user -P password -t "fxp20/control" -m "StartReading"
mosquitto_pub -h localhost -p 1883 -u user -P password -t "fxp20/control" -m "StopReading"
```

---

## 💻 Client Application Examples

### Python MQTT Client
```python
import paho.mqtt.client as mqtt
import json

def on_connect(client, userdata, flags, rc):
    print(f"Connected with result code {rc}")
    # Subscribe to tag data
    client.subscribe("fxp20/data")

def on_message(client, userdata, msg):
    tag_data = msg.payload.decode()
    print(f"Received tag: {tag_data}")
    # Process tag data here

# Configure client
client = mqtt.Client()
client.username_pw_set("user", "password")
client.on_connect = on_connect
client.on_message = on_message

# Connect and start listening
client.connect("localhost", 1883, 60)
client.loop_forever()
```

### JavaScript MQTT Client
```javascript
const mqtt = require('mqtt');
const client = mqtt.connect('mqtt://user:password@localhost:1883');

client.on('connect', function () {
  console.log('Connected to MQTT broker');
  client.subscribe('fxp20/data');
});

client.on('message', function (topic, message) {
  if (topic === 'fxp20/data') {
    console.log('Tag data:', message.toString());
    // Process tag data here
  }
});

// Send control commands
function sendCommand(command) {
  client.publish('fxp20/control', command);
}

// Examples
sendCommand('Connect');
sendCommand('StartReading');
```

### C# MQTT Client
```csharp
using MQTTnet;
using MQTTnet.Client;

var factory = new MqttFactory();
var client = factory.CreateMqttClient();

var options = new MqttClientOptionsBuilder()
    .WithTcpServer("localhost", 1883)
    .WithCredentials("user", "password")
    .Build();

client.UseConnectedHandler(async e => {
    Console.WriteLine("Connected to MQTT broker");
    await client.SubscribeAsync("fxp20/data");
});

client.UseApplicationMessageReceivedHandler(e => {
    var topic = e.ApplicationMessage.Topic;
    var payload = Encoding.UTF8.GetString(e.ApplicationMessage.Payload);
    
    if (topic == "fxp20/data") {
        Console.WriteLine($"Tag data: {payload}");
        // Process tag data here
    }
});

await client.ConnectAsync(options);
```

---

## 🛠️ MQTT Troubleshooting

### Connection Issues

#### Broker Connection Failed
- **🔍 Check Network**: Verify broker IP/hostname and port
- **🔐 Authentication**: Confirm username/password are correct
- **🔥 Firewall**: Check firewall settings on broker machine
- **▶️ Broker Status**: Ensure MQTT broker is running

#### Authentication Errors
- **👤 User Setup**: Verify user exists in broker configuration
- **🔐 Password**: Check password matches broker configuration
- **⚙️ Broker Config**: Confirm authentication is properly enabled

### Data Flow Issues

#### No Data Received
- **📡 Subscription**: Verify client subscribed to correct topic
- **🎯 Topic Match**: Check topic names match exactly (case-sensitive)
- **🔗 FXP20 Connection**: Ensure FXP20 Key Injector is connected
- **▶️ Reading Status**: Confirm tag reading is active

#### Control Commands Not Working
- **📥 Topic Listening**: Verify FXP20 Key Injector registered to control topic
- **📝 Command Format**: Check command text matches expected format
- **🔗 Connection**: Ensure MQTT connection is active
- **📊 Logging**: Enable broker logging to trace message flow

### Performance Issues

#### High Latency
- **🌐 Network**: Check network latency to broker
- **⚙️ Broker Load**: Monitor broker resource usage
- **📊 QoS Settings**: Consider adjusting Quality of Service levels
- **🔧 Buffer Settings**: Tune broker and client buffer sizes

#### Message Loss
- **💾 QoS Levels**: Use appropriate QoS for reliability requirements
- **📡 Persistence**: Configure persistent sessions if needed
- **🔄 Retry Logic**: Implement client-side retry mechanisms
- **📊 Monitoring**: Monitor broker message statistics

---

## 📊 MQTT Best Practices

### Topic Design
- **🏗️ Hierarchical Structure**: Use logical topic hierarchies
- **📝 Descriptive Names**: Choose clear, meaningful topic names
- **🔧 Flexibility**: Design for future expansion
- **📊 Standards**: Follow organizational naming conventions

### Security
- **🔐 Authentication**: Always use username/password authentication
- **🛡️ Encryption**: Use TLS/SSL for sensitive environments
- **🚪 Access Control**: Implement topic-based access controls
- **🔄 Credential Rotation**: Regularly update MQTT credentials

### Performance
- **📊 QoS Selection**: Choose appropriate Quality of Service levels
- **💾 Retain Messages**: Use retain flag judiciously
- **🔄 Keep-Alive**: Configure appropriate keep-alive intervals
- **📈 Monitoring**: Implement broker and client monitoring

### Integration
- **🔌 Connection Pooling**: Reuse connections where possible
- **🎯 Topic Filtering**: Use efficient subscription patterns
- **📊 Message Batching**: Batch messages for high-volume scenarios
- **⚡ Async Processing**: Use asynchronous message processing

---

## 🔧 Advanced MQTT Features

### Quality of Service (QoS)
- **QoS 0**: At most once delivery (fire and forget)
- **QoS 1**: At least once delivery (acknowledged delivery)
- **QoS 2**: Exactly once delivery (assured delivery)

### Retained Messages
- **💾 Last Known Value**: Broker stores last message on topic
- **🆕 New Subscribers**: Immediately receive retained message
- **🏷️ Status Updates**: Useful for device status information

### Persistent Sessions  
- **📊 Session Storage**: Broker remembers client subscriptions
- **🔄 Reconnection**: Automatic subscription restoration
- **📧 Offline Messages**: Queue messages for offline clients

### Last Will and Testament
- **💔 Disconnect Detection**: Broker publishes message when client disconnects unexpectedly
- **🚨 Status Notification**: Notify other clients of device failures
- **🔄 Recovery Actions**: Trigger recovery procedures automatically

---

## 🔗 Related Topics

- **[Configuration Guide](Configuration.md)** - Detailed Config.xml settings
- **[Setup Guide](Setup.md)** - Basic setup and connection
- **[Troubleshooting](Troubleshooting.md)** - MQTT-specific troubleshooting
- **[User Interface Guide](User-Interface.md)** - GUI protocol selection

---

## 📞 MQTT Resources

### Documentation
- **[MQTT.org](https://mqtt.org/)** - Official MQTT specification
- **[Mosquitto Documentation](https://mosquitto.org/documentation/)** - Mosquitto broker docs
- **[HiveMQ Learning Center](https://www.hivemq.com/mqtt-essentials/)** - MQTT tutorials

### Tools
- **[MQTT Explorer](https://mqtt-explorer.com/)** - GUI MQTT client
- **[MQTT Lens](https://chrome.google.com/webstore/detail/mqttlens/hemojaaeigabkbcookmlgmdigohjobjm)** - Chrome extension
- **[Mosquitto Clients](https://mosquitto.org/download/)** - Command-line tools

---

*Need MQTT help? Check our [Troubleshooting Guide](Troubleshooting.md) or return to [Home](Home.md).*