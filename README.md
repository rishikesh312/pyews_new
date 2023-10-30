## pyEWS: Python Interface for the Emergent Web Server (EWS)

### **Emergent Web Server (EWS) Overview**:

**1. Setting Up**:
- Docker: Ensure Docker is installed and configured on your machine. If not, follow the instructions at Docker's Get Started page.

**2. Quick Start with Docker**:
```bash
# Running the EWS Container:
docker run --name=ews -p 2011-2012:2011-2012 -d robertovrf/ews:1.0
# Check the Running Containers:
docker container ls
# Accessing the EWS Container Terminal:
docker exec -it ews bash
```

**3. Installation**:
```bash
pip install dist/pyEWS-<version>.whl
```

**3. Package Structure**:

- **global_vars.py**:
Holds global configurations for the `pyEWS`.
```python
settings = {
    "Initialized": False,
    "IP": "localhost:2012",  # Set the IP address of the EWS
    "main_component_path": None,  # Path to the main component
    "proxy_JSON": None
}
```

- **server_interface.py**:
Interface functions to communicate with the Emergent Web Server.
```python    def initialize_server(main_component_path, proxy_JSON):
        """Initializes the EWS prior to its usage."""
        if(not settings["Initialized"]):
            settings["main_component_path"] = main_component_path
            ewsRESTInterface.set_main({"comp":settings["main_component_path"]})

            settings["proxy_JSON"] = proxy_JSON
            ewsRESTInterface.add_proxy(settings["proxy_JSON"])

            settings["Initialized"] = True
        else:
            print("Server already initialized")
```

**3. Usage**:

- Ensure the Emergent Web Server is running.
- Set the IP of the EWS using the settings dictionary in global_vars.py.
- Use the `initialize_server` function from `server_interface.py` at the beginning of any scripts using this package unless the EWS is already initialized.

**4. Sample Script (main.py)**:
```python
from pyEWS import server_interface

def main():
    response = server_interface.initialize_server()
    if response.get("status") == "success":
        print("EWS initialized successfully!")
    else:
        print("Failed to initialize EWS. Please ensure it's running and accessible.")

if __name__ == "__main__":
    main()
```

### **Additional Resources**:
- A demo Python script showcasing functionality and implementing an epsilon-greedy algorithm is included in the `examples/` directory.
- For troubleshooting with EWS, check logs in `emergent_web_server/pal/em.log`.
- Visit the official [EWS repository](https://github.com/robertovrf/emergent_web_server) for more details.

This combined reference provides an overview of EWS and offers a foundational setup and usage guide for the `pyEWS` Python interface. Users are encouraged to review the official documentation and examples to gain a deeper understanding and effectively leverage the full suite of features.
