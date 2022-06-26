# jagungbakar

## Funny things:

```bash
# Kancane yo d pikir mazzeh, yo ndak mampu clusterku

vagrant@k3s-master1:~$ sudo k3s kubectl get po -n kube-system
NAME                                      READY   STATUS              RESTARTS       AGE
coredns-7796b77cd4-wb49x                  0/1     ContainerCreating   0              35m
kube-vip-ds-4r5r6                         0/1     Completed           3              35m
kube-vip-ds-7j8lj                         0/1     CrashLoopBackOff    11 (12m ago)   35m
kube-vip-ds-v9b78                         0/1     Completed           8              35m
local-path-provisioner-84bb864455-b8txp   1/1     Running             0              35m
metrics-server-ff9dbcb6c-2thb7            0/1     ContainerCreating   0              35m
vagrant@k3s-master1:~$ sudo k3s kubectl logs -n kube-system kube-vip-ds-7j8lj
Error from server: Get "https://k3s-master2:10250/containerLogs/kube-system/kube-vip-ds-7j8lj/kube-vip": proxy error from 127.0.0.1:6443 while dialing k3s-master2:10250, code 500: 500 Internal Server Error
vagrant@k3s-master1:~$ sudo k3s kubectl logs -n kube-system kube-vip-ds-7j8lj
The connection to the server 127.0.0.1:6443 was refused - did you specify the right host or port?
```