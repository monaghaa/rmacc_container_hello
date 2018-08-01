Bootstrap:docker  
From:ubuntu:latest

%labels
MAINTAINER Andy M

%environment
HELLO_BASE=/code
export HELLO_BASE

%files
#copy files into container /opt directory
     mymessage.txt /opt

%post  
echo "This section is performed after you bootstrap to build the image."  
apt-get update
apt-get install -y vim nano 
mkdir -p /code  
echo '#!/bin/bash' > /code/hello.sh
cat /opt/mymessage.txt >> /code/hello.sh
chmod u+x /code/hello.sh  

%runscript
echo "This is executed when you run the image!" 
exec /bin/bash $HELLO_BASE/hello.sh "$@"  

%help
#This provides help to users of the container

A base Ubuntu Singularity container with a sample bash script
To run the example script:
>singularity run <image_name>.img" 

%test
# Sanity check that the container is operating
# Check bash version
    bin/bash --version
