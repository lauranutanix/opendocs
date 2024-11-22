# Creating a workload CAPX cluster spanning Prism Element clusters

!!! warning
        The scenario and features described on this page are experimental. It's important to note that they have not been fully validated.

This page will explain how to deploy CAPX-based Kubernetes clusters where worker nodes are spanning multiple Prism Element (PE) clusters. 

!!! note
        All the PE clusters must be managed by the same Prism Central (PC) instance.

The topology will look like this: 

- One PC managing multiple PE's
- One CAPI management cluster
- One CAPI workload cluster with multiple `MachineDeployment`resources

Refer to the [CAPI quickstart](https://cluster-api.sigs.k8s.io/user/quick-start.html){target=_blank} to get started with CAPX. 

To create workload clusters spanning multiple Prism Element clusters, it is required to create a `MachineDeployment` and `NutanixMachineTemplate` resource for each Prism Element cluster. The Prism Element specific parameters (name/UUID, subnet,...) are referenced in the `NutanixMachineTemplate`. 

## Steps
1. Create a management cluster that has the CAPX infrastructure provider deployed.
2. Create a `cluster.yml` file containing the workload cluster definition. Refer to the steps defined in the [CAPI quickstart guide](https://cluster-api.sigs.k8s.io/user/quick-start.html){target=_blank} to create an example `cluster.yml` file.
3. Add additional `MachineDeployment` and `NutanixMachineTemplate` resources.

    By default there is only one machine template and machine deployment defined. To add nodes residing on another Prism Element cluster, a new `MachineDeployment` and `NutanixMachineTemplate` resource needs to be added to the yaml file. The autogenerated `MachineDeployment` and `NutanixMachineTemplate` resource definitions can be used as a baseline.
    
    Make sure to modify the `MachineDeployment` and `NutanixMachineTemplate` parameters.

4. Apply the modified `cluster.yml` file to the management cluster.