# 🦟 Mosquitto MQTT Broker Setup Guide

Complete guide for installing, configuring, and managing Mosquitto MQTT broker for FXP20 Key Injector integration.

---

## 🎯 Overview

**Eclipse Mosquitto** is an open-source MQTT broker that provides a lightweight, reliable messaging platform for FXP20 Key Injector MQTT integration. This guide covers:

- **📥 Installation**: Windows, Linux, and Docker setup
- **⚙️ Configuration**: Security, authentication, and topics
- **🔐 Security**: User management and access control
- **📊 Management**: Monitoring and maintenance
- **🧪 Testing**: Verification and troubleshooting

---

## 📥 Installation Methods

### Option 1: Windows Installation (Recommended for Desktop)

#### Download and Install
1. **📥 Visit** [Mosquitto Downloads](https://mosquitto.org/download/)
2. **💻 Download** Windows installer (mosquitto-x.x.x-install-windows-x64.exe)
3. **▶️ Run** installer as Administrator
4. **✅ Accept** license agreement
5. **📂 Choose** installation directory (default: `C:\Program Files\mosquitto`)
6. **🔧 Select** components (install all recommended components)
7. **✅ Complete** installation

#### Post-Installation Setup
1. **📂 Navigate** to installation directory
2. **📝 Create** configuration file
3. **🔧 Configure** Windows service
4. **▶️ Start** Mosquitto service

```batch
:: Navigate to installation directory
cd "C:\Program Files\mosquitto"

:: Create basic configuration
copy mosquitto.conf.example mosquitto.conf

:: Install as Windows service
mosquitto install

:: Start service
net start mosquitto
```

### Option 2: Docker Installation (Recommended for Servers)

#### Docker Compose Setup
Create `docker-compose.yml`:

```yaml
version: '3.8'
services:
  mosquitto:
    image: eclipse-mosquitto:latest
    container_name: mosquitto-broker
    hostname: mosquitto
    ports:
      - "1883:1883"      # MQTT
      - "9001:9001"      # WebSocket (optional)
    volumes:
      - ./config:/mosquitto/config
      - ./data:/mosquitto/data
      - ./logs:/mosquitto/log
    environment:
      - TZ=America/New_York
    restart: unless-stopped
    user: "1000:1000"    # Match your user ID
```

#### Directory Structure
```
mosquitto/
├── docker-compose.yml
├── config/
│   ├── mosquitto.conf
│   └── passwd
├── data/
└── logs/
```

#### Start Docker Container
```bash
# Create directories
mkdir -p config data logs

# Start container
docker-compose up -d

# View logs
docker-compose logs -f mosquitto
```

### Option 3: Linux Installation

#### Ubuntu/Debian
```bash
# Update package list
sudo apt update

# Install Mosquitto broker and client tools
sudo apt install mosquitto mosquitto-clients

# Start and enable service
sudo systemctl start mosquitto
sudo systemctl enable mosquitto

# Check status
sudo systemctl status mosquitto
```

#### CentOS/RHEL
```bash
# Install EPEL repository
sudo yum install epel-release

# Install Mosquitto
sudo yum install mosquitto mosquitto-clients

# Start and enable service
sudo systemctl start mosquitto
sudo systemctl enable mosquitto
```

---

## ⚙️ Basic Configuration

### Configuration File Location
- **Windows**: `C:\Program Files\mosquitto\mosquitto.conf`
- **Linux**: `/etc/mosquitto/mosquitto.conf`
- **Docker**: `./config/mosquitto.conf`

### Minimal Configuration
Create or edit `mosquitto.conf`:

```conf
# Basic Mosquitto Configuration

# Network Settings
listener 1883
bind_address 0.0.0.0

# Security Settings
allow_anonymous false
password_file /mosquitto/config/passwd

# Logging
log_dest file /mosquitto/log/mosquitto.log
log_type error
log_type warning
log_type notice
log_type information
log_timestamp true

# Persistence
persistence true
persistence_location /mosquitto/data/

# Connection Settings
max_connections 100
keepalive_interval 60
```

### Advanced Configuration
```conf
# Advanced Mosquitto Configuration

# Multiple Listeners
listener 1883 0.0.0.0
protocol mqtt

listener 9001 0.0.0.0
protocol websockets

# TLS/SSL Configuration (Optional)
#listener 8883
#certfile /mosquitto/config/server.crt
#keyfile /mosquitto/config/server.key
#cafile /mosquitto/config/ca.crt
#require_certificate true

# Access Control
allow_anonymous false
password_file /mosquitto/config/passwd
acl_file /mosquitto/config/acl

# Logging Configuration
log_dest file /mosquitto/log/mosquitto.log
log_dest stdout
log_type debug
log_type error
log_type warning
log_type notice
log_type information
log_type subscribe
log_type unsubscribe
log_type websockets
log_type none
log_timestamp true

# Performance Settings
max_connections 1000
max_keepalive 65535
max_packet_size 1048576
message_size_limit 1048576

# Persistence Settings
persistence true
persistence_location /mosquitto/data/
persistence_file mosquitto.db
autosave_interval 1800
autosave_on_changes false

# Queue Settings
max_queued_messages 1000
max_inflight_messages 100
upgrade_outgoing_qos false
```

---

## 🔐 User Management and Security

### Creating User Accounts

#### Method 1: Command Line (Linux/Docker)
```bash
# Create password file with first user
mosquitto_passwd -c /mosquitto/config/passwd admin

# Add additional users
mosquitto_passwd /mosquitto/config/passwd fxp20_user
mosquitto_passwd /mosquitto/config/passwd client_user

# Update user password
mosquitto_passwd /mosquitto/config/passwd fxp20_user

# Delete user
mosquitto_passwd -D /mosquitto/config/passwd old_user
```

#### Method 2: Windows
```batch
:: Navigate to Mosquitto directory
cd "C:\Program Files\mosquitto"

:: Create password file
mosquitto_passwd.exe -c passwd admin

:: Add users
mosquitto_passwd.exe passwd fxp20_user
mosquitto_passwd.exe passwd client_user
```

#### Method 3: Docker Container
```bash
# Enter running container
docker exec -it mosquitto-broker sh

# Create/manage users
mosquitto_passwd -c /mosquitto/config/passwd admin
mosquitto_passwd /mosquitto/config/passwd fxp20_user

# Exit container
exit
```

### Access Control Lists (ACL)

Create `acl` file for topic-level permissions:

```conf
# ACL Configuration File

# Admin user - full access
user admin
topic readwrite #

# FXP20 devices - specific topics only
user fxp20_user
topic write fxp20/+/data
topic write fxp20/+/status
topic read fxp20/+/control
topic read fxp20/+/config

# Client applications - read data, write control
user client_user
topic read fxp20/+/data
topic read fxp20/+/status
topic write fxp20/+/control

# Anonymous users - denied (if allow_anonymous true)
pattern read $SYS/broker/load/#
```

### ACL Pattern Examples
```conf
# Pattern-based access control

# User-specific topics
pattern readwrite clients/%u/#

# Device-specific topics  
pattern write devices/%c/data
pattern read devices/%c/control

# Hierarchical permissions
topic read warehouse/floor1/#
topic write warehouse/floor1/reader001/#

# System topics (read-only)
pattern read $SYS/broker/clients/+/connected
pattern read $SYS/broker/load/+
```

---

## 🚀 Service Management

### Windows Service Control

#### Service Management
```batch
:: Start Mosquitto service
net start mosquitto

:: Stop Mosquitto service  
net stop mosquitto

:: Restart Mosquitto service
net stop mosquitto && net start mosquitto

:: Check service status
sc query mosquitto

:: Configure service startup
sc config mosquitto start= auto
```

#### Service Troubleshooting
```batch
:: Install service manually
mosquitto install

:: Remove service
mosquitto uninstall

:: Run in console mode for debugging
mosquitto -c mosquitto.conf -v
```

### Linux Service Control

#### SystemD Management
```bash
# Start service
sudo systemctl start mosquitto

# Stop service
sudo systemctl stop mosquitto

# Restart service
sudo systemctl restart mosquitto

# Enable auto-start
sudo systemctl enable mosquitto

# Check status
sudo systemctl status mosquitto

# View logs
journalctl -u mosquitto -f
```

### Docker Container Management

#### Container Operations
```bash
# Start container
docker-compose up -d mosquitto

# Stop container
docker-compose stop mosquitto

# Restart container
docker-compose restart mosquitto

# View logs
docker-compose logs -f mosquitto

# Check container status
docker-compose ps

# Update configuration and restart
docker-compose restart mosquitto
```

---

## 🧪 Testing and Verification

### Command Line Testing

#### Using Mosquitto Client Tools
```bash
# Subscribe to test topic (Terminal 1)
mosquitto_sub -h localhost -p 1883 -u admin -P password -t "test/topic"

# Publish test message (Terminal 2)  
mosquitto_pub -h localhost -p 1883 -u admin -P password -t "test/topic" -m "Hello World"

# Subscribe to FXP20 data topic
mosquitto_sub -h localhost -p 1883 -u client_user -P password -t "fxp20/+/data"

# Send control command to FXP20
mosquitto_pub -h localhost -p 1883 -u client_user -P password -t "fxp20/reader1/control" -m "Connect"
```

#### Testing FXP20 Integration
```bash
# Monitor FXP20 data
mosquitto_sub -h localhost -p 1883 -u client_user -P password -t "fxp20/data" -v

# Send commands to FXP20
mosquitto_pub -h localhost -p 1883 -u client_user -P password -t "fxp20/control" -m "StartReading"
mosquitto_pub -h localhost -p 1883 -u client_user -P password -t "fxp20/control" -m "StopReading"
```

### FXP20 Key Injector Configuration

#### MQTT Settings for Mosquitto
```xml
<?xml version="1.0" encoding="utf-8"?>
<FXP20KeyInjectorConfig>
  <!-- Mosquitto Connection -->
  <Protocol>MQTT</Protocol>
  <MQTTServer>localhost</MQTTServer>              <!-- or server IP -->
  <MQTTPort>1883</MQTTPort>
  <MQTTUser>fxp20_user</MQTTUser>                 <!-- Created above -->
  <MQTTPassword>your_secure_password</MQTTPassword>
  
  <!-- Topics -->
  <MQTTSendTopic>fxp20/data</MQTTSendTopic>
  <MQTTControlTopic>fxp20/control</MQTTControlTopic>
  
  <!-- Connection Settings -->
  <MQTTKeepAlive>60</MQTTKeepAlive>
  <MQTTReconnect>true</MQTTReconnect>
  <MQTTQOS>1</MQTTQOS>
  <MQTTTimeout>30000</MQTTTimeout>
</FXP20KeyInjectorConfig>
```

---

## 📊 Monitoring and Logging

### Log File Analysis

#### Log Locations
- **Windows**: `C:\Program Files\mosquitto\mosquitto.log`
- **Linux**: `/var/log/mosquitto/mosquitto.log`
- **Docker**: `./logs/mosquitto.log`

#### Important Log Messages
```log
# Successful connection
1234567890: New connection from 192.168.1.100 on port 1883.
1234567890: New client connected from 192.168.1.100 as fxp20_reader (p2, c1, k60).

# Authentication events
1234567890: Client fxp20_reader disconnected.

# Subscription events
1234567890: fxp20_reader 1 fxp20/control

# Message publishing
1234567890: Received PUBLISH from fxp20_reader (d0, q1, r0, m1, 'fxp20/data', ... (24 bytes))
```

### System Monitoring

#### Broker Statistics
Access system topics for monitoring:
```bash
# Connection count
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/clients/connected'

# Message statistics  
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/messages/received'
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/messages/sent'

# Load statistics
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/load/+' 

# Subscription count
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/subscriptions/count'
```

#### Performance Monitoring Script
```bash
#!/bin/bash
# monitor_mosquitto.sh

echo "=== Mosquitto Broker Status ==="
echo "Connected Clients:"
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/clients/connected' -C 1

echo "Messages Received:"
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/messages/received' -C 1

echo "Memory Usage:"
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/heap/current' -C 1

echo "Uptime:"
mosquitto_sub -h localhost -u admin -P password -t '$SYS/broker/uptime' -C 1
```

---

## 🔧 Troubleshooting

### Common Issues and Solutions

#### Connection Refused
**Symptoms**: Client cannot connect to broker
```bash
# Check if broker is running
ps aux | grep mosquitto          # Linux
netstat -an | find "1883"        # Windows

# Test connectivity
telnet localhost 1883

# Check firewall
sudo ufw allow 1883               # Ubuntu
netsh advfirewall firewall add rule name="Mosquitto" dir=in action=allow protocol=TCP localport=1883  # Windows
```

#### Authentication Failed
**Symptoms**: Client connects but authentication fails
```bash
# Verify user exists
cat /mosquitto/config/passwd

# Test credentials
mosquitto_pub -h localhost -u testuser -P testpass -t test -m "hello"

# Check ACL permissions
cat /mosquitto/config/acl
```

#### Message Not Delivered
**Symptoms**: Messages published but not received
```bash
# Check topic permissions
mosquitto_sub -h localhost -u admin -P password -t 'test' -v

# Verify QoS settings
mosquitto_pub -h localhost -u admin -P password -t 'test' -m "hello" -q 1

# Check retained messages
mosquitto_pub -h localhost -u admin -P password -t 'test' -m "hello" -r
```

### Docker-Specific Issues

#### Permission Problems
```bash
# Fix volume permissions
sudo chown -R 1883:1883 ./config ./data ./logs

# Or run as root (less secure)
docker-compose run --user root mosquitto
```

#### Configuration Not Loading
```bash
# Check mount points
docker exec mosquitto-broker ls -la /mosquitto/config/

# Validate configuration
docker exec mosquitto-broker mosquitto -c /mosquitto/config/mosquitto.conf -t
```

### Performance Tuning

#### High Load Configuration
```conf
# High-performance settings
max_connections 10000
max_inflight_messages 500
max_queued_messages 10000
message_size_limit 10485760

# Disable unnecessary logging
log_type error
log_type warning
```

#### Memory Optimization
```conf
# Memory-conscious settings
persistence false
max_queued_messages 100
max_inflight_messages 20
autosave_interval 60
```

---

## 🔒 Security Best Practices

### Network Security
```conf
# Bind to specific interface
bind_address 192.168.1.100

# Disable anonymous access
allow_anonymous false

# Enable access control
password_file /mosquitto/config/passwd
acl_file /mosquitto/config/acl
```

### TLS/SSL Configuration
```conf
# TLS listener
listener 8883
certfile /mosquitto/config/server.crt
keyfile /mosquitto/config/server.key
cafile /mosquitto/config/ca.crt
require_certificate false
use_identity_as_username false
```

### Firewall Configuration
```bash
# Linux (ufw)
sudo ufw allow from 192.168.1.0/24 to any port 1883

# Linux (iptables)
iptables -A INPUT -p tcp --dport 1883 -s 192.168.1.0/24 -j ACCEPT

# Windows (netsh)
netsh advfirewall firewall add rule name="Mosquitto MQTT" dir=in action=allow protocol=TCP localport=1883 remoteip=192.168.1.0/24
```

---

## 📚 Integration Examples

### Python Client Example
```python
import paho.mqtt.client as mqtt

def on_connect(client, userdata, flags, rc):
    print(f"Connected with result code {rc}")
    client.subscribe("fxp20/data")

def on_message(client, userdata, msg):
    print(f"Topic: {msg.topic}, Message: {msg.payload.decode()}")

client = mqtt.Client()
client.username_pw_set("client_user", "password")
client.on_connect = on_connect
client.on_message = on_message

client.connect("localhost", 1883, 60)
client.loop_forever()
```

### Node.js Client Example
```javascript
const mqtt = require('mqtt');

const client = mqtt.connect('mqtt://localhost:1883', {
    username: 'client_user',
    password: 'password'
});

client.on('connect', () => {
    console.log('Connected to Mosquitto');
    client.subscribe('fxp20/data');
});

client.on('message', (topic, message) => {
    console.log(`Received: ${topic} - ${message.toString()}`);
});

// Send control command
client.publish('fxp20/control', 'StartReading');
```

### C# Client Example
```csharp
using MQTTnet;
using MQTTnet.Client;

var factory = new MqttFactory();
var client = factory.CreateMqttClient();

var options = new MqttClientOptionsBuilder()
    .WithTcpServer("localhost", 1883)
    .WithCredentials("client_user", "password")
    .Build();

client.UseApplicationMessageReceivedHandler(e => {
    Console.WriteLine($"Topic: {e.ApplicationMessage.Topic}");
    Console.WriteLine($"Payload: {Encoding.UTF8.GetString(e.ApplicationMessage.Payload)}");
});

await client.ConnectAsync(options);
await client.SubscribeAsync("fxp20/data");

Console.WriteLine("Connected and subscribed. Press any key to exit.");
Console.ReadKey();
```

---

## 📞 Related Resources

- **[MQTT Integration Guide](MQTT.md)** - FXP20 MQTT configuration
- **[Configuration Reference](Config-Reference.md)** - MQTT parameters
- **[Troubleshooting Guide](Troubleshooting.md)** - MQTT troubleshooting
- **[Official Mosquitto Documentation](https://mosquitto.org/documentation/)**

---

*Mosquitto broker ready for FXP20 integration? Check the [MQTT Integration Guide](MQTT.md) for FXP20 configuration or return to [Home](Home.md).*