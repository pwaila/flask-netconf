# Introduction

A really simple web app to generate and send simple netconf GET requests and to generate a sample Python script that uses ncclient.

# Installation

Please run the script ```start.sh```. This will create a virtualenv, attempt to load required dependencies, and start the web application. Note that the dependencies may require native libraries to be installed in the underlyinging environment. Thes native library dependencies have not yet been fully documented.

Once the start.sh script has completed successfully, you may open the link [http://127.0.0.1:8080/netconf](http://127.0.0.1:8080/netconf)!

Please note that this web application has no security as part of its function, but neither does it cache credentials, and any device communication requires the end-user to provide credentials.

# Now With Docker

Optionally, you may also choose to package flasj-netconf as a Docker container. This has not been tested much, but isn't seen to fail. Please ensure you have Docker installed, and then you can do the following while in the flask-netconf top-level directory.

1. Create the Container:

    ```
    docker build -t flask-netconf .
    ```

1. Run the Container (port 8000 is the exposed port, modify the [Dockerfile](Dockerfile) to change):

    ```
    docker run -d --name FLASK_NETCONF -p <host-port>:8000 flask-netconf
    ```

1. Browse to [`http://localhost:8000`](http://localhost:8000)

If you have prevously used this web app running natively with local virtual devices, say XRv or CSR1Kv in a vagrant box, with NETCONF ports mapped to local ports, please remember that the virtual devices are **not** visibile on `127.0.0.1` to the container, and must be accessed via one of your host's actual IP addresses.
