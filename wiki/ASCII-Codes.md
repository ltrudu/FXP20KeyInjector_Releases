# 🔤 ASCII Character Codes Reference

Complete ASCII character reference for keyboard hooks and special character handling in FXP20 Key Injector.

---

## 📋 Overview

This reference provides ASCII character codes for configuring keyboard hooks, special character handling, and data formatting in FXP20 Key Injector. Use these codes when setting up:

- **⌨️ Keyboard Hook Keys**: Custom trigger keys
- **📝 Special Characters**: Control characters in data
- **🔧 Data Formatting**: Custom prefixes, suffixes, and separators
- **🎛️ Function Keys**: F1-F12 key mappings

---

## ⌨️ Standard ASCII Characters (0-127)

### Control Characters (0-31)
| Code | Hex | Key | Description | Usage |
|------|-----|-----|-------------|-------|
| **0** | 0x00 | NUL | Null | String terminator |
| **1** | 0x01 | SOH | Start of Heading | Header marker |
| **2** | 0x02 | STX | Start of Text | Text marker |
| **3** | 0x03 | ETX | End of Text | End marker |
| **4** | 0x04 | EOT | End of Transmission | Transmission end |
| **5** | 0x05 | ENQ | Enquiry | Query character |
| **6** | 0x06 | ACK | Acknowledge | Acknowledgment |
| **7** | 0x07 | BEL | Bell | Beep/Alert |
| **8** | 0x08 | BS | Backspace | ⌫ Backspace |
| **9** | 0x09 | TAB | Horizontal Tab | ⭾ Tab |
| **10** | 0x0A | LF | Line Feed | New line (Unix) |
| **11** | 0x0B | VT | Vertical Tab | Vertical tab |
| **12** | 0x0C | FF | Form Feed | Page break |
| **13** | 0x0D | CR | Carriage Return | Enter/Return |
| **14** | 0x0E | SO | Shift Out | Character set shift |
| **15** | 0x0F | SI | Shift In | Character set shift |
| **27** | 0x1B | ESC | Escape | Escape key |

### Printable Characters (32-126)

#### Space and Punctuation (32-47)
| Code | Hex | Char | Description | Usage in Config |
|------|-----|------|-------------|-----------------|
| **32** | 0x20 | ` ` | Space | Used in data content |
| **33** | 0x21 | `!` | Exclamation | Used in data content |
| **34** | 0x22 | `"` | Quote | Used in data content |
| **35** | 0x23 | `#` | Hash | Used in data content |
| **36** | 0x24 | `$` | Dollar | Used in data content |
| **37** | 0x25 | `%` | Percent | Field placeholder |
| **38** | 0x26 | `&` | Ampersand | Data connector |
| **39** | 0x27 | `'` | Apostrophe | Used in data content |
| **40** | 0x28 | `(` | Left Parenthesis | Data grouping |
| **41** | 0x29 | `)` | Right Parenthesis | Data grouping |
| **42** | 0x2A | `*` | Asterisk | Wildcard |
| **43** | 0x2B | `+` | Plus | Data concatenation |
| **44** | 0x2C | `,` | Comma | Used with `<AddCSVSeparator>true</AddCSVSeparator>` |
| **45** | 0x2D | `-` | Hyphen/Minus | Used in data content |
| **46** | 0x2E | `.` | Period | Used in data content |
| **47** | 0x2F | `/` | Forward Slash | Used in data content |

#### Numbers (48-57)
| Code | Hex | Char | Description |
|------|-----|------|-------------|
| **48** | 0x30 | `0` | Zero |
| **49** | 0x31 | `1` | One |
| **50** | 0x32 | `2` | Two |
| **51** | 0x33 | `3` | Three |
| **52** | 0x34 | `4` | Four |
| **53** | 0x35 | `5` | Five |
| **54** | 0x36 | `6` | Six |
| **55** | 0x37 | `7` | Seven |
| **56** | 0x38 | `8` | Eight |
| **57** | 0x39 | `9` | Nine |

#### Uppercase Letters (65-90)
| Code | Hex | Char | Code | Hex | Char | Code | Hex | Char |
|------|-----|------|------|-----|------|------|-----|------|
| **65** | 0x41 | `A` | **74** | 0x4A | `J` | **83** | 0x53 | `S` |
| **66** | 0x42 | `B` | **75** | 0x4B | `K` | **84** | 0x54 | `T` |
| **67** | 0x43 | `C` | **76** | 0x4C | `L` | **85** | 0x55 | `U` |
| **68** | 0x44 | `D` | **77** | 0x4D | `M` | **86** | 0x56 | `V` |
| **69** | 0x45 | `E` | **78** | 0x4E | `N` | **87** | 0x57 | `W` |
| **70** | 0x46 | `F` | **79** | 0x4F | `O` | **88** | 0x58 | `X` |
| **71** | 0x47 | `G` | **80** | 0x50 | `P` | **89** | 0x59 | `Y` |
| **72** | 0x48 | `H` | **81** | 0x51 | `Q` | **90** | 0x5A | `Z` |
| **73** | 0x49 | `I` | **82** | 0x52 | `R` |

#### Lowercase Letters (97-122)
| Code | Hex | Char | Code | Hex | Char | Code | Hex | Char |
|------|-----|------|------|-----|------|------|-----|------|
| **97** | 0x61 | `a` | **106** | 0x6A | `j` | **115** | 0x73 | `s` |
| **98** | 0x62 | `b` | **107** | 0x6B | `k` | **116** | 0x74 | `t` |
| **99** | 0x63 | `c` | **108** | 0x6C | `l` | **117** | 0x75 | `u` |
| **100** | 0x64 | `d` | **109** | 0x6D | `m` | **118** | 0x76 | `v` |
| **101** | 0x65 | `e` | **110** | 0x6E | `n` | **119** | 0x77 | `w` |
| **102** | 0x66 | `f` | **111** | 0x6F | `o` | **120** | 0x78 | `x` |
| **103** | 0x67 | `g` | **112** | 0x70 | `p` | **121** | 0x79 | `y` |
| **104** | 0x68 | `h` | **113** | 0x71 | `q` | **122** | 0x7A | `z` |
| **105** | 0x69 | `i` | **114** | 0x72 | `r` |

---

## ⌨️ Extended Keys and Function Keys

### Function Keys (F1-F12)
| Key | Virtual Code | Config Usage | Description |
|-----|--------------|--------------|-------------|
| **F1** | 112 | `<HookKeyboardKey>112</HookKeyboardKey>` | Function 1 |
| **F2** | 113 | `<HookKeyboardKey>113</HookKeyboardKey>` | Function 2 |
| **F3** | 114 | `<HookKeyboardKey>114</HookKeyboardKey>` | Function 3 |
| **F4** | 115 | `<HookKeyboardKey>115</HookKeyboardKey>` | Function 4 |
| **F5** | 116 | `<HookKeyboardKey>116</HookKeyboardKey>` | Function 5 |
| **F6** | 117 | `<HookKeyboardKey>117</HookKeyboardKey>` | Function 6 |
| **F7** | 118 | `<HookKeyboardKey>118</HookKeyboardKey>` | Function 7 |
| **F8** | 119 | `<HookKeyboardKey>119</HookKeyboardKey>` | Function 8 |
| **F9** | 120 | `<HookKeyboardKey>120</HookKeyboardKey>` | Function 9 |
| **F10** | 121 | `<HookKeyboardKey>121</HookKeyboardKey>` | Function 10 |
| **F11** | 122 | `<HookKeyboardKey>122</HookKeyboardKey>` | Function 11 |
| **F12** | 123 | `<HookKeyboardKey>123</HookKeyboardKey>` | Function 12 (default) |

### Navigation Keys
| Key | Virtual Code | Config Usage | Description |
|-----|--------------|--------------|-------------|
| **Home** | 36 | `<HookKeyboardKey>36</HookKeyboardKey>` | Home key |
| **End** | 35 | `<HookKeyboardKey>35</HookKeyboardKey>` | End key |
| **PageUp** | 33 | `<HookKeyboardKey>33</HookKeyboardKey>` | Page Up |
| **PageDown** | 34 | `<HookKeyboardKey>34</HookKeyboardKey>` | Page Down |
| **Insert** | 45 | `<HookKeyboardKey>45</HookKeyboardKey>` | Insert key |
| **Delete** | 46 | `<HookKeyboardKey>46</HookKeyboardKey>` | Delete key |

### Arrow Keys
| Key | Virtual Code | Config Usage | Description |
|-----|--------------|--------------|-------------|
| **Up** | 38 | `<HookKeyboardKey>38</HookKeyboardKey>` | Up arrow |
| **Down** | 40 | `<HookKeyboardKey>40</HookKeyboardKey>` | Down arrow |
| **Left** | 37 | `<HookKeyboardKey>37</HookKeyboardKey>` | Left arrow |
| **Right** | 39 | `<HookKeyboardKey>39</HookKeyboardKey>` | Right arrow |

### Modifier Keys
| Key | Virtual Code | Config Usage | Description |
|-----|--------------|--------------|-------------|
| **Space** | 32 | `<HookKeyboardKey>32</HookKeyboardKey>` | Space bar |
| **Enter** | 13 | `<HookKeyboardKey>13</HookKeyboardKey>` | Enter key |
| **Tab** | 9 | `<HookKeyboardKey>9</HookKeyboardKey>` | Tab key |
| **Escape** | 27 | `<HookKeyboardKey>27</HookKeyboardKey>` | Escape key |

**Note**: Modifier keys (Ctrl, Alt, Shift) are not configurable

---

## 🔧 Common Configuration Examples

### Keyboard Hook Configuration
```xml
<!-- Function key triggers (only HookKeyboardKey is configurable) -->
<HookKeyboardToStartReading>true</HookKeyboardToStartReading>
<HookKeyboardKey>112</HookKeyboardKey>             <!-- F1 key code -->
<HookKeyboardReadingDurationInMs>5000</HookKeyboardReadingDurationInMs>

```

### Data Formatting with Special Characters
```xml
<!-- Available formatting options -->
<AddCR>true</AddCR>                               <!-- Carriage return (ASCII 13) -->
<AddLF>false</AddLF>                              <!-- Line feed (ASCII 10) -->
<AddCSVSeparator>true</AddCSVSeparator>           <!-- Add CSV separator -->

```

---

## 📊 Character Encoding and Escape Sequences

### XML Character Entities
When using special characters in Config.xml, use these XML entities:

| Character | ASCII | XML Entity | Usage |
|-----------|-------|------------|-------|
| **<** | 60 | `&lt;` | Less than |
| **>** | 62 | `&gt;` | Greater than |
| **&** | 38 | `&amp;` | Ampersand |
| **"** | 34 | `&quot;` | Double quote |
| **'** | 39 | `&apos;` | Single quote |

### Numeric Character References
Use numeric references for control characters:

| Character | ASCII | Numeric | Usage |
|-----------|-------|---------|-------|
| **Tab** | 9 | `&#9;` | Tab character in data |
| **Line Feed** | 10 | `&#10;` | Used with `<AddLF>true</AddLF>` |
| **Carriage Return** | 13 | `&#13;` | Used with `<AddCR>true</AddCR>` |
| **Escape** | 27 | `&#27;` | Escape character in data |

### Hexadecimal References
Alternative hex format for special characters:

| Character | ASCII | Hex | Usage |
|-----------|-------|-----|-------|
| **Tab** | 9 | `&#x9;` | Tab character in data |
| **Line Feed** | 10 | `&#xA;` | Used with `<AddLF>true</AddLF>` |
| **Carriage Return** | 13 | `&#xD;` | Used with `<AddCR>true</AddCR>` |
| **Space** | 32 | `&#x20;` | Space character in data |

---

## 🎯 Application-Specific Character Handling

### Notepad/Text Editors
```xml
<!-- Optimized for text editors -->
<AddCR>true</AddCR>                               <!-- Enter key -->
<AddLF>false</AddLF>                             <!-- Windows line ending -->
```

### Excel/Spreadsheet Applications
```xml
<!-- Optimized for spreadsheets -->
<AddCSVSeparator>true</AddCSVSeparator>          <!-- Add CSV separator -->
<AddCR>true</AddCR>                              <!-- New row -->
```

### Database Applications
```xml
<!-- Optimized for database entry -->
<AddCR>false</AddCR>                             <!-- No auto-enter -->
```

### Web Forms
```xml
<!-- Optimized for web forms -->
<AddCR>false</AddCR>                             <!-- Manual form submission -->
```

---

## 🧪 Testing Character Configurations

### Character Testing Procedure
1. **⚙️ Configure** character settings in Config.xml
2. **📝 Open** target application (e.g., Notepad)
3. **🧪 Use** "Text to Send" debug feature
4. **📤 Click** "Send Clipboard" or "Send Key Events"
5. **✅ Verify** characters appear correctly
6. **🔧 Adjust** settings as needed

### Test Strings
```xml
<!-- Test different character types -->
<TestString1>ABC123!@#</TestString1>            <!-- Mixed alphanumeric -->
<TestString2>Tab&#9;Separated&#9;Data</TestString2> <!-- Tab-separated -->
<TestString3>Line1&#10;Line2&#10;Line3</TestString3> <!-- Multi-line -->
<TestString4>Quote"Test"Data</TestString4>       <!-- Quoted data -->
```


---

## 🔧 Troubleshooting Character Issues

### Common Character Problems

#### Missing Characters
**Cause**: Target application doesn't support character
**Solution**: Use character replacement or different encoding

#### Wrong Characters Displayed
**Cause**: Character encoding mismatch
**Solution**: Verify ASCII/Unicode settings

#### Control Characters Visible
**Cause**: Application displays control characters literally
**Solution**: Use different control characters or escape sequences

### Character Compatibility Testing

#### Test Matrix
| Character Type | Notepad | Excel | Web Forms | Database |
|---------------|---------|-------|-----------|----------|
| **Letters** | ✅ | ✅ | ✅ | ✅ |
| **Numbers** | ✅ | ✅ | ✅ | ✅ |
| **Spaces** | ✅ | ✅ | ✅ | ✅ |
| **Tabs** | ✅ | ✅ | ⚠️ | ✅ |
| **Enter/CR** | ✅ | ✅ | ⚠️ | ⚠️ |
| **Special Chars** | ✅ | ⚠️ | ⚠️ | ⚠️ |

**Legend:** ✅ Full support, ⚠️ Limited support, ❌ No support

---

## 📚 Related Resources

- **[Config Reference](Config-Reference.md)** - Complete configuration parameters
- **[User Interface Guide](User-Interface.md)** - GUI character configuration
- **[Send Protocols](Send-Protocols.md)** - Character handling by protocol
- **[Troubleshooting Guide](Troubleshooting.md)** - Character-related issues

---

*Need help with specific character configurations? Check the [Config Reference](Config-Reference.md) for detailed parameter documentation or return to [Home](Home.md).*