# lc-k8s-apps


Repository that mocks the lc-k8s-apps.</br></br>

This repo contains the charts for our aks applications.</br>
They are deployed by an applicatonset residing in the [lc-k8s-apps-deployments](https://github.com/dom-lc/k8s-apps-deployments.git) </br></br>
*Note that this repository will be used to demonstrate concepts and does not follow the best security practices.*

## Structure

All of our cluster apps resides each in their own directory under ```charts```. Inside each app's directory we can find the Chart and values files for each cluster.</br>

## Create a New application

To create a new applications, you can copy the folder ```./templates/new-app``` to ```./charts``` and rename the folder your desired application name.</br>
Then , edit the ```<your-apps-name>/Chart.yaml``` to set your desired values and dependencies.

### New apps validations and testing

Before doing a PR for your new application, you have to ensure your Chart can successfuly build and be deployed.</br>
To do so, we can validate our chart and test our deployment using the ```Test New App``` workflow of the [lc-k8s-apps-deployments](https://github.com/dom-lc/k8s-apps-deployments.git) repository.</br>
Read the README of the apps deployments repository for more details on the process of testing the new application. When all tests have been made and your app is ready to deploy, follow the next steps.

### New apps PR

### Helm Values

When your values are all set, copy them to the [lc-k8s-apps-values](https://github.com/dom-lc/k8s-apps-values.git) under a folder by your apps name. You can find more instructions in the README of the apps values repository if needed.

### Versioning
Versioning is done by automatically with release please.</br>
You have to add these lines to the ```packages:``` in the [release-please-config.json](./release-please-config.json) :

```
 "charts/<your-chart-name>": {
            "package-name": "<your-chart-name>",
            "changelog-path": "CHANGELOG.md"
        }
```

Push the code with the as release like : ```git commit -m "feat(chart-name): initial chart" -m "release-as: 0.1.0"```. </br>
You then need to approve the PR created by release-please sio that your versioning is applied.

For the PR, use the naming convention as in the documentation.</br>
Accept the release-please PRs.
</br></br>
If your application requires terraform managed infrastructure (ex: nodepool, database, storage account,...), Please refer to our [Infrastructure Repository](https://github.com/dom-lc/lc-k8s-infra) in order to crate and manage your terraform configs.

## Versioning & Tagging

## Update/Upgrade an application

## References

* Helm's Official Documentation
* Release-Please Official Page