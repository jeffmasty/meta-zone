# meta-zone
Aggregator for the [JudahZone](https://github.com/jeffmasty/JudahZone) project

build all: 
mvn -T1C -DskipTests clean install

build zone-core:
mvn -pl :zone-core -am -DskipTests clean install


---------------------------

# meta-zone

**Maven aggregator for the [JudahZone](https://github.com/jeffmasty/JudahZone) real-time audio project.**

This project serves as the top-level builder and dependency manager for all modules in the JudahZone ecosystem. It ensures consistent versions, simplifies the build process, and manages the relationships between modules.

---

## Project Structure

The `meta-zone` aggregator manages the following modules:

-   **`JudahZone`**: The main groovebox application (mixer, sequencer, looper, effects).
-   **`zone-core`**: Shared utilities for logging, constants, and memory management.
-   **`zone-fx`**: Base classes and implementations for audio effects (reverb, delay, etc.).
-   **`zone-gui`**: Common Swing GUI components and helpers.
-   **`zone-scope`**: A real-time audio visualization toolkit (spectrogram, spectrometer, etc.).
-   **`zone-javax`**: Wrappers for JavaSound audio input and output.
-   **`zone-jnajack`**: JNA-based bindings for the JACK audio connection kit.
-   **`zone-test`**: Shared utilities and fixtures for unit testing.

---

## Prerequisites

-   **Java 21** or newer (tested on OpenJDK 21).
-   **Maven 3.8+** (for building the project).

---

## Build 

Clone this repository to get started. All build commands can be run from the `meta-zone` root directory.

Build a Specific Module

To build a single module and its required dependencies, use the -pl (projects) and -am (also make) flags.

- build and run the zone-scope visualizer:

	mvn -pl :zone-scope -am -DskipTests clean package
	
	java -jar ../zone-scope/zone-scope-full.jar

- Build the `zone-fx` DSP package library (useful if you only need effects tooling):

	mvn -pl :zone-fx -am -DskipTests clean package

- To build the JudahZone application, full dependencies:

	mvn -pl :JudahZone -am -DskipTests clean package
	
- This command cleans, builds, and installs all modules in parallel. This is the recommended command for a full project build.

	mvn -T1C -DskipTests clean install

•  -T1C: Builds with one thread per CPU core.
•  -DskipTests: Skips running unit tests during the build.
•  clean install: Deletes previous build artifacts and installs the new artifacts into your local Maven repository (~/.m2).

---

## Contributing

This project aggregates multiple repositories. To contribute:

1.  Fork the `meta-zone` repository.
2.  Make your changes in the appropriate module branch.
3.  Submit a Pull Request against the `meta-zone` aggregator. Please ensure all modules build successfully before submitting.

---

## License

This project and its submodules are licensed under the **GPL-3.0 License**.