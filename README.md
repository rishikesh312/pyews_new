## pyEWS: Python Interface for the Emergent Web Server (EWS)

### **Emergent Web Server (EWS) Overview**:

**1. Setting Up**:
- Docker: Ensure Docker is installed and configured on your machine. If not, follow the instructions at Docker's Get Started page.

**2. EWS Setup**:
```bash
# Running the EWS Container:
docker run --name=ews -p 2011-2012:2011-2012 -d robertovrf/ews:1.0
# Check the Running Containers:
docker container ls
# Accessing the EWS Container Terminal:
docker exec -it ews bash
# Executing EWS Tool inside the Container:
dana -sp ../repository InteractiveEmergentSys.o
```

**3. Installation**:
```bash
pip install dist/pyews-1.0.3-py3-none-any.whl
```
**4. Testing**:
Run the python file in examples folder to check if everything it is working
```bash
#windows
python ./examples/demo.py
#linux
python3 ./examples/demo.py
```

**5. Usage**:

- Ensure the Emergent Web Server is running.
- Set the IP of the EWS using the settings dictionary in global_vars.py.
- Use the `initialize_server` function from `server_interface.py` at the beginning of any scripts using this package unless the EWS is already initialized.


### **Additional Resources**:
- For troubleshooting with EWS, check logs in `emergent_web_server/pal/em.log`.
- Visit the EWS repository [EWS repository](https://github.com/rishikesh312/emergent_web_server_new) for more details.

