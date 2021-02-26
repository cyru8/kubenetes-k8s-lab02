# kubenetes-k8s-lab02
# kubectl create or apply -f deployment.yaml
# automationmgr@master1:~/workbench/kubenetesbench/kubenetes-k8s-lab02$ kubectl get deployment
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
webapp01   0/1     1            0           17s


automationmgr@master1:~/workbench/kubenetesbench/kubenetes-k8s-lab02$ kubectl describe deployment webapp01
Name:                   webapp01
Namespace:              default
CreationTimestamp:      Thu, 25 Feb 2021 23:08:02 -0800
Labels:                 app=webapps
Annotations:            deployment.kubernetes.io/revision: 1
Selector:               app=webapps
Replicas:               1 desired | 1 updated | 1 total | 1 available | 0 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  25% max unavailable, 25% max surge
Pod Template:
  Labels:  app=webapps
  Containers:
   webapp01:
    Image:      katacoda/docker-http-server:latest
    Port:       80/TCP
    Host Port:  0/TCP
    Limits:
      cpu:     100m
      memory:  100Mi
    Requests:
      cpu:        100m
      memory:     100Mi
    Liveness:     tcp-socket :80 delay=5s timeout=5s period=10s #success=1 #failure=3
    Readiness:    http-get http://:80/_status/healthz delay=5s timeout=2s period=10s #success=1 #failure=3
    Environment:  <none>
    Mounts:       <none>
  Volumes:        <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Available      True    MinimumReplicasAvailable
  Progressing    True    NewReplicaSetAvailable
OldReplicaSets:  <none>
NewReplicaSet:   webapp01-6b8f85d6cc (1/1 replicas created)
Events:
  Type    Reason             Age   From                   Message
  ----    ------             ----  ----                   -------
  Normal  ScalingReplicaSet  70s   deployment-controller  Scaled up replica set webapp01-6b8f85d6cc to 1


$ kubectl create or apply -f service.yaml
