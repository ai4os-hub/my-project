# My  project
[![Build Status](https://jenkins.services.ai4os.eu/buildStatus/icon?job=AI4OS-hub/my-project/main)](https://jenkins.services.ai4os.eu/job/AI4OS-hub/job/my-project/job/main/)

My project to test child template

This is a container that will run the my-project application leveraging the DEEP as a Service API component ([DEEPaaS API](https://github.com/ai4os/DEEPaaS)). The application is based on **ai4oshub/ai4os-image-classification-tf** module.

    
## Running the container

### Directly from Docker Hub

To run the Docker container directly from Docker Hub and start using the API, simply run the following command:

```bash
$ docker run -ti -p 5000:5000 -p 6006:6006 -p 8888:8888 ai4oshub/my-project
```

This command will pull the Docker container from the Docker Hub [ai4oshub](https://hub.docker.com/u/ai4oshub/) repository and start the default command (`deepaas-run --listen-ip=0.0.0.0`).

**N.B.** For either CPU-based or GPU-based images you can also use [udocker](https://github.com/indigo-dc/udocker).

### Building the container

If you want to build the container directly in your machine (because you want to modify the `Dockerfile` for instance) follow the following instructions:
```bash
git clone https://github.com/ai4os-hub/my-project
cd my-project
docker build -t ai4oshub/my-project .
docker run -ti -p 5000:5000 -p 6006:6006 -p 8888:8888 ai4oshub/my-project
```

These three steps will download the repository from GitHub and will build the Docker container locally on your machine. You can inspect and modify the `Dockerfile` in order to check what is going on. For instance, you can pass the `--debug=True` flag to the `deepaas-run` command, in order to enable the debug mode.


## Connect to the API

Once the container is up and running, browse to http://0.0.0.0:5000/ui to get the [OpenAPI (Swagger)](https://www.openapis.org/) documentation page.


## Project structure
```
├─ Dockerfile             <- Describes main steps on integration of DEEPaaS API and
│                            <your_project> application in one Docker image
│
├─ Jenkinsfile            <- Describes basic Jenkins CI/CD pipeline
│
├─ LICENSE                <- License file
│
├─ README.md              <- README for developers and users
│
├── .sqa/                 <- CI/CD configuration files
│
└─ metadata.json          <- Defines information propagated to the AI4OS Hub
```

You can validate the `metadata.json` before making a git push using:
```shell
pip install ai4-metadata-validator
ai4-metadata-validator metadata.json
```
