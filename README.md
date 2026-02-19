# 🌱 IrrIot - Smart Irrigation System

> **IoT-Based Agricultural Solution** - Intelligent water management through Arduino and Java Web integration

The project presented at the 2019 Agrotins Fair consisted of an integration between Arduino and a Java-based web platform to enable efficient monitoring and control of an irrigation system. The solution was designed to deliver precision agriculture capabilities, promoting optimized water usage and greater resource efficiency in agricultural production environments.

This project was recognized as one of the highlights of the fair, standing out for its practical innovation and real-world applicability. It also earned the highest possible grade in the Network Development and Infrastructure course, demonstrating strong technical execution in both software integration and infrastructure design.

See the full **[article here](https://www.unitins.br/nPortal/portal/noticias/detalhes/2287-2019-5-9-estande-da-unitins-apresenta-resultado-de-pesquisas-por-meio-de-exposicao-de-trabalhos-e-mesas-redondas)** !

## 📑 Table of Contents

- [✨ Key Features](#-key-features)
- [🛠️ Technologies Used](#️-technologies-used)
- [📦 Prerequisites](#-prerequisites)
- [🚀 How to Run Locally](#-how-to-run-locally)
- [🏗️ Production Build](#-production-build)
- [📁 Project Structure](#-project-structure)
- [🔧 Configuration](#-configuration)
- [📚 Documentation](#-documentation)
- [👨‍💻 Author](#-author)

## ✨ Key Features

### 🌡️ Real-Time Monitoring
- ✅ **Soil Moisture Tracking** - Continuous monitoring of soil humidity levels
- ✅ **Environmental Sensors** - Air temperature and humidity measurement
- ✅ **Light Detection** - Luminosity monitoring for optimal irrigation timing
- ✅ **Historical Data** - Log tracking and historical analysis of sensor readings
- ✅ **Live Dashboard** - Real-time data visualization with interactive charts

### 💧 Irrigation Control
- ✅ **Automated Control** - Arduino-based irrigation system activation
- ✅ **Remote Management** - Web-based control interface for irrigation operations
- ✅ **Smart Scheduling** - Data-driven irrigation decisions based on sensor inputs
- ✅ **Resource Optimization** - Efficient water usage through intelligent monitoring

### 📊 Data Visualization
- ✅ **Interactive Charts** - Chart.js powered data visualization
- ✅ **PrimeFaces Components** - Rich UI components for enhanced user experience
- ✅ **Responsive Design** - Bootstrap-based mobile-friendly interface
- ✅ **Real-Time Updates** - Dynamic data refresh without page reload

### 🎨 User Experience
- ✅ **Intuitive Navigation** - Simple menu system with clear sections
- ✅ **Visual Feedback** - Status indicators and notifications
- ✅ **Cross-Device Support** - Responsive layout for desktop, tablet, and mobile
- ✅ **Custom Branding** - Project logo and themed interface

## 🛠️ Technologies Used

### Backend
- **Java** 11 - Core programming language
- **JSF (JavaServer Faces)** 2.3.8 - Component-based web framework
- **CDI (Weld)** 3.1.0 - Contexts and Dependency Injection
- **PrimeFaces** 7.0 - Rich UI component library for JSF
- **Hibernate Validator** 6.0.16 - Bean validation framework

### Frontend
- **XHTML** - JSF view templates
- **Bootstrap** 5.x - Responsive CSS framework
- **Chart.js** - JavaScript charting library
- **Font Awesome** 5.8.1 - Icon toolkit
- **JSTL** 1.2 - JavaServer Pages Standard Tag Library

### Database
- **PostgreSQL** 42.2.5 - Relational database for data persistence

### Hardware Integration
- **Arduino** - Microcontroller for sensor data collection
- **IoT Sensors** - Humidity, temperature, luminosity, and soil moisture sensors
- **Serial Communication** - Arduino to web application data transfer

### Build & Deployment
- **Maven** 3.x - Dependency management and build automation
- **WAR Packaging** - Java Web Application Archive deployment
- **Jakarta EE** 8 (Java EE 8) - Enterprise application platform

## 📦 Prerequisites

Before you begin, ensure you have the following installed:

- **Java Development Kit (JDK)** 11 or higher
- **Apache Maven** 3.6.x or higher
- **PostgreSQL** 12.x or higher
- **Apache Tomcat** 9.x or compatible Jakarta EE application server
- **Arduino IDE** (for hardware setup)
- **Git**

## 🚀 How to Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/matheuspcouto/irriot.git
cd irriot
```

### 2. Configure the database

Create a PostgreSQL database for the application:

```sql
CREATE DATABASE irriot;
CREATE USER irriot_user WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE irriot TO irriot_user;
```

Update database connection settings in your application server configuration.

### 3. Configure file paths

Update the sensor data log file path in [IrrigacaoController.java](src/controller/IrrigacaoController.java#L30):

```java
BufferedReader arquivo = new BufferedReader(new FileReader(
    "path/to/your/Historico_de_Log.txt"));
```

### 4. Build the application

```bash
mvn clean install
```

This will:
1. ✅ Download all dependencies
2. ✅ Compile Java sources
3. ✅ Package the application as a WAR file
4. ✅ Run unit tests (if configured)

### 5. Deploy to application server

Copy the generated WAR file to your Tomcat webapps directory:

```bash
cp target/Irriot-0.0.1-SNAPSHOT.war $TOMCAT_HOME/webapps/Irriot.war
```

Or use your IDE's built-in deployment tools.

### 6. Start the application server

```bash
$TOMCAT_HOME/bin/startup.sh  # Linux/Mac
$TOMCAT_HOME/bin/startup.bat # Windows
```

### 7. Access the application

Navigate to `http://localhost:8080/Irriot/faces/menu.xhtml` in your web browser.

**Available pages:**
- `menu.xhtml` - Main dashboard and menu
- `grafico.xhtml` - Data visualization and charts

## 🏗️ Production Build

### Build for production

```bash
mvn clean package -Pprod
```

This command will:
1. ✅ Compile and optimize all Java classes
2. ✅ Bundle web resources (CSS, JS, XHTML)
3. ✅ Generate production-ready WAR file in `target/`
4. ✅ Apply resource minimization

**Build artifacts:**
- Output file: `target/Irriot-0.0.1-SNAPSHOT.war`
- Ready for deployment to production servers
- Compatible with Tomcat, WildFly, GlassFish, or any Jakarta EE 8 server

**Deployment options:**
- Apache Tomcat 9.x
- WildFly Application Server
- GlassFish Server
- Cloud platforms (AWS, Azure, Google Cloud)

## 📁 Project Structure

```
Irriot/
├── src/
│   ├── BotaoController.java              # Navigation controller
│   ├── ChartJsView.java                  # Chart data provider
│   ├── controller/
│   │   └── IrrigacaoController.java      # Main irrigation logic controller
│   └── application/
│       ├── MensagensSistema.properties   # System messages (i18n)
│       └── Util.java                     # Utility functions
├── WebContent/
│   ├── grafico.xhtml                     # Data visualization page
│   ├── menu.xhtml                        # Main menu/dashboard
│   ├── META-INF/
│   │   └── MANIFEST.MF                   # Application manifest
│   ├── resources/
│   │   ├── css/
│   │   │   ├── bootstrap.css             # Bootstrap framework
│   │   │   └── style.css                 # Custom styles
│   │   ├── js/
│   │   │   ├── bootstrap.js              # Bootstrap JavaScript
│   │   │   └── bootstrap.bundle.js       # Bootstrap with dependencies
│   │   └── img/
│   │       ├── logo.png                  # Project logo
│   │       └── favicon.ico               # Site favicon
│   └── WEB-INF/
│       ├── beans.xml                     # CDI configuration
│       ├── faces-config.xml              # JSF configuration
│       └── web.xml                       # Web application descriptor
├── target/                               # Build output directory
├── Historico_de_Log.txt                  # Sensor data log file
├── pom.xml                               # Maven project configuration
└── README.md                             # Project documentation
```

## 🔧 Configuration

### Database Configuration

Configure your database connection in your application server's context configuration or `persistence.xml`:

```xml
<persistence-unit name="IrriotPU">
    <properties>
        <property name="javax.persistence.jdbc.url" value="jdbc:postgresql://localhost:5432/irriot"/>
        <property name="javax.persistence.jdbc.user" value="irriot_user"/>
        <property name="javax.persistence.jdbc.password" value="your_password"/>
    </properties>
</persistence-unit>
```

### Arduino Setup

1. Connect sensors to Arduino pins (configure according to your hardware setup)
2. Upload the Arduino sketch to read sensor data
3. Configure serial communication to write data to `Historico_de_Log.txt`
4. Ensure the log file is accessible to the Java application

### Sensor Data Format

The application expects sensor data in the following format in `Historico_de_Log.txt`:

```
[Date/Time]
Luminosity: [value]
Air Humidity: [value]%
Air Temperature: [value]°C
Soil Status: [wet/dry]
```

## 📚 Documentation

### Component Architecture

The application follows the **MVC (Model-View-Controller)** pattern with **CDI** for dependency injection:

- **Views (XHTML)** - JSF Facelets templates with PrimeFaces components
- **Controllers (Java)** - CDI managed beans with `@Named` and `@ViewScoped`
- **Model** - Data entities and business logic
- **Services** - Arduino integration and data processing

### Key Controllers

| Controller | Scope | Description |
|-----------|-------|-------------|
| **IrrigacaoController** | `@ViewScoped` | Reads sensor data from log file, provides real-time irrigation metrics |
| **BotaoController** | `@ViewScoped` | Handles navigation between pages (menu and chart views) |
| **ChartJsView** | - | Provides data for Chart.js visualizations |

### JSF Configuration

- **Servlet mapping:** `/faces/*`
- **Welcome file:** `menu.xhtml`
- **ViewScoped beans:** Maintained during view lifecycle
- **CDI integration:** Full dependency injection support

### Sensor Integration

The system reads sensor data from a text file that Arduino writes to via serial communication. The [IrrigacaoController](src/controller/IrrigacaoController.java) parses this file to extract:

- **Air Humidity** - Latest reading from DHT sensor
- **Air Temperature** - Current temperature measurement
- **Luminosity** - Light level detection
- **Soil Moisture Status** - Wet/dry soil condition

### Styling and Themes

- **Bootstrap 5** - Core responsive framework
- **Custom CSS** - `style.css` for project-specific styling
- **PrimeFaces Theme** - Rich component styling
- **Font Awesome** - Icon set for UI elements

## 👨‍💻 Author

**Matheus Pimentel Do Couto**
- Email: matheuspcouto70@gmail.com
- GitHub: [@matheuspcouto](https://github.com/matheuspcouto)
- LinkedIn: [matheuspcouto](https://www.linkedin.com/in/matheuspcouto/)
- Instagram: [@matheuspcouto](https://www.instagram.com/matheuspcouto/)

---

⭐ **IrrIot** - Smart Irrigation System | Presented at Agrotins 2019 | Built with Java, Arduino, and 🌱
