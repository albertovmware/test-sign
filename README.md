# Image signing and verification for kubernetes clusters

For this exercise, Harbor was used as container registry.
It was deployed in a ubuntu 20.04 VM after generate ssl certificates with certbot.
The harbor.yml file with the values for the deployments is at harbor folder.

The folder connaisseur contains the helm chart for the connaisseur instance that is with the namespaced validation running in validate mode

The folder connaisseurd contains the helm chart for the connaisseur instance that is with the detection mode.

To let both work together, I changed the app.name in the chart.yaml of connaisseurd, to fix colisions in roles

To deploy the instances:
```console
helm install connaisseur helm --atomic --create-namespace --namespace connaisseur
```
```console
helm install connaisseurd helm --atomic --create-namespace --namespace connaisseurd
```

To test the image deployment on the cluster, go through actions, and run the workflow run-images.
![](https://github.com/albertovmware/test-sign/blob/main/img/github.gif)
