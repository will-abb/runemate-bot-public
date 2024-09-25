# RuneMate Bot Project Setup
Follow this: https://www.runemate.com/community/threads/development-project-setup.23689/

## Requirements
- An IDE (IntelliJ IDEA recommended)
- JDK 17 (Temurin recommended)

## Project Setup

1. **Open IntelliJ IDEA** and start a new project:
    - **Name:** Choose a name for your project (e.g., `runematej-bots`)
    - **Build System:** Gradle
    - **Gradle DSL:** Groovy
    - **Add sample code**: Off
    - **Gradle distribution:** Wrapper
    - **Gradle version:** 8.7 (or the latest available)
    - **Group ID:** `com.runemate.username` (replace `username` with your actual username)
    - **Artifact ID:** Same as the project name

2. **Configure the project:**
    - Ensure you are using JDK 17. IntelliJ can download it for you if needed.
    - Open the `build.gradle` file and replace its contents with the following:

      ```groovy
      plugins {
          id 'java' // Apply the Java plugin to your Gradle project
          id 'com.runemate' version '1.0.0' // Apply the RuneMate plugin to your Gradle project
      }
 
      repositories {
          mavenCentral()
          maven { url 'https://jitpack.io' }
      }
 
      // Used to configure various aspects of the RuneMate plugin
      runemate {
          devMode.set(true)
      }
 
      // Sets the project language level to 17
      java {
          toolchain {
              languageVersion = JavaLanguageVersion.of(17)
          }
      }
      ```

3. **Create the Manifest File:**
    - Create a new file named `Test.manifest.yml` in the directory `src/main/resources/com/tinsel1608/scripts`.
    - Add the following content to `Test.manifest.yml`:

      ```yaml
      mainClass: com.tinsel1608.scripts.Test
      name: Test
      internalId: test-bot
      tagline: Test Bot Tagline
      description: Test Bot Description
      version: 0.0.1
      compatibility:
        - OSRS
      categories:
        - COOKING
      features:
        - type: DIRECT_INPUT
          mode: optional
      access: public
      hidden: false
      resources:
        - com/tinsel1608/scripts/Test
      tags:
        - Bot
      ```

4. **Verify the Directory Structure:**
    - Ensure the directory structure looks like this after building the project:
    - the build directory will appear after the build
      ```
      runematej-bots
      |-- build
      |   |-- classes
      |       |-- java
      |           |-- main
      |               |-- com
      |                   |-- tinsel1608
      |                       |-- scripts
      |                           |-- Test.class
      |-- src
      |   |-- main
      |       |-- java
      |           |-- com
      |               |-- tinsel1608
      |                   |-- scripts
      |                       |-- Test.java
      |       |-- resources
      |           |-- com
      |               |-- tinsel1608
      |                   |-- scripts
      |                       |-- Test.manifest.yml
      |-- build.gradle
      |-- settings.gradle
      ```

6. **Configure the RuneMate Client:**
    - Ensure the RuneMate client is configured to point to the correct directory:
        1. Delete any incorrect paths.
        2. Add the path `C:\Users\willi\IdeaProjects\runematej-bots` to the project.

7. **Run the `runClient` Task:**
    - In IntelliJ IDEA, open the Gradle tool window.
    - Navigate to `Tasks > runemate > runClient` and double-click to run the task.

By following these steps and using the provided configurations, your bot should be correctly set up and recognized by the RuneMate client. If you encounter any issues, ensure that all paths and configurations are accurate and that the necessary files are in the correct locations.
