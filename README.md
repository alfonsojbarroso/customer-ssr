# Customer SSR

A small server-side-rendered web application built with Java, Spring Boot, and Thymeleaf. The home page is rendered on the server and displays a message and a short list of technologies.

## Requirements

- Java 21 or later
- No separate Maven installation is required; the project includes the Maven Wrapper.

## Run locally

From this project directory, start the application with the Maven Wrapper:

```powershell
.\mvnw.cmd spring-boot:run
```

On macOS or Linux:

```bash
./mvnw spring-boot:run
```

Open [http://localhost:6060](http://localhost:6060). The server listens on port `6060`, as configured in `src/main/resources/application.properties`.

## What the application does

The `GET /` route is handled by `HomeController`. It adds a message and the items `Java`, `Spring Boot`, and `Thymeleaf` to the view model, then renders `templates/index.html` with Thymeleaf.

The page also links a web app manifest and attempts to register a service worker. These are PWA-oriented scaffolding; the current application does not implement customer CRUD or a customer data API.

## Build and test

Run the tests:

```powershell
.\mvnw.cmd test
```

Build the executable JAR:

```powershell
.\mvnw.cmd package
```

Run the packaged application:

```powershell
java -jar target/customer-ssr-0.0.1-SNAPSHOT.jar
```

## Project layout

```text
src/
├── main/
│   ├── java/com/customer/ssr/
│   │   ├── CustomerSsrApplication.java
│   │   └── controller/HomeController.java
│   └── resources/
│       ├── application.properties
│       ├── static/
│       │   ├── manifest.json
│       │   └── sw.js
│       └── templates/index.html
└── test/java/com/customer/ssr/
    └── CustomerSsrApplicationTests.java
```

## PWA assets

The manifest and service worker are in `src/main/resources/static`. The page and service worker currently refer to `/css/styles.css`, and the manifest refers to `/images/icon-192.png`; those files are not included in the project yet. Add the corresponding files under `src/main/resources/static` before relying on the stylesheet cache or app icon. Without the stylesheet, the service worker's precache step can fail.


## Author

Dr. Alfonso José Barroso Barajas