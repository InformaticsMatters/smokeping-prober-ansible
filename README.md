# smokeping-prober-ansible
Playbooks to deploy the [SmokePing Prober] utility.

## Deploying
To deploy the SmokePing Prober utility, you need to have admin access to
a suitable Kubernetes cluster, and poetry installed: -

    poetry shell
    poetry install

    export KUBECONFIG=~/k8s-config/my-cluster
    ansible-playbook site.yaml

## Undeploying
You simply need to add `-e spp_state=absent` to the `ansible-playbook` command: -

    ansible-playbook site.yaml -e spp_state=absent

---

[smokeping prober]: https://github.com/SuperQ/smokeping_prober
