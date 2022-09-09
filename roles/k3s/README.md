# k3s

This playbook will setup a minimal VPS ready for `k3s`
to be installed using [k3sup](https://github.com/alexellis/k3sup).

To run this playbook:

```sh 
export SERVER_IP=<VPS_IP>

ansible-playbook droplet-dev.yml -u root -i $SERVER_IP, --ask-vault-pass

#Once done, run `k3sup` from your local machine passing in the IP of the VPS.

k3sup install --ip $SERVER_IP \
--user k3s --local-path=./kubeconfig \
--context k3s-remote --k3s-extra-args=' \
--write-kubeconfig-mode 644'
# to join agents
export IP=<AGENT_VPS_IP>
k3sup join --ip $IP --server-ip $SERVER_IP --user root 
```
