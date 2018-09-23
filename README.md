# VMware manage vCenter hosts
Ansible role that adds/removes esxi hosts in vCenter Server

The configuration of the role is done so that it shouldn't be necessary to
modify the role for any configuration.
All settings can be configured by changing role parameters or by declaring new
config as variable.

Please report any issues or send PR.

## Examples
```yaml
---

- name: Example of how to add a esxi host
  hosts: vcenter
    vars:
      vcenter_auth:
        hostname: 192.0.2.1
        username: administrator@abc.lan
        password: super_pass
        validate_certs: False
    esxi_hosts:
      - name: 192.168.1.1
        add_conn: yes
        datacenter: dc1
        cluster: cl1
        state: present
        esxi_ssl_thumbprint : xx:xx:xx
        esxi_username: root
        esxi_password: pass
  roles:
    - ansible-vmware_host  

  ```

## Role variables
```yaml
## Role variables
# ---------------------------------------------------------------------------
# Define the vcenter auth details to be used
# ---------------------------------------------------------------------------
vcenter_auth: { }


# ---------------------------------------------------------------------------
# Define the vmware esxi hosts to be added/removed
# ---------------------------------------------------------------------------
esxi_hosts: { }
```

## License
Apache

## Author
Dan Murarasu
