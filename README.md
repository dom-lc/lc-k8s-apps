# lc-k8s-apps


Repository that mocks the lc-k8s-apps.</br></br>

This repo contains the charts for our aks applications.</br>
They are deployed by an applicatonset residing in the [lc-k8s-apps-deployments](https://github.com/dom-lc/k8s-apps-deployments.git) </br></br>
*Note that this repository will be used to demonstrate concepts and does not follow the best security practices.*

## Structure

All of our cluster apps resides each in their own directory under ```charts```. Inside each app's directory we can find the Chart and values files for each cluster.</br>

## Create a New application



### Versioning
Versioning is done by automatically with release please.</br>
You have to add these lines to the ```packages:``` in the [release-please-config.json](./release-please-config.json) :

```
 "charts/<your-chart-name>": {
            "package-name": "<your-chart-name>",
            "changelog-path": "CHANGELOG.md"
        }
```

Also tag the commit so that your version will not be bumped on the firstcommit with ```git tag chart-name-v0.1.0``` then ```git push origin chart-name-v0.1.0```. </br>
then push the code with the as release like : ```git commit -m "feat(chart-name): initial chart" -m "as-release 0.1.0"```. </br>
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