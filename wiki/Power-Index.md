# ⚡ Transmit Power Index Reference

Complete reference guide for RF transmit power levels on the Zebra FXP20 RFID reader.

---

## 📡 Power Index Overview

The Zebra FXP20 transmit power is controlled by the **TransmitPowerIndex** parameter ranging from **0 to 170**. Each index corresponds to a specific power value as defined by the official Zebra documentation.

**Configuration Element:** `<TransmitPowerIndex>value</TransmitPowerIndex>`

---

## 📊 Official Power Index Table

### Complete Power Reference (0-50)

| Index | Power Value | Index | Power Value | Index | Power Value | Index | Power Value | Index | Power Value |
|-------|-------------|-------|-------------|-------|-------------|-------|-------------|-------|-------------|
| **0** | 1000 | **10** | 1100 | **20** | 1200 | **30** | 1300 | **40** | 1400 |
| **1** | 1010 | **11** | 1110 | **21** | 1210 | **31** | 1310 | **41** | 1410 |
| **2** | 1020 | **12** | 1120 | **22** | 1220 | **32** | 1320 | **42** | 1420 |
| **3** | 1030 | **13** | 1130 | **23** | 1230 | **33** | 1330 | **43** | 1430 |
| **4** | 1040 | **14** | 1140 | **24** | 1240 | **34** | 1340 | **44** | 1440 |
| **5** | 1050 | **15** | 1150 | **25** | 1250 | **35** | 1350 | **45** | 1450 |
| **6** | 1060 | **16** | 1160 | **26** | 1260 | **36** | 1360 | **46** | 1460 |
| **7** | 1070 | **17** | 1170 | **27** | 1270 | **37** | 1370 | **47** | 1470 |
| **8** | 1080 | **18** | 1180 | **28** | 1280 | **38** | 1380 | **48** | 1480 |
| **9** | 1090 | **19** | 1190 | **29** | 1290 | **39** | 1390 | **49** | 1490 |

### Power Reference (50-100)

| Index | Power Value | Index | Power Value | Index | Power Value | Index | Power Value | Index | Power Value |
|-------|-------------|-------|-------------|-------|-------------|-------|-------------|-------|-------------|
| **50** | 1500 | **60** | 1600 | **70** | 1700 | **80** | 1800 | **90** | 1900 |
| **51** | 1510 | **61** | 1610 | **71** | 1710 | **81** | 1810 | **91** | 1910 |
| **52** | 1520 | **62** | 1620 | **72** | 1720 | **82** | 1820 | **92** | 1920 |
| **53** | 1530 | **63** | 1630 | **73** | 1730 | **83** | 1830 | **93** | 1930 |
| **54** | 1540 | **64** | 1640 | **74** | 1740 | **84** | 1840 | **94** | 1940 |
| **55** | 1550 | **65** | 1650 | **75** | 1750 | **85** | 1850 | **95** | 1950 |
| **56** | 1560 | **66** | 1660 | **76** | 1760 | **86** | 1860 | **96** | 1960 |
| **57** | 1570 | **67** | 1670 | **77** | 1770 | **87** | 1870 | **97** | 1970 |
| **58** | 1580 | **68** | 1680 | **78** | 1780 | **88** | 1880 | **98** | 1980 |
| **59** | 1590 | **69** | 1690 | **79** | 1790 | **89** | 1890 | **99** | 1990 |

### Power Reference (100-150)

| Index | Power Value | Index | Power Value | Index | Power Value | Index | Power Value | Index | Power Value |
|-------|-------------|-------|-------------|-------|-------------|-------|-------------|-------|-------------|
| **100** | 2000 | **110** | 2100 | **120** | 2200 | **130** | 2300 | **140** | 2400 |
| **101** | 2010 | **111** | 2110 | **121** | 2210 | **131** | 2310 | **141** | 2410 |
| **102** | 2020 | **112** | 2120 | **122** | 2220 | **132** | 2320 | **142** | 2420 |
| **103** | 2030 | **113** | 2130 | **123** | 2230 | **133** | 2330 | **143** | 2430 |
| **104** | 2040 | **114** | 2140 | **124** | 2240 | **134** | 2340 | **144** | 2440 |
| **105** | 2050 | **115** | 2150 | **125** | 2250 | **135** | 2350 | **145** | 2450 |
| **106** | 2060 | **116** | 2160 | **126** | 2260 | **136** | 2360 | **146** | 2460 |
| **107** | 2070 | **117** | 2170 | **127** | 2270 | **137** | 2370 | **147** | 2470 |
| **108** | 2080 | **118** | 2180 | **128** | 2280 | **138** | 2380 | **148** | 2480 |
| **109** | 2090 | **119** | 2190 | **129** | 2290 | **139** | 2390 | **149** | 2490 |

### Power Reference (150-170)

| Index | Power Value | Index | Power Value |
|-------|-------------|-------|-------------|
| **150** | 2500 | **160** | 2600 |
| **151** | 2510 | **161** | 2610 |
| **152** | 2520 | **162** | 2620 |
| **153** | 2530 | **163** | 2630 |
| **154** | 2540 | **164** | 2640 |
| **155** | 2550 | **165** | 2650 |
| **156** | 2560 | **166** | 2660 |
| **157** | 2570 | **167** | 2670 |
| **158** | 2580 | **168** | 2680 |
| **159** | 2590 | **169** | 2690 |
| | | **170** | 2700 |

**Note:** Power values are official Zebra FXP20 specifications from the FXP20KeyInjector documentation.

---

## 🎯 Power Selection Guide

### Low Power (Index 0-50)

#### Optimal Uses:
- ✅ **Close Range Applications**: Short distance reading
- ✅ **Power Conservation**: Lower power consumption
- ✅ **Interference Reduction**: Minimizing RF noise
- ✅ **Dense Tag Environments**: Many tags close together

#### Configuration Example:
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>25</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S1</SingulationControl_Session>
  </antennaConfig>
</AntennasConfig>
```

### Medium Power (Index 51-120)

#### Optimal Uses:
- ✅ **General Handheld Use**: Standard RFID applications
- ✅ **Mixed Environments**: Varying tag densities
- ✅ **Balanced Performance**: Optimal power usage
- ✅ **Standard Inventory**: Typical warehouse operations

#### Configuration Example:
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>85</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
  </antennaConfig>
</AntennasConfig>
```

### High Power (Index 121-170)

#### Optimal Uses:
- ✅ **Long Range Reading**: Maximum reading distance
- ✅ **Difficult Tags**: Poor quality or damaged tags
- ✅ **Through Materials**: Reading through packaging
- ✅ **Harsh Environments**: Industrial applications

#### Configuration Example:
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>150</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
  </antennaConfig>
</AntennasConfig>
```

---

## 📏 Power Selection Guidelines

### Power Index Selection

#### Based on Application Requirements:
- **Low Power (0-50)**: Close proximity, power conservation
- **Medium Power (51-120)**: Standard handheld applications
- **High Power (121-170)**: Long range, difficult environments

#### Test Configuration:
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>85</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
    <SingulationControl_TagPopulation>30</SingulationControl_TagPopulation>
  </antennaConfig>
</AntennasConfig>
```

**Note:** Actual reading performance depends on tag type, environmental conditions, antenna orientation, and regulatory limits.

---

## 📊 Application-Specific Examples

### Standard Applications

#### General Inventory:
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>100</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
  </antennaConfig>
</AntennasConfig>
```

#### Close Range Reading:
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>25</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S1</SingulationControl_Session>
  </antennaConfig>
</AntennasConfig>
```

#### Maximum Range:
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>170</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
  </antennaConfig>
</AntennasConfig>
```

---

## 🧪 Power Index Testing

### Test Configuration

#### Basic Test Setup:
```xml
<AntennasConfig>
  <antennaConfig>
    <Antenna_ID>1</Antenna_ID>
    <TransmitPowerIndex>85</TransmitPowerIndex>
    <SingulationControl_Session>SESSION_S0</SingulationControl_Session>
  </antennaConfig>
</AntennasConfig>
```

### Common Test Values

| Power Index | Power Value | Application |
|-------------|-------------|-------------|
| 25 | 1250 | Low power testing |
| 85 | 1850 | Medium power testing |
| 150 | 2500 | High power testing |
| 170 | 2700 | Maximum power testing |

---

## 🔧 Troubleshooting Power Settings

### Common Issues

#### Poor Read Performance:
**Solutions**:
1. **⬆️ Increase** TransmitPowerIndex value (try increments of 25)
2. **⚡ Check** FXP20 power connection
3. **📡 Verify** antenna configuration
4. **🧪 Test** with different power index values

#### Inconsistent Reading:
**Solutions**:
1. **⚙️ Adjust** power index for your environment
2. **🔄 Change** session parameters
3. **📡 Check** for RF interference

---

## 📚 Related Resources

- **[Antenna Configuration](Antenna-Configuration.md)** - Complete RF settings guide
- **[Configuration Reference](Config-Reference.md)** - Power-related parameters
- **[Troubleshooting Guide](Troubleshooting.md)** - Power troubleshooting
- **[Setup Guide](Setup.md)** - Initial power configuration

---

*Need help optimizing power settings for your application? Check the [Antenna Configuration](Antenna-Configuration.md) guide or return to [Home](Home.md).*