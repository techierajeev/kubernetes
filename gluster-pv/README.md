Steps to create Persistent Volumes Using Glusterfs Plugin

Initial condition which must be fulfilled:-

1. GlusterFS must be running and reachable from kubernetes master.
2. for testing purpose mount the glusterfs volume on master and unmount it if every thing works fine if not then first make you gluster cluster healthy.

After all these we need to create following files on master namely:-

1. glusterfs-endpoints.yml
 after creating run:-
 kubectl create -f glusterfs-endpoints.yml
 make sure to edit glusterfs-endpoints.yml file reflects the ip corresponding to your gluster cluster Storage Pool.

2. Create Persistent Volume for Glusterfs using following command
  kubectl create -f glusterfs-pv.yml

3. check the persistent Volume Using
  Kubectl get pv

4. create a claim for glusterfs pv by running following command
  kubectl create -f glusterfs-pvc.yml

5. verify if the pvc has been bounded to pv or not using follwing command:-
  kubectl get pvc

for testing purpose of pvc, nginxpod.yml is there which uses the pvc created,

run the nginx pod using
kubectl apply -f nginx.yml

then check whether the data is being properly synced up or not according to nginx pod specs.

