# import_custom_jar_demo01
Employee Jar Create and use it in Employee Class Project
1. Write a Project inside it only one Class Empoyee and Make a Jar of it and use that in Another Project;
-->
Project 1:
	employee-lib
	
	location : C:\Users\TANMOY SAHA\OneDrive\Desktop\New folder\employee-lib
	
pom.xml:

  <modelVersion>4.0.0</modelVersion>
  <groupId>com.employee</groupId>
  <artifactId>employee-lib</artifactId>
  <version>1.0</version>
  <name>employee-artifact</name>
  <!-- FIXME change it to the project's website -->
  <url>https://github.com/yourusername/employee-lib</url>
  
  
now use Maven commands to generate jar:

mvn clean install

outp:
[INFO] [1m------------------------------------------------------------------------[m
[INFO] [1;32mBUILD SUCCESS[m
[INFO] [1m------------------------------------------------------------------------[m
[INFO] Total time:  9.808 s
[INFO] Finished at: 2025-07-29T00:35:57+05:30
[INFO] [1m------------------------------------------------------------------------

Jar Name: employee-lib-1.0.jar
jar location:
C:\Users\TANMOY SAHA\OneDrive\Desktop\New folder\employee-lib\target\employee-lib-1.0.jar
When we want to ust it use its below dependency

Its Dependency Name:

<dependency>
    <groupId>com.employee</groupId>
    <artifactId>employee-lib</artifactId>
    <version>1.0.0</version>
</dependency>
------------------
✅ Option 1: Install the JAR into your local Maven repo
🔧 Run this command:

mvn install:install-file ^
  -Dfile="C:\Users\TANMOY SAHA\OneDrive\Desktop\New folder\employee-lib\target\employee-lib-1.0.jar" ^
  -DgroupId=com.employee ^
  -DartifactId=employee-lib ^
  -Dversion=1.0.0 ^
  -Dpackaging=jar
  
  <dependency>
    <groupId>com.employee</groupId>
    <artifactId>employee-lib</artifactId>
    <version>1.0.0</version>
</dependency>


✅ Option 2 Local File: Add to pom.xml of the consuming project:

<dependency>
    <groupId>com.employee</groupId>
    <artifactId>employee-lib</artifactId>
    <version>1.0.0</version>
    <scope>system</scope>
    <systemPath>C:/libs/employee-lib-1.0.jar</systemPath>
</dependency>

or
same project location :

<dependencies>
    <dependency>
        <groupId>com.employee</groupId>
        <artifactId>employee-lib</artifactId>
        <version>1.0.0</version>
        <scope>system</scope>
        <systemPath>${project.basedir}/lib/employee-lib-1.0.jar</systemPath>
    </dependency>
</dependencies>


Project 2:
----------

	customer-lib
	location : C:\Users\TANMOY SAHA\OneDrive\Desktop\New folder\customer-lib
	
pom.xml:

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>

		<dependency>
			<groupId>com.employee</groupId>
			<artifactId>employee-lib</artifactId>
			<version>1.0.0</version>
			<scope>system</scope>
			<systemPath>C:/libs/employee-lib-1.0.jar</systemPath>
		</dependency>

code:

package com.customer.customer_lib;

import employee_group.employee_artfact.Employee;

public class Customer {

	public Employee employee;
}
