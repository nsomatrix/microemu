# MicroEmulator

MicroEmulator is a free, open-source emulator for J2ME (Java 2 Platform, Micro Edition) applications. It allows you to run MIDP (Mobile Information Device Profile) applications and games on your desktop computer.

## Project Structure

This repository contains the source code for various MicroEmulator modules, including:
*   `microemulator-javase-swing`: The main desktop application (Swing-based).
*   `microemulator-javase`: Core Java SE integration.
*   `microemulator-midp`: MIDP API implementation.
*   `microemulator-cldc`: CLDC API implementation.
*   `api`: Core API definitions.
*   And many more modules for different platforms and extensions.

## Building the Project

MicroEmulator uses Gradle as its build system.

### Prerequisites

*   **Java Development Kit (JDK):** Version 8 or higher is recommended.
*   **Gradle:** The project includes a Gradle Wrapper, so you don't need to install Gradle globally.

### Build Steps

1.  **Clone the repository (if you haven't already):**
    ```bash
    git clone https://github.com/microemulator/microemulator.git
    cd microemulator
    ```
    *(Note: Assuming you are already in the project root `/home/manish/project/microemu`)*

2.  **Build the entire project:**
    To compile all modules and generate their respective JAR files, run the following command from the project root directory:
    ```bash
    ./gradlew build
    ```
    This command will download necessary dependencies, compile the source code, and package the modules.

3.  **Build only the desktop application JAR:**
    If you only need the runnable desktop application, you can build just that module:
    ```bash
    ./gradlew :microemulator:microemu-javase-swing:jar
    ```
    This command will ensure all necessary dependencies for the `microemu-javase-swing` module are built and included in its JAR.

## Running the Desktop Application

After a successful build, you can find the runnable JAR for the desktop application.

### Location of the Runnable JAR

The main runnable JAR for the Swing-based desktop application is located at:
`microemulator/microemu-javase-swing/build/libs/microemu-javase-swing-2.0.5-SNAPSHOT.jar`

### Execution

To run the MicroEmulator desktop application, use the `java -jar` command:
```bash
java -jar microemulator/microemu-javase-swing/build/libs/microemu-javase-swing-2.0.5-SNAPSHOT.jar
```
This will launch the MicroEmulator GUI, allowing you to load and run J2ME applications.

## Resources

*   **Official Website (if applicable):** [Insert official website link here if one exists, otherwise remove]
*   **Source Code:** [https://github.com/microemulator/microemulator](https://github.com/microemulator/microemulator) (This repository)

## Contributing

Contributions are welcome! Please refer to the project's guidelines (if any) for contributing.