---
layout: post
title: Containers
categories:
  - Containers
---
* [Docker](Docker.md)
  * [Windows Docker port binding failure - Listing reserved network port ranges](https://github.com/docker/for-win/issues/3171):   
  `netsh interface ipv4` show excludedportrange protocol=tcp`
  * Kubernetes cluster:  
  I think this is a container-of-containers, e.g. redis container, es container, pg container, openldap container, etc.
  * Docker Volumes:  
  Apparently you can use a Volume to overcome file-case issues when a Linux container is building source files hosted on the Windows host.
  * [Podman](https://developers.redhat.com/blog/2019/02/21/podman-and-buildah-for-docker-users/#:~:text=You%20install%20Podman%20instead%20of,a%20different%20place%20than%20Docker) and [Podman on Github](https://github.com/containers/libpod/blob/master/docs/tutorials/podman_tutorial.md):  
  The biggest problem with Docker is the use of a single daemon process. All child processes are owned by this process, i.e. this a single point of failure. There are also security implications. Podman has addressed many of these problems. The commands you are familiar with in Docker work the same for Podman. **The claim is that if you have existing scripts that run Docker you can create a docker alias for podman and all your scripts should work (alias docker=podman)**.  
  Installation on Red Hat 8.1: `yum install podman` (Note: you don't need Docker installed to use Podman). 
    * Detach from an interactive container:  
    Holding-down Ctrl, press P and then Q.  
    To re-attach to the detached interative container:    
    `podman attach web_test`     
    * [List containers in a pod](https://developers.redhat.com/blog/2019/01/15/podman-managing-containers-pods/#:~:text=You%20can%20add%20a%20container,use%20of%20*%E2%80%93pod*.):  
    `podman pod ps`  
    `podman ps -a --pod`   
    * Remove pod, even if it contains containers (see "man podman-pos-rm"):  
    `podman pod rm -a -f`  
    * Run command "ps" in a container:  
    `podman exec web_test ps`  
    * View log in a container:  
    **Note:** Anything that the program writes to stdout or stderr will be recorded here.  
    `podman logs web_test`  
    * [Podman Networking between containers](https://www.redhat.com/sysadmin/container-networking-podman):   
      **Note:** The Docker "--link" option to network containers is no longer supported (see [here](https://docs.docker.com/network/links/)).  
      * The simplest container networking method - using a "Pod":  
      **Note:** When using a pod, each container has the same IP address, i.e. everything runs in the same "localhost".  
      **Note:** You can run this as a non-root user (aka "rootless").  
      Example:    
      `podman pod create --name=mypod`  
      `podman run --detached --name=web --pod=mypod nginx:latest`  
      `podman run --interative --tty --pod=mypod --name=web_test busybox:latest /bin/sh`    
      `# wget -O - http://localhost:80`  
      (This example is based on page 18 of DockerInAction).  
      **Note:** Grouping containers into a pod also enables you to manage them as one, `podman pod stop|start`.  
      * Using IP apddress:  
      **Note:** This only works as root user (aka "rootfull" containers), because network device association cannot be achieved unless running as root.  
      `# podman run -dt --rm --name web nginx:latest`  
      `# podman inspect web | grep IPAddress`  
      `"IPAddress": "10.88.0.2"`  
      From the host:  
      `# curl http://10.88.0.2:80`  
      `# podman run -it --name shell nginx:latest /bin/sh`  
      From inside the "shell" container:  
      `# curl http://10.88.0.2:80`  
    *  The order that the Docker/Podman container registries are queried:  
    `/etc/containers/registries.conf`  
    
