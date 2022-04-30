
## image-syncer
sync k8s.gcr.io docker images to dockerhub or aliyun registry use [aliyun image-syncer](https://github.com/AliyunContainerService/image-syncer) and github action!

### Getting Started

1. Fork this repo, then create your self secrets:

    1. `Settings`-->`Secrets`-->`New Repository Secrets`
    2. Add your `DOCKERHUB_USERNAME` and `DOCKERHUB_PASSWORD` key values.

![githubaction01.png](https://i.loli.net/2021/08/21/TjN76FtngG5Dehf.png)

2。 Add registry to `images:` that you want to sync:

format
```
auth:
  <src or destation registry url>
    username: DOCKERHUB_USERNAME
    password: DOCKERHUB_PASSWORD
images:
   <src registry>: <destation registry>
```

DO NOT CHANGE DOCKERHUB_USERNAME and DOCKERHUB_PASSWORD ,it will be replaced by sed command.

For example

```yaml
auth:
  registry.hub.docker.com:
    username: DOCKERHUB_USERNAME
    password: DOCKERHUB_PASSWORD
images:
  k8s.gcr.io/metrics-server/metrics-server: DOCKERHUB_USERNAME/metrics-server
  k8s.gcr.io/ingress-nginx/controller: DOCKERHUB_USERNAME/ingress-nginx-controller
  k8s.gcr.io/git-sync/git-sync: DOCKERHUB_USERNAME/git-sync
  gcr.io/kaniko-project/executor:debug,latest: DOCKERHUB_USERNAME/kaniko-executor
  k8s.gcr.io/kube-state-metrics/kube-state-metrics: DOCKERHUB_USERNAME/kube-state-metrics
  k8s.gcr.io/sig-storage/nfs-subdir-external-provisioner: DOCKERHUB_USERNAME/nfs-subdir-external-provisioner
  k8s.gcr.io/prometheus-adapter/prometheus-adapter: DOCKERHUB_USERNAME/prometheus-adapter
```

3. Check action logs

![githubaction02.png](https://i.loli.net/2021/08/21/OkXVWY8pN6Foat7.png)

4. After synced, check your images


