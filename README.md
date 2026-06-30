# Building a REST API with Spring Boot - Learning Summary (Provided by Claude)

Below are some summaries of my chat conversation with Claude as I worked through this Spring Academy Course, which walked me through on how to build a Cash Card REST API using Spring Boot.

## Top Lessons Learned While Working on This Project

### 1. Spring Boot Version Mismatch (biggest issue)
You had Spring Boot 4.1.0 installed while the course was written for 3.x. This caused a
cascade of problems including the wrong `TestRestTemplate` package path and other API
differences. We diagnosed it through your `build.gradle` and downgraded to `3.3.5`.

### 2. Wrong JSONArray Import
You were using `org.json.JSONArray` instead of `net.minidev.json.JSONArray`, which caused
`containsExactlyInAnyOrder` to fail since AssertJ couldn't resolve the correct `ListAssert`
type. A classic Java gotcha where multiple libraries share identical class names.

### 3. Spring Security Packages Not Resolving
After correctly adding Spring Security to `build.gradle` and confirming Gradle was resolving
the jars properly via the dependency tree, IntelliJ still couldn't find
`org.springframework.security` packages. Fixed by invalidating IntelliJ's caches via
**File → Invalidate Caches → Invalidate and Restart**.

### 4. Invalid Gradle JDK Configuration
Opening an existing Spring Boot project in IntelliJ threw a Gradle JDK configuration error.
Fixed by pointing IntelliJ's Gradle JVM setting to your Java 17 installation.



## Spring & Java
- What a Steel Thread is and how it applies to Spring Boot development
- Inversion of Control vs Dependency Injection and how they differ
- What Spring Beans are and how they compare to J2EE/Jakarta EJBs
- The Service Locator pattern and why Spring prefers DI over it
- Advantages and disadvantages of Dependency Injection
- What API contracts are and how they drive both implementation and testing
- What `@PathVariable` is and when to use it vs `@RequestParam` and `@RequestBody`
- What the `@` symbol means in Java annotations vs JSONPath syntax
- What idempotency means and why POST isn't idempotent
- What `$..id` (recursive descent) and `$[*]` (wildcard) mean in JSONPath
- What `<S extends T>` means in Java generics
- How Spring Data derived query methods work and how Spring generates SQL from method names
- How to validate derived query method names in Spring Data
- How embedded Tomcat works in Spring Boot and why you don't need a standalone install
- The difference between Spring Boot 3.x and 4.x package changes

## Java General
- How to convert a String to Long in Java 17
- The difference between `long` primitive and `Long` wrapper type
- Why IntelliJ's "type may be primitive" warning isn't always correct in Spring context
- How to suppress IntelliJ inspections properly using `//noinspection` vs `@SuppressWarnings`
- The difference between IntelliJ warnings and weak warnings

## IntelliJ
- How to fix Invalid Gradle JDK configuration error
- How to sync settings across devices using a JetBrains account
- How to enable and customize semantic highlighting for more color distinction
- How to use the Structure panel (`Alt+7`) and File Structure popup (`Ctrl+F12`)
- The `Ctrl+Alt+O` shortcut for organizing imports
- The `Alt+Enter` shortcut for auto-importing classes
- The `Ctrl+Shift+U` shortcut for toggling caps
- How to invalidate caches to fix mysterious resolution problems
- How to unstage and undo git commits in IntelliJ
- How to connect Claude as an AI agent via JetBrains AI Assistant

## Manjaro/Linux
- How to enable color output in pacman via `/etc/pacman.conf`
- Recommended Java development packages for Manjaro
- How to install the Spring Boot CLI via AUR using `yay`
- How to convert a Spring Initializr curl command to a Spring CLI command
- The difference between `yay` and `pacman` and when to use each
- How to install and use `yay` for AUR packages
- How to push a new git repository to GitHub
- How to configure USB tethering and Wi-Fi hotspot on Android
- How to connect to a Wi-Fi network using `nmcli` on Sway
- How to rearrange windows vertically in Sway
- How to kill a process with `pkill`
- How to convert spaces to tabs in Java files using `unexpand`
- How to enable color syntax highlighting in IntelliJ

## General Development Concepts
- What Scrum is and why so many resources are devoted to teaching it
- Why Rust web frameworks aren't yet competing directly with Spring Boot
- Whether web applications built on Rust are outpacing Spring
- How Firefox Sync and Tab Session Manager can sync pinned tabs across devices
- How to save and persist browser tabs across machines