# Gitea

*Git with a cup of tea*
*A painless, self-hosted Git service*

## Resources

* [Homepage](https://gitea.com/)
* [Documentation](https://docs.gitea.io/en-us/)
* [Container Specific Documentation](https://docs.gitea.io/en-us/install-with-docker/)

## kustomization

This kustomization will create the following Kubernetes Resources

* A [Namespace](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/) named `gtitea`
  in which the whole application resides.
* Resources for the main server:
    * A [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) + [Service](https://kubernetes.io/docs/concepts/services-networking/service/) both named `gitea`.
    * [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) named `gitea`
      in which gitea persists its data like repositories and LFS files.
    * An example [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/) + [Secret](https://kubernetes.io/docs/concepts/configuration/secret/) both named `gitea`.
* Resources for the database:
    * A [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) + [Service](https://kubernetes.io/docs/concepts/services-networking/service/) both
      named `gitea-postgres`.
    * A [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) named `gitea-postgres` in which the database is persisted.
    * An example [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/) + [Secret](https://kubernetes.io/docs/concepts/configuration/secret/) both named `gitea-postgres`.

## Configuration

The application can be configured through the generated ConfigMaps and Secrets as they get injected as
environment variables.

*Note: The main server backend automatically configures its DB_\* environment variables based on the 
configuration of the postgre server.*
