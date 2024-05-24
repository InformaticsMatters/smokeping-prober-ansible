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

## Existing deployment parameters
Parameters for existing (historical) deployments can be found in various
`parameters-*.yaml` files in the root fo the repository.

To deploy the prober with a specific set of parameters, you can use the `-e` flag
with `ansible-playbook`: -

    ansible-playbook site.yaml -e @parameters-<name>.yaml

## Undeploying
You simply need to add `-e spp_state=absent` to the `ansible-playbook` command: -

    ansible-playbook site.yaml -e spp_state=absent

And, with a parameter file: -

    ansible-playbook site.yaml -e @parameters-<name>.yaml -e spp_state=absent

## Grafana dashboard
A customised Grafana dashboard is available in the `grafana` directory. This
allows selection of metrics based on the **Namespace** of the originating
SmokePing metrics using the `namespace` variable, whose value is automatically
extracted from the observed metrics.

---

[smokeping prober]: https://github.com/SuperQ/smokeping_prober
[11335]: https://grafana.com/grafana/dashboards/11335-smoke-ping/
