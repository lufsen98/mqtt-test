# MQTT-BROKER


# image directory

## includes
**Dockerfile** 
for building an interactive development
environment with C/C++ tools, emulating a Raspberry Pi
Zero system.
see [Dockerfile](...) for the tools pre installed with the image. 

**Compose File**

Compose file to create network and containers

if you want to create more then 1 container check the comments in the compose.yaml file.

1883 port only needed for container running the broker

**MQTT-BROKER**

will be added steps to start the docker file with the right configs to be able to take connections from other containers on the same network
