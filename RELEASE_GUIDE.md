# SonarQube Japanese Localization Pack Release Guide

[日本語](https://github.com/cresco-sonar/sonar-l10n-ja/blob/master/RELEASE_GUIDE_ja.md)

This document describes the release procedure for SonarQube Japanese Localization Pack (sonar-l10n-ja).

## 1. Prerequisites

- Git installed
- Maven installed
- Write access to the GitHub repository

## 2. Pre-Release Preparation

### 2.1. Code Review

Before releasing, check the following:

- Translation content
- Tests pass successfully
- Version number in `pom.xml` is appropriate (e.g., `1.1-SNAPSHOT`)

### 2.2. Test Build

Verify that the build works correctly before starting the release process:

```bash
mvn clean package
```

When this command succeeds, a plugin file called `target/sonar-l10n-ja-plugin-1.1-SNAPSHOT.jar` will be generated.

## 3. Executing the Release

### 3.1. Maven Release Execution

Run the release process with the following command:

```bash
mvn release:prepare release:perform
```

This command does the following:

1. Removes the `-SNAPSHOT` suffix from the version number (e.g., `1.1-SNAPSHOT` → `1.1`)
2. Creates a release tag (e.g., `sonar-l10n-ja-plugin-1.1`)
3. Commits and pushes the tag to the repository
4. Sets the version number for the next development version (e.g., `1.2-SNAPSHOT`)
5. Executes the release build
6. Generates artifacts in `target/checkout/target/releases`

### 3.2. Verify Generated JAR File

After the release process succeeds, you can check the following file:

- `target/sonar-l10n-ja-plugin-1.1.jar` (release version JAR)

## 4. Creating a GitHub Release

### 4.1. Navigate to GitHub Release Page

1. Open the GitHub repository page in your browser: https://github.com/cresco-sonar/sonar-l10n-ja
2. Go to the "Releases" section (on the right side of the repository page)
3. Click the "Draft a new release" or "Create a new release" button

### 4.2. Enter Release Information

1. For "Choose a tag", select the tag created during the Maven release (e.g., `sonar-l10n-ja-plugin-1.1`)
2. Enter a release title (e.g., "Japanese Localization Pack v1.1")
3. Write release notes (changes and improvements)

### 4.3. Attach JAR File

1. Drag & drop or upload the JAR file generated during the build (`target/sonar-l10n-ja-plugin-1.1.jar`) using the "Attach binaries" button
2. Checksum files are usually not necessary but can be included if needed

### 4.4. Publish Release

Review the information and click the "Publish release" button to publish the release.

## 5. Post-Release Tasks

### 5.1. Submit to SonarQube (Optional)

To register with the SonarQube marketplace, you need to contact the SonarSource team.

### 5.2. Verify Release Information

After releasing, check the following:

- JAR file is correctly attached to the GitHub release page
- Download links work properly
- Preparation for the next development version is complete

---

## Reference Commands

### Simple Build (For Testing)

```bash
mvn clean package
```

### Execute Release Build

```bash
mvn release:prepare release:perform
```

### Cleanup If Release Process Fails

```bash
mvn release:clean
```
