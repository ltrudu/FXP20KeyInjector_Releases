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
| **32** | 0x20 | ` ` | Space | `<FieldSeparator> </FieldSeparator>` |
| **33** | 0x21 | `!` | Exclamation | `<DataPrefix>!</DataPrefix>` |
| **34** | 0x22 | `"` | Quote | `<CSVQuoteChar>"</CSVQuoteChar>` |
| **35** | 0x23 | `#` | Hash | `<DataPrefix>#</DataPrefix>` |
| **36** | 0x24 | `$` | Dollar | `<DataPrefix>$</DataPrefix>` |
| **37** | 0x25 | `%` | Percent | Field placeholder |
| **38** | 0x26 | `&` | Ampersand | Data connector |
| **39** | 0x27 | `'` | Apostrophe | `<CSVQuoteChar>'</CSVQuoteChar>` |
| **40** | 0x28 | `(` | Left Parenthesis | Data grouping |
| **41** | 0x29 | `)` | Right Parenthesis | Data grouping |
| **42** | 0x2A | `*` | Asterisk | Wildcard |
| **43** | 0x2B | `+` | Plus | Data concatenation |
| **44** | 0x2C | `,` | Comma | `<CSVSeparator>,</CSVSeparator>` |
| **45** | 0x2D | `-` | Hyphen/Minus | `<FieldSeparator>-</FieldSeparator>` |
| **46** | 0x2E | `.` | Period | `<FieldSeparator>.</FieldSeparator>` |
| **47** | 0x2F | `/` | Forward Slash | `<FieldSeparator>/</FieldSeparator>` |

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
| **F1** | VK_F1 | `<StartReadingKey>F1</StartReadingKey>` | Function 1 |
| **F2** | VK_F2 | `<StopReadingKey>F2</StopReadingKey>` | Function 2 |
| **F3** | VK_F3 | `<BeepKey>F3</BeepKey>` | Function 3 |
| **F4** | VK_F4 | `<StartReadingKey>F4</StartReadingKey>` | Function 4 |
| **F5** | VK_F5 | `<StartReadingKey>F5</StartReadingKey>` | Function 5 |
| **F6** | VK_F6 | `<StartReadingKey>F6</StartReadingKey>` | Function 6 |
| **F7** | VK_F7 | `<StartReadingKey>F7</StartReadingKey>` | Function 7 |
| **F8** | VK_F8 | `<StartReadingKey>F8</StartReadingKey>` | Function 8 |
| **F9** | VK_F9 | `<StartReadingKey>F9</StartReadingKey>` | Function 9 |
| **F10** | VK_F10 | `<StartReadingKey>F10</StartReadingKey>` | Function 10 |
| **F11** | VK_F11 | `<StartReadingKey>F11</StartReadingKey>` | Function 11 |
| **F12** | VK_F12 | `<StartReadingKey>F12</StartReadingKey>` | Function 12 |

### Navigation Keys
| Key | Virtual Code | Config Usage | Description |
|-----|--------------|--------------|-------------|
| **Home** | VK_HOME | `<StartReadingKey>Home</StartReadingKey>` | Home key |
| **End** | VK_END | `<StopReadingKey>End</StopReadingKey>` | End key |
| **PageUp** | VK_PRIOR | `<StartReadingKey>PageUp</StartReadingKey>` | Page Up |
| **PageDown** | VK_NEXT | `<StopReadingKey>PageDown</StopReadingKey>` | Page Down |
| **Insert** | VK_INSERT | `<StartReadingKey>Insert</StartReadingKey>` | Insert key |
| **Delete** | VK_DELETE | `<StopReadingKey>Delete</StopReadingKey>` | Delete key |

### Arrow Keys
| Key | Virtual Code | Config Usage | Description |
|-----|--------------|--------------|-------------|
| **Up** | VK_UP | `<StartReadingKey>Up</StartReadingKey>` | Up arrow |
| **Down** | VK_DOWN | `<StartReadingKey>Down</StartReadingKey>` | Down arrow |
| **Left** | VK_LEFT | `<StartReadingKey>Left</StartReadingKey>` | Left arrow |
| **Right** | VK_RIGHT | `<StartReadingKey>Right</StartReadingKey>` | Right arrow |

### Modifier Keys
| Key | Virtual Code | Config Usage | Description |
|-----|--------------|--------------|-------------|
| **Ctrl** | VK_CONTROL | `<RequireCtrl>true</RequireCtrl>` | Control modifier |
| **Alt** | VK_MENU | `<RequireAlt>true</RequireAlt>` | Alt modifier |
| **Shift** | VK_SHIFT | `<RequireShift>true</RequireShift>` | Shift modifier |
| **Space** | VK_SPACE | `<StartReadingKey>Space</StartReadingKey>` | Space bar |
| **Enter** | VK_RETURN | `<StartReadingKey>Enter</StartReadingKey>` | Enter key |
| **Tab** | VK_TAB | `<StartReadingKey>Tab</StartReadingKey>` | Tab key |
| **Escape** | VK_ESCAPE | `<StopReadingKey>Escape</StopReadingKey>` | Escape key |

---

## 🔧 Common Configuration Examples

### Keyboard Hook Configuration
```xml
<!-- Function key triggers -->
<HookKeyboardToStartReading>true</HookKeyboardToStartReading>
<StartReadingKey>F1</StartReadingKey>              <!-- F1 to start -->
<StopReadingKey>F2</StopReadingKey>               <!-- F2 to stop -->
<BeepKey>F3</BeepKey>                             <!-- F3 to beep -->

<!-- Arrow key triggers -->
<StartReadingKey>Down</StartReadingKey>            <!-- Down arrow to start -->
<StopReadingKey>Up</StopReadingKey>               <!-- Up arrow to stop -->

<!-- Space bar trigger -->
<StartReadingKey>Space</StartReadingKey>           <!-- Space to start/stop -->

<!-- Ctrl+Key combinations -->
<UseModifierKeys>true</UseModifierKeys>
<RequireCtrl>true</RequireCtrl>
<StartReadingKey>S</StartReadingKey>               <!-- Ctrl+S to start -->
<StopReadingKey>Q</StopReadingKey>                <!-- Ctrl+Q to stop -->
```

### Data Formatting with Special Characters
```xml
<!-- Tab-separated data -->
<FieldSeparator>&#9;</FieldSeparator>             <!-- Tab character (ASCII 9) -->
<AddCR>true</AddCR>                               <!-- Carriage return (ASCII 13) -->

<!-- Custom prefixes and suffixes -->
<DataPrefix>TAG:</DataPrefix>                     <!-- Text prefix -->
<DataSuffix>&#10;</DataSuffix>                   <!-- Line feed (ASCII 10) -->

<!-- CSV with special characters -->
<CSVSeparator>,</CSVSeparator>                   <!-- Comma separator -->
<CSVQuoteChar>"</CSVQuoteChar>                   <!-- Double quote -->
<CSVEscapeChar>\</CSVEscapeChar>                 <!-- Backslash escape -->
```

### Character Replacement
```xml
<!-- Replace spaces with underscores -->
<ReplaceChars>true</ReplaceChars>
<ReplaceFrom> </ReplaceFrom>                      <!-- Space (ASCII 32) -->
<ReplaceTo>_</ReplaceTo>                         <!-- Underscore (ASCII 95) -->

<!-- Remove control characters -->
<ReplaceFrom>&#1;&#2;&#3;</ReplaceFrom>          <!-- Control chars 1,2,3 -->
<ReplaceTo></ReplaceTo>                          <!-- Remove (empty replacement) -->
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
| **Tab** | 9 | `&#9;` | `<FieldSeparator>&#9;</FieldSeparator>` |
| **Line Feed** | 10 | `&#10;` | `<DataSuffix>&#10;</DataSuffix>` |
| **Carriage Return** | 13 | `&#13;` | `<DataSuffix>&#13;</DataSuffix>` |
| **Escape** | 27 | `&#27;` | `<DataPrefix>&#27;</DataPrefix>` |

### Hexadecimal References
Alternative hex format for special characters:

| Character | ASCII | Hex | Usage |
|-----------|-------|-----|-------|
| **Tab** | 9 | `&#x9;` | `<FieldSeparator>&#x9;</FieldSeparator>` |
| **Line Feed** | 10 | `&#xA;` | `<DataSuffix>&#xA;</DataSuffix>` |
| **Carriage Return** | 13 | `&#xD;` | `<DataSuffix>&#xD;</DataSuffix>` |
| **Space** | 32 | `&#x20;` | `<FieldSeparator>&#x20;</FieldSeparator>` |

---

## 🎯 Application-Specific Character Handling

### Notepad/Text Editors
```xml
<!-- Optimized for text editors -->
<AddCR>true</AddCR>                               <!-- Enter key -->
<AddLF>false</AddLF>                             <!-- Windows line ending -->
<FieldSeparator> </FieldSeparator>               <!-- Space separator -->
```

### Excel/Spreadsheet Applications
```xml
<!-- Optimized for spreadsheets -->
<CSVSeparator>,</CSVSeparator>                   <!-- Comma for CSV -->
<AddCR>true</AddCR>                              <!-- New row -->
<DataPrefix></DataPrefix>                        <!-- No prefix needed -->
<DataSuffix></DataSuffix>                        <!-- No suffix needed -->
```

### Database Applications
```xml
<!-- Optimized for database entry -->
<FieldSeparator>&#9;</FieldSeparator>            <!-- Tab to next field -->
<AddCR>false</AddCR>                             <!-- No auto-enter -->
<TrimWhitespace>true</TrimWhitespace>            <!-- Clean data -->
```

### Web Forms
```xml
<!-- Optimized for web forms -->
<FieldSeparator>&#9;</FieldSeparator>            <!-- Tab to next field -->
<AddCR>false</AddCR>                             <!-- Manual form submission -->
<ConvertToUpper>false</ConvertToUpper>           <!-- Preserve case -->
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

### Debug Configuration
```xml
<!-- Debug character handling -->
<ShowCharacterCodes>true</ShowCharacterCodes>     <!-- Display ASCII codes -->
<LogCharacterSends>true</LogCharacterSends>       <!-- Log sent characters -->
<HighlightSpecialChars>true</HighlightSpecialChars> <!-- Highlight control chars -->
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