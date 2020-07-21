# Ansible role - `k8s_metallb`

Manage MetalLB on a Kubernetes cluster.

This role can installs, (re)configure and uninstall MetalLB on a Kubernetes cluster.

## Tags

| Tag      | Description                             |
|----------|-----------------------------------------|
| `apply`  | Deploy and configure MetalLB            |
| `delete` | Remove MetalLB and associated resources |

## Variables

| Variable              | Type             | Required | Default | Description                                                                                      |
|-----------------------|------------------|----------|---------|--------------------------------------------------------------------------------------------------|
| `k8s_metallb_version` | `string`         | No       | `0.9.3` | MetalLB version                                                                                  |
| `k8s_metallb_pools`   | `list` of `dict` | Yes      | -       | MetalLB pools: [Documentation](https://metallb.universe.tf/configuration/#layer-2-configuration) |
| `k8s_metallb_peers`   | `list` of `dict` | No       | -       | MetalLB peers: [Documentation](https://metallb.universe.tf/configuration/#bgp-configuration)     |

### Variables - `k8s_metallb_pools`

MetalLB pools configuration is encoded into Ansible variables (e.g. in inventories `group_vars`). Example:

```yaml
k8s_metallb_pools:
  - name: production
    protocol: layer2
    addresses: "172.29.252.180-172.29.252.181"
  - name: test
    protocol: layer2
    addresses: "172.29.252.178-172.29.252.179"
```

## Templates

| Template           | Description           |
|--------------------|-----------------------|
| `configmap.yml.j2` | MetalLB configuration |

