# Task 1 - Initial Codebase Review

## Objective

Prepare local development environment for the Midas Core transaction processing service.

## Technologies Identified

- Java 17
- Spring Boot
- Maven
- Kafka
- SQL Database
- REST API

## Initial Observations

- Project uses Maven Wrapper.
- Configuration is stored in application.yml.
- Source code located under src/.
- Additional services directory exists and requires investigation.

## Architecture Assumption

The system appears to be event-driven.

Expected flow:

Transaction Producer
→ Kafka
→ Midas Core
→ Database
→ REST API

Further investigation required.

## Codebase Inspection Findings

### Existing Components

- MidasCoreApplication
- DatabaseConduit
- UserRecord
- UserRepository
- Balance
- Transaction

### External Dependency

A separate JAR exists:

transaction-incentive-api.jar

This suggests a multi-service architecture where Midas Core communicates with another service.

### Architectural Observation

The system appears to follow:

- Spring Boot
- Repository Pattern
- Event-Driven Processing
- SQL Persistence
- Service Integration

These patterns are commonly used in enterprise banking systems.

## Dependency Analysis

### Spring Boot Web

Provides REST API capabilities.

### Spring Data JPA

Provides repository abstraction and database persistence.

### Spring Kafka

Enables event-driven transaction processing.

### H2 Database

Provides an embedded database for local development and testing.

### Testcontainers Kafka

Allows integration tests to run against a real Kafka instance in a containerized environment.

### Enterprise Relevance

These technologies are commonly used in backend systems responsible for processing financial transactions at scale.


## JAVA_HOME Investigation

Issue:
Maven Wrapper failed because JAVA_HOME was not configured.

Root Cause:
Java 17 was installed but Windows environment variables were not updated.

Resolution:
Configured JAVA_HOME to point to the Java 17 installation directory and added %JAVA_HOME%\bin to PATH.

Enterprise Relevance:
Build tools, CI/CD pipelines, application servers, and IDEs often depend on environment variables. Misconfigured runtime environments are a common onboarding issue for backend engineers.

## Java Environment Setup

Configured Java 17 for:

- IntelliJ IDEA
- JAVA_HOME
- Maven Wrapper

Verified:

- Java 17 runtime
- Maven Wrapper execution
- Project SDK alignment

### Enterprise Relevance

Backend applications depend on consistent runtime versions.

Incorrect Java versions can cause:
- Build failures
- Dependency conflicts
- Production deployment issues

Environment configuration is a fundamental software engineering skill.

## Maven Build Lifecycle

Executed:

mvn clean compile

Outcome:

BUILD SUCCESS

### What Happened

- Maven resolved project dependencies
- Java 17 compiled source code
- Bytecode was generated in target/classes

### Enterprise Relevance

Every backend service follows a build pipeline:

Source Code
→ Compilation
→ Testing
→ Packaging
→ Deployment

A successful build confirms that the project can be compiled consistently across developer machines and CI/CD environments.