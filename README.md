# Security Onion Airgap Update
This script will allow you to download updated docker containers and OS patches from the internet and install them on Securty Onion machines running on an airgap network.   

## Terms
    - Gateway Node:  This node is responible for downloading the latest Docker Images and Operating System Patches.  It must be connected to the internet. 
    - Master Node: This node will is the Master Node running on the airgap network and the first node that needs to be updated.
    - Sensor Node:  This node is Heavy, Storage and Forward Nodes on the airgap network.
    - so-acng: A apt-cacher-ng docker container that will run on the Gateway and Master Nodes. This container will cache the requried Operating System packages.
    -so-registry:  A docker registry container that will run on the Gateway and Master Nodes.  This will  store and let you distribute Docker images.

## Important 
To ensure that all dependancies are downloaded it is important to ensure that the Gateway Node is running the same major and minor versions of Security Onion as the Master Server.  Example.  If you built the Master Node running in the airgap network using the Security Onion 16.04.5.2, you must use that same ISO version OR older on the Gateway Node.  
## Updating the Gateway Node
Updating the Gateway Node is a two step process.  Step one will install apt-cacher-ng and update the Operating System.  Step two will pull the most recent docker images from docker hub.

1. Download the latest version of the so-airgap repo from Github on the Gateway node.
 
      `git clone https://github.com/bryant-treacle/securityonion-airgap.git`
    
2. Navigate to the securityonion-airgap directory.
      
      `cd securityonion-airgap`
      
3. Make so-airgap-update an executable file

      `sudo chmod +x so-airgap-update`
      
4. Launch so-airgap-update script
    
      `sudo ./so-arigap-update`
      
5. From the option menu, choose Gateway Node and Step_one when prompted and reboot when complete.
6. After reboot, launch so-airgap-update script
7. From the option menu, Choose Gateway Node and Step_two when prompted.
8. Once complete, copy the content on securityonion-airgap folder and /opt/airgap/save to the Master Node on the airgap network.

## Updating the Master Node


