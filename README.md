
## EWS (Emergent Web Server) Deployment Guide

### Table of Contents
- [Prerequisites](#prerequisites)
- [Docker-Based Execution](#docker-based-execution)
- [Native Installation](#native-installation)


### Prerequisites <a name="prerequisites"></a>

Before proceeding, ensure that:

- **Docker** is installed and running on your machine. If not, refer to the [Docker Installation Guide](https://www.docker.com/get-started).

---

### Docker-Based Execution <a name="docker-based-execution"></a>

#### 1. **Deploy the EWS Container**

Pull and run the EWS container from Docker Hub:

```bash
docker run --name=ews -p 2011-2012:2011-2012 -d robertovrf/ews:1.0
```

#### 2. **Check Container Status**

To ensure the EWS container is running:

```bash
docker container ls | grep ews
```

#### 3. **Interact with the EWS Container**

To access the terminal of the EWS container:

```bash
docker exec -it ews bash
```

Within the EWS container:

#### 4. **Navigate to the Target Directory**

```bash
cd emergent_web_server/pal/
```

#### 5. **Start the Interactive Emergent System Tool**

```bash
dana -sp ../repository InteractiveEmergentSys.o
```

#### 6. **Utilize EWS Features**

Here's a list of common commands and instructions for interacting with the EWS:

- **General Commands**:
  - View help: `sys> help`
  - List configurations: `sys> get_all_configs`
  - View current configuration: `sys> get_config`
  - Update configuration: `sys> set_config [ID]`

- **Web Interface**:
  - Visit: http://localhost:2012/
  - Explore available resources: Review `emergent_web_server/repository/htdocs`

#### 7. **Perception and Learning**

For machine learning enthusiasts:

- Retrieve performance data: `sys> get_perception`
- Initiate learning algorithm: `sys> learn`

  **Parameters**:
  - Observation window: `5000ms` (recommended)
  - Exploration threshold: `3` (recommended)
  - Rounds: `52` (recommended)

---

### Native Installation (For Power Users) <a name="native-installation"></a>

#### 1. **Manage External Dependencies**

For a local setup, ensure the following are installed:

- **Dana Programming Language** ([Version 251] - [Installation Guide](http://www.projectdana.com/dana/guide/installation))
- **Python** 3.7 - [Download here](https://www.python.org/downloads/)
- **Perl** 5 - [Download here](https://www.perl.org/get.html)

#### 2. **Familiarize with the Project Structure**

Here's an overview of the EWS project directories:

- **Docker**: Houses the Dockerfile and linked scripts.
- **make_scripts**: Contains essential scripts for project compilation.
- **pal**: Core Dana codebase for the EWS API.
- **python_scripts**: Python helpers to communicate with EWS.
- **repository**: Web server components.
- **ws_clients**: Workload scripts compliant with HTTP 1.0.

#### 3. **Compile the EWS Codebase**

To begin, switch to the `emergent_web_server` directory and run:

```bash
dana make.dn
dana make.o
```

For Unix-based systems (Linux/MacOS):

```bash
dana make.o -l all
```

#### 4. **Launch EWS**

For different components:

- **Standard Emergent System**:
  ```bash
  cd emergent_web_server/pal/
  dana -sp ../repository EmergentSys.o
  ```

- **Interactive Emergent System**:
  ```bash
  cd emergent_web_server/pal/
  dana -sp ../repository InteractiveEmergentSys.o
  ```

- **Clients**:
  Navigate to `emergent_web_server/ws_clients/` and choose:

  ```bash
  dana ClientTextPattern.o
  ```

  OR

  ```bash
  dana ClientImagePattern.o
  ```

---

Remember to frequently check for updates to ensure optimal performance and take advantage of new features. Enjoy your experience with the EWS!
