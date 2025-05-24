# lc-k8s-apps


Repository that mocks the lc-k8s-apps.</br></br>

This repo contains the charts for our aks base applications, meaning that these apps will be running by default on each clusters and we should all agree that no one except the cluster management team (LC) should have access to this repository.</br>
They are deployed by an applicatonset using a helm git generator that we define in our [applicative infrastructure repository](https://github.com/dom-lc/lc-k8s-infra).</br></br>
*Note that this repository will be used to demonstrate concepts and does not follow the best security practices.*

## Structure

All of our "core" cluster apps resides each in their own directory under ```charts```. Inside each app's directory we can find the Chart and values files for each cluster.</br></br>
Consider you could have put your values in a separate repository as LC uses lc-k8s-apps-values. I wanted here to showcase the use of the applicationset for all our core apps but the structure is "modulable".

## Create a New application

In order to create a new application:
* copy the ```./new-app``` directory and paste int under ```./charts```.
* Rename 

## Update/Upgrade an application