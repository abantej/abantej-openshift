# abantej-openshift
Abantej's Openshift Project


## Install Openshift on Ubuntu

```
wget https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz

tar xvzf openshift*.tar.gz

cd openshift-origin-client-tools*/

sudo mv oc kubectl /usr/local/bin/

oc version

cat << EOF | sudo tee /etc/docker/daemon.json
{
"insecure-registries" : [ "172.30.0.0/16" ]
}
EOF

sudo systemctl restart docker

oc cluster up

oc cluster down

sudo nano ./openshift.local.clusterup/openshift-controller-manager/openshift-
master.kubeconfig

# In that file, search for the line:
server: https://127.0.0.1:8443

# Replace that line with:
server: https://SERVER_IP:8443
# Where SERVER_IP is the IP address of the hosting server.

oc cluster up --public-hostname=SERVER_IP

```

## Login to Openshift

https://127.0.0.1:8443

```
oc login -u USERNAME -p PASSWORD

oc login -u system:admin

oc project default

oc login

oc new-project dev --display-name="Test Project" --description="My Test Project"
```