# tmc-labs
All files need for LifeFire TMC Labs - 2022/23



### OPA Lab

Flux cli installed into the dekstops

New Cluster
1.  Enable Continuous delivery
    a. UI
    b. CLI - tmc cluster fluxcd continuousdelivery enable --cluster-name <cluster name>
2. k get ns on cluster should look like
tanzu-continuousdelivery-resources   Active   9m9s
tanzu-fluxcd-packageinstalls         Active   8m20s
tanzu-kustomize-controller 
tanzu-source-controller

k get pods -n tanzu-kustomize-controller
and
k get pods -n tanzu-source-controller

3. Add ssh credntials for their lab

4. Add git repo
name: livefire-tmc
url: https://github.com/<their repo>/tmc-labs.git

5. Add Kustomization
repo is livefire.tmc
path /continuous-delivery/psp/flux-config
turn prune on

check "addons" tab to see new stuff

<find the logs way to watch>

### Force CD to sync with git repo
```
flux reconcile source git livefire-tmc -n tanzu-continuousdelivery-resources
```
### Force CD to apply changes seen in git repo
```
flux reconcile kustomization flux-deploy -n tanzu-continuousdelivery-resources
```