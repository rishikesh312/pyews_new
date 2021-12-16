# py-ews
Python Interface to the emergent_web_server
1. Ensure the Emergent Web Server is running.

2. Make sure to set the IP of the EWS using the settings dictionary found in global_vars.py

3. Use the initialize_server function found in the server_interface.py prior at the beginning of any scripts using this package. Unless the EWS is already initialized.

# example script
from py-ews.server_interface import ewsRESTInterface as eRI
from py-ews.global_vars import settings

settings["IP"] = "http://localhost:2011/"
eRI.initialize_server({"comp":"../repository/TCPNetwork.o"},{"exp":"|../metacom/monitoring/proxies/HTTPProxy.o|*(*:http.handler.GET.HTTPGET[0]:*)|"})

eRI.get_all_configs()