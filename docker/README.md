Example using Docker
==============

[German / Deutsch](LIESMICH.md)

This project creates a VM with the application in a Docker
container.


# Vagrant

Vagrant starts a VM, installs Docker and then runs the Docker
Container on the VM.

To run:

- Install Vagrant as discussed at
  http://docs.vagrantup.com/v2/installation/index.html
- Install Virtual Box from https://www.virtualbox.org/wiki/Downloads
- Change to the directory containing this README.md and run `vagrant
   up`

The result should be:

- A new VirtualBox VM is fired up by Vagrant
- Docker is installed in the VM
- You can access the application at http://localhost:8090/

# Docker Machine

Docker Machine installs Docker on a VM. Then other tools like Docker
Compose can use Docker as if it was running on a local machine.

To run:

- Install Virtual Box from https://www.virtualbox.org/wiki/Downloads
- Install Docker, see https://docs.docker.com/installation/
- Install Docker Machine, see https://docs.docker.com/machine/#installation
- Execute `docker-machine create  --virtualbox-memory "4096" --driver
  virtualbox dev` . This will create a new environment called `dev`with Docker
  Machine. It will be virtual machine in Virtual Box with 4GB RAM.
  - Execute `eval "$(docker-machine env dev)"` (Linux / Mac OS X) or
    `docker-machine.exe env --shell powershell dev` (Windows,
    Powershell) /  `docker-machine.exe env --shell cmd dev` (Windows,
    cmd.exe). Now the docker tool will use the newly created virtual
    machine as environment.
- Change to the directory this directory and run
  - `docker build -t java java`
  - `docker build -t user-registration user-registration`
  - `docker run -p 8080:8080 user-registration docker run -p 8080:8080
    -d user-registration`

The result should be:

- A new VirtualBox VM with a Docker installation
- The application running on the VM

You can find the IP adress of the machine using `docker-machine ip
dev` . Tomcat is available at port 8080.
