## **pyEWS: A Python Interface for the Emergent Web Server (EWS)**

### **1. Overview**

`pyEWS` is an advanced Python interface designed to facilitate interaction with the REST API of the Emergent Web Server (EWS). This document serves as a comprehensive guide for setting up and efficiently using the `pyEWS` system.

### **2. Prerequisites**: 

#### **Docker Configuration**: 
  - It's imperative to have Docker properly installed and configured on your machine before proceeding with the subsequent steps.
  - For those unfamiliar with Docker, refer to the official [Docker Documentation](https://www.docker.com/get-started) for detailed installation instructions.

### **3. EWS Configuration via Docker**:

To set up the Emergent Web Server using Docker, adhere to the following sequence of commands:

```bash
# Initiate the EWS container:
docker run --name=ews -p 2011-2012:2011-2012 -d robertovrf/ews:1.0

# Verify the active status of the initiated container:
docker container ls

# Access the terminal interface of the EWS container:
docker exec -it ews bash

# Activate the EWS toolkit within the container:
dana -sp ../repository InteractiveEmergentSys.o
```

### **4. Native EWS Installation Procedure**:

For those opting for a non-containerized approach, the following instructions detail a native installation process:

1. **Required Dependencies**:
    - **Dana Programming Language**: Adhere to the official [installation guide](http://www.projectdana.com/dana/guide/installation).
    - **Python 3.7**: Procure from the [official Python website](https://www.python.org/downloads/).
    - **Perl 5**: Access from the [official Perl website](https://www.perl.org/get.html).

2. **Compilation Protocol**:
    - Commence by compiling the `make.dn` tool:
        ```bash
        dana make.dn
        ```
    - Subsequently, execute `make.o` with appropriate options:
        ```bash
        dana make.o -l all
        ```

3. **EWS Native Execution**:
    - Trigger the `EmergentSys.o`:
        ```bash
        dana -sp ../repository EmergentSys.o
        ```
    - Activate the `InteractiveEmergentSys.o`:
        ```bash
        dana -sp ../repository InteractiveEmergentSys.o
        ```

4. **Client Script Execution**:
    - As an exemplar, the following can be executed:
        ```bash
        dana ClientTextPattern.o
        ```
        
---

### **5. pyEWS Installation Procedure**:

Install the pre-compiled version of `pyEWS` utilizing pip:

```bash
pip install dist/pyews-1.0.3-py3-none-any.whl
```

### **6. pyEWS Utilization**:

- **Validity Test**:
  - To ensure a successful installation, execute the provided Python script located in the examples directory:
    ```bash
    # Windows platform:
    python ./examples/demo.py

    # Linux/Mac platforms:
    python3 ./examples/demo.py
    ```

- **Operational Guidelines**:
  - Ensure the continuous operation of EWS.
  - Make sure to set the IP of the EWS using the settings dictionary found in global_vars.py
  - Before you run any script that uses the `pyEWS` package, start with the `initialize_server` function from the `server_interface.py` file.
  - 
### **7. Troubleshooting & Additional Resources**:

- For EWS-related discrepancies, consult the logs located at `emergent_web_server/pal/em.log`.
- A more granular understanding can be obtained from the official [EWS repository](https://github.com/rishikesh312/emergent_web_server_new).
