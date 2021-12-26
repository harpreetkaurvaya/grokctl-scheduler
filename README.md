# fix-node-scheduler

### Installation

I already upload docker image to docker.io. You can check [here](https://hub.docker.com/repository/docker/grokctl/fix-node-scheduler).
```bash
kubectl apply -f grokctl-fix-node-scheduler-resources.yaml
```

### Configure nodes

#### You need to labels your nodes which you want statically attach you pod. It is always scheduel this node.
```bash
kubectl label node your_nodename web-0=true #web-o is web statefulset application. You can see example in repository.
kubectl label node your_other_nodename web-1=true
```

### Install statefulset application

#### You need to set schedulerName=`fix-node-scheduler` because we have our scheduler now. Its name is fix-node-scheduler. I already set in example statefulset resource.
```bash
kubectl apply -f example-statefulset.yaml
```

#### When you apply example statefulset application you will see web-0 and web-1 scheduled to your chosen nodes. 
