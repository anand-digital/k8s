# k8s cheatsheet
https://kubernetes.io/docs/reference/kubectl/cheatsheet/

kubectl set image deployment/nginx-deployment nginx-container=nginx:1.18.0          
kubectl rollout status deployment/nginx-deployment
kubectl rollout history deployment/nginx-deployment
kubectl rollout undo deployment/nginx-deployment   

# Pod State
Running
Pending/ContainerCreating
Succeeded/Completed
Failed/Error/Crashloopback
Unknown

# Pod Condition
PodScheduled    --> The pod has been scheduled to a node
Initialized     --> The containers started successfully
Ready           --> pod can serve requests and is going to be added to matching services
ContainersReady --> all container in the pod are ready
Unschedulable   --> the pod cannot be scheduled (resource contraint, node unreachable, n/w error)

# Create Secret
kubectl create secret generic db-user-pass --from-file=./username.txt --from-file=./password.txt 

# Decryption
$ echo "cGFzc3dvcmQK"|base64 -d
password
$ echo "cm9vdAo="|base64 -d
root

# Encryption
$ echo -n "root" | base64
cm9vdA==
$ echo -n "password" | base64
cGFzc3dvcmQ=
