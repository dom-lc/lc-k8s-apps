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
* Rename the directory you just copied under ```./charts``` to match your new application name
* Fill in the application.yaml with your apps's name and branch name
* Fill in the name and description in the ```Chart.yaml``` file
* If your chart is importing an exixsting application chart, import it in your ```Chart.yaml```'s dependency section
* add a ```template``` folder and define your custom charts yaml templates if required
* Set all the values in the surveillance-green.yaml

</br></br>
If you are unsure whatis the version to use for your dependency, youcan refer to the online official tool's repository or add it to your local repositories an list the versions with:

```
helm search repo repository-name/application-name --versions
```

</br></br>
If your application requires terraform managed infrastructure (ex: nodepool, database, storage account,...), Please refer to the [lc ingrastructure repository](https://github.com/dom-lc/lc-k8s-infra.git) in order to crate and manage your terraform config.

## Update/Upgrade an application

kubectl -n argocd patch application actions-runner-system -p '{"metadata":{"finalizers":[]}}' --type=merge