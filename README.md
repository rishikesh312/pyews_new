Reference Implementation for EWS System

### Prerequisites

- Ensure Docker is installed and set up. [Docker Installation Guide](https://www.docker.com/get-started).

---

### Docker-Based Execution

#### 1. **Run EWS Container from Docker Hub**

```bash
docker run --name=ews -p 2011-2012:2011-2012 -d robertovrf/ews:1.0
```

#### 2. **Verify EWS Container is Running**

```bash
docker container ls
```

#### 3. **Access EWS Container Terminal**

```bash
docker exec -it ews bash
```

Inside the EWS container:

#### 4. **Navigate to the Specified Directory**

```bash
cd emergent_web_server/pal/
```

#### 5. **Launch the Interactive Emergent System Tool**

```bash
dana -sp ../repository InteractiveEmergentSys.o
```

#### 6. **Interacting with EWS**

- Access help: `sys> help`
- List available configurations: `sys> get_all_configs`
- Get current configuration: `sys> get_config`
- Set configuration: `sys> set_config [ID]` (Replace [ID] with the desired configuration ID.)
- Access the web server: Open a browser and go to http://localhost:2012/.
- View available server resources: Check `emergent_web_server/repository/htdocs`.

#### 7. **Perception and Learning**

- Get performance data: `sys> get_perception`
- Use learning algorithm: `sys> learn`

For the learning algorithm:

- Recommended observation window: 5000ms
- Recommended exploration threshold: 3
- Recommended number of rounds: 52

Execute learning algorithm after setting the values.

---

### Native Installation (For Users Preferring Local Set Up)

#### 1. **External Dependencies**

- Install Dana Programming Language [Version 251]. [Installation Guide](http://www.projectdana.com/dana/guide/installation).
- Install Python 3.7 from [Python Downloads](https://www.python.org/downloads/).
- Install Perl 5 from [Perl Downloads](https://www.perl.org/get.html).

#### 2. **Project Structure**

- **Docker**: Contains the Dockerfile and associated scripts.
- **make_scripts**: Scripts required to execute 'make.dn' for compilation.
- **pal**: Main Dana code for EWS API.
- **python_scripts**: Python scripts to interact with EWS API.
- **repository**: Components of the web server.
- **ws_clients**: HTTP 1.0 client scripts for workload.

#### 3. **Compiling EWS Project**

Navigate to `emergent_web_server` folder:

```bash
dana make.dn
dana make.o
```

For Linux/MacOS:

```bash
dana make.o -l all
```

#### 4. **Executing EWS**

For **EmergentSys.o**:

```bash
cd emergent_web_server/pal/
dana -sp ../repository EmergentSys.o
```

For **InteractiveEmergentSys.o**:

```bash
cd emergent_web_server/pal/
dana -sp ../repository InteractiveEmergentSys.o
```

For **Clients**:

```bash
cd emergent_web_server/ws_clients/
dana ClientTextPattern.o
```

OR

```bash
dana ClientImagePattern.o
```

This reference implementation provides a comprehensive step-by-step guide to run and interact with the EWS system using either Docker or a native installation.
