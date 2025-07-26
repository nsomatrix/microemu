# MicroEmulator

[![License: LGPL v2.1](https://img.shields.io/badge/License-LGPL%20v2.1-blue.svg)](https://www.gnu.org/licenses/lgpl-2.1)
[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://img.shields.io/badge/build-passing-brightgreen.svg)

MicroEmulator is a pure Java implementation of J2ME (Java 2 Micro Edition) CLDC/MIDP Emulator. It allows demonstration of MIDlet (MIDP/CLDC) based applications as standalone Java applications or as web browser applets.

## Features

- Run MIDlet applications as standalone Java applications
- Run MIDlet applications as web browser applets
- Support for various device profiles
- Compatible with Nokia UI and Siemens API extensions
- Cross-platform (Windows, macOS, Linux)

## Requirements

- Java SE 1.5 or higher
- Maven 2 or higher (for building from source)

## Getting Started

### Running as a Standalone Application

You can run MIDlet applications in two ways:

1. Using the main class:
   ```bash
   java org.microemu.app.Main (MIDlet application main class)
   # or
   java org.microemu.app.Main (MIDlet jad file)
   ```
   
   Note: `microemulator.jar` must be in CLASSPATH

2. Using the JAR file directly:
   ```bash
   java -jar microemulator.jar (MIDlet application main class)
   # or
   java -jar microemulator.jar (MIDlet jad file)
   ```
   
   Parameters:
   - `(MIDlet application main class)` is optional, but if used, the MIDlet application JAR file must be in CLASSPATH
   - `(MIDlet jad file)` must have .jad extension
   - For Nokia UI support, include `nokiaui.jar` in the CLASSPATH
   - For Siemens API support, include `siemensapi.jar` in the CLASSPATH

### Running as a Web Applet

To prepare the applet version of a MIDlet:

1. Select "Save for Web" from the File menu in the standalone MicroEmulator application
2. This process performs additional bytecode modification to satisfy compatibility issues

Example HTML code:
```html
<applet code="org.microemu.applet.Main"
        width=226 height=471 archive="microemu-javase-applet.jar,(MIDlet application jar)">
    <param name="midlet" value="(MIDlet application main class)">
</applet>
```

For Nokia UI support, include `nokiaui.jar` in the archive attribute.
For Siemens API support, include `siemensapi.jar` in the archive attribute.

To use a specific device profile:
```html
<param name="device" value="({device class name} | {device.xml file location})">
```

Example with SimpleDemo MIDlet, Nokia UI support, and Minimum device:
```html
<applet code="org.microemu.applet.Main"
        width=157 height=285 archive="microemu-javase-applet.jar,nokiaui.jar,minimum.jar,simpledemo.jar">
    <param name="midlet" value="org.microemu.midp.examples.simpledemo.SimpleDemo">
    <param name="device" value="org/microemu/device/minimum/device.xml">
</applet>
```

## Building from Source

We use Maven 2 to build the project.

### Prerequisites

Set the following environment variables:
- `JAVA_HOME`
- `SWT_HOME` (to build SWT module)

Optional for testing:
- `WTK_HOME` to compile and test MIDlets

### Build Commands

To create Eclipse projects:
```bash
mvn eclipse:clean eclipse:eclipse -DdownloadSources=true
```

To build without tests:
```bash
mvn -Dmaven.test.skip=true
```

To build distribution assembly:
```bash
mvn -DperformRelease=true
```
The distribution package will be created in `microemulator/target/microemulator-2.X.X.zip`

Note: The `microemu-javase-swt` module is not built by default. To activate its build, add the property `buildByMicroEmulatorTeam` to `settings.xml`.

## Project Structure

- `microemu-cldc` - CLDC implementation
- `microemu-midp` - MIDP implementation
- `microemu-javase` - Java SE specific implementation
- `microemu-javase-applet` - Applet implementation
- `microemu-javase-swing` - Swing UI implementation
- `microemu-javase-swt` - SWT UI implementation
- `microemu-examples` - Example MIDlet applications
- `microemu-tests` - Test suite

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a pull request

## License

This project is licensed under the GNU Lesser General Public License (LGPL) - see the [COPYING](microemulator/COPYING) file for details.

## Acknowledgments

- Thanks to all contributors who have helped with the development
- Device skins and profiles included in the distribution
- Special thanks to the 3G Lab for their contributions

## Support

- Issue tracker: [Google Code Issues](http://code.google.com/p/microemu/issues/list)
- Mailing list: microemulator-support@googlegroups.com
- Project website: [http://www.microemu.org/](http://www.microemu.org/)
