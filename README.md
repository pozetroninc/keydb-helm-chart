KeyDB
=====
A Helm chart for a replicated [KeyDB](https://keydb.dev/) cluster optionally with a Redis module loaded.

## Install

```
$ helm repo add pozetron https://www.pozetron.com/helm
$ helm search repo pozetron
$ helm install my-keydb pozetron/keydb
```

## Chart Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| replicaCount | int | `3` | Number of Pods to create. |
| keydb.password | string | `"thanks@jdsully"` | Every deployment should have one. |
| keydb.activereplica | string | `"yes"` | ["Active-Active" Replication](https://docs.keydb.dev/docs/active-rep/) |
| keydb.multimaster | string | `"yes"` | ["Multiple-Master" Replication](https://docs.keydb.dev/docs/multi-master/) |
| keydb.appendonly | string | `"no"` | Append Only File [persistence](https://docs.keydb.dev/docs/persistence/) |
| keydb.module | string | `nil` | A custom [Redis Module](https://redis.io/modules) to load e.g. "redistimeseries.so" |
| keydb.threads | int | `2` | Number of worker threads serving requests. This number should be related to the performance of your network hardware, not the number of cores on your machine. |
| keydb.port | int | `6379` |  |
| keydb.extraArgs | object | `{}` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"pozetroninc/keydb"` | The Docker (Hub) repository for the image. |
| image.tag | string | `""` | The version of KeyDB to install e.g. "v5.3.3" |
| persistence.enabled | bool | `false` |  |
| persistence.size | string | `1G` | How much persistent storage for each pod. |
| persistence.accessMode | string | `ReadWriteOnce` | The [storage class](https://kubernetes.io/docs/concepts/storage/storage-classes/) |

### Contributors

Special thanks to: [Hazim](https://github.com/hazim1093) 
