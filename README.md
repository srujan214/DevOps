Experiment 4

Practical Exercise: Build and Run a Java Application with Maven, Migrate the Same Application to Gradle

Part 1: Create and Build a Java Application with Maven

Step 1: Create a Maven Project in IntelliJ IDEA

1. Open IntelliJ IDEA

Launch IntelliJ IDEA and click on File → New→ Project.

2. Select Maven

In the New Project window, choose Maven from the options on the left.

Check Create from archetype and select maven-archetype-quickstart.

Click Next.

3. Enter Project Details

GroupId: com.example

ArtifactId: MVNGRDLDEMO

Click Next and then Finish.

4. Wait for IntelliJ to Load Dependencies

IntelliJ will automatically download the Maven dependencies, so just relax for a moment.

Step 2: Update pom.xml to Add Build Plugin To compile and package your project into a jar file, you need to add the Maven Compiler and

Jar plugins.

a) 1. Open the pom.xml file.

2. Add the following inside the <project> tag:

<build>

<plugins>

<!-- Compiler Plugin -->

<plugin>

<groupId>org.apache.maven.plugins</groupId>

<artifactId>maven-compiler-plugin</artifactId>

<version>3.8.1</version>

<configuration>

<source>1.8</source>

<target>1.8</target>

</configuration>

</plugin>

<!-- Jar Plugin -->

<plugin>

<groupId>org.apache.maven.plugins</groupId>

<artifactId>maven-jar-plugin</artifactId>

<version>3.2.0</version>

<configuration>
<archive>

<manifest>

<addClasspath>true</addClasspath>

<mainClass>org.example.Main</mainClass>

</manifest>

</archive>

</configuration>

</plugin>

</plugins>

</build>

b) 1. Open the Main.java file. 2. Add the following code package org.example;

public class Main

static void main() {

System.out.println("Hello students"); System.out.println("Welcome to Devops Lab"); System.out.println("Lab Program no.4");


Step 3: Build and Run the Maven Project

1. Open IntelliJ IDEA Terminal

Press Alt + F12 to open the terminal.

2. Compile and Package the Project

Run the following commands to build the project:

mvn clean compile

mvn package

3. Locate the JAR File

After running the above, your jar file will be located at: D: \Idea Projects\MVNGRDLDEMO\target MVNGRDLDEMO-1.0-SNAPSHOT.jar

4. Run the JAR File

To run the generated JAR file, use: java -jar target\MVNGRDLDEMO-1.0-SNAPSHOT.jar

Part 2: Migrate Maven Project to Gradle

Step 1: Initialize Gradle in Your Project 1. Open Terminal in IntelliJ IDEA Make sure you're in the project directory: cd "D:\Idea Projects MVNGRDLDEMO
2. Run Gradle Init Command
Execute the following command to migrate your Maven project to Gradle:
gradle init --type pom
This command will convert your Maven pom.xml into a Gradle build.gradle file.
Step 2: Review and Update build.gradle
Open build.gradle in IntelliJ IDEA.
Ensure the following configurations are correct:
plugins {
id 'java'
}
group = 'com.example'
version = '1.0-SNAPSHOT'
repositories {
mavenCentral()
}
dependencies {
testImplementation 'junit:junit:4.13.2'
}
jar {
manifest {
attributes('Main-Class': 'org.example.Main')
}
}
Step 3: Build and Run the Gradle Project
1. Clean and Build the Project
To clean and build your Gradle project, run:
gradle clean build
2. Run the Generated JAR File
Now, run the generated JAR file using:
java -jar build/libs/MVNGRDLDEMO-1.0-SNAPSHOT.jar
