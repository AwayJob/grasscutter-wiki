# Prerequisites
- [Java SE Development Kits - 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
- [Git](https://git-scm.com/downloads)
- [Gradle](https://gradle.org/next-steps/?version=7.4.2&format=all)

## Note about Gradle
If the command `gradle` is mentioned, use your operating system equivalent. (ex. on Windows use `gradlew`)

# Building
Grasscutter uses Gradle to handle dependencies & building.

##### Windows

```shell
git clone https://github.com/Grasscutters/Grasscutter.git
cd Grasscutter
.\gradlew.bat # Setting up environments
.\gradlew jar # Compile
```

##### Linux

```bash
git clone https://github.com/Grasscutters/Grasscutter.git
cd Grasscutter
chmod +x gradlew
./gradlew jar # Compile
```

You can find the output jar in the root of the project folder.

(other build methods work too!)
