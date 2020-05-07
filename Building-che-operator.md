# Building Che-Operator
The instructions provided below specify the steps to build [Che-Operator](https://github.com/eclipse/che-operator) version 7.12.1 on Linux on IBM Z for following distributions:
*    RHEL 7.7

### Prerequisites:
*   Kubernetes. For deploying Che-Operator, you must have Kubernetes installed. Download Kubernetes binary from [Kubernetes](https://github.com/kubernetes/kubernetes/releases).
*   Docker packages are provided for RHEL (7.5 or higher) in their respective repositories. Instructions for installing Docker can be found [here](http://www.ibm.com/developerworks/linux/linux390/docker.html). More information about Docker CE can be found [here](https://docs.docker.com/install/).
*   At the time of creation of these build instructions Che-Operator was verified using Kubernetes version 1.15.0 and Docker 18.06.

_**General Notes:**_
*   _When following the steps below please use a standard permission user unless otherwise specified._
*   _A directory `/<source_root>/` will be referred to in these instructions, this is a temporary writable directory anywhere you'd like to place it._

### Step 1: Install dependencies
```
export SOURCE_ROOT=/<source_root>/
```
*    RHEL 7.7
     ```
     sudo yum install -y git 
     ```
     
### Step 2: Build Che-Operator
```
cd $SOURCE_ROOT
git clone https://github.com/eclipse/che-operator.git
cd che-operator/
git checkout 7.12.1
```

*	Build che-operator image for s390x
```
cd $SOURCE_ROOT/che-operator
docker build -t che-operator:7.12.1 .
```
*	Deploy che-operator on Kubernetes cluster
```
./build_deploy_local.sh $workspace
````
### References:
[Che-Operator GitHub](https://github.com/eclipse/che-operator)
