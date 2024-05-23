# smokeping-prober-ansible
Playbooks to deploy the [SmokePing Prober] utility.

## Deploying
To deploy the SmokePing Prober utility, you need to have admin access to
a suitable Kubernetes cluster with prometheus, and grafana installed.

To install the prober: -

    poetry shell
    poetry install

    export KUBECONFIG=~/k8s-config/my-cluster
    ansible-playbook site.yaml

Once done you can add the *off-the-shelf* Grafana dashboard (grafana ID [11335])
to your Grafana instance.

## Undeploying
You simply need to add `-e spp_state=absent` to the `ansible-playbook` command: -

    ansible-playbook site.yaml -e spp_state=absent

---

[smokeping prober]: https://github.com/SuperQ/smokeping_prober
[11335]: https://grafana.com/grafana/dashboards/11335-smoke-ping/
