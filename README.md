# AAP-WIN10LTSC

Windows **10 LTSC** playbooks for **Ansible Automation Platform** demos over **WinRM**, with **application workload** use cases (IIS, services, firewall ports) alongside operational tasks (facts, logs, patches).

## Inventory and Controller

- Playbooks target **`hosts: windows`** (see `inventory/ltsc-windows.ini`).
- **Do not** store passwords in this repo. In AAP, attach the **Machine** credential **LTSC - Windows** to job templates.
- Inventory **WindowsLTSC** in org **Demo - L2** defines group `windows`, host `win10-ltsc`, and WinRM connection variables.
- SCM project **GitHub - WindowsLTSC** syncs this repo; job templates use prefix **LTSC - Windows**.

## Playbook index

| Playbook | Purpose | Risk |
|----------|---------|------|
| `playbooks/win_connectivity.yml` | WinRM smoke test | Read-only |
| `playbooks/win_gather_facts.yml` | OS / memory facts | Read-only |
| `playbooks/win_ltsc_edition_facts.yml` | LTSC edition / build | Read-only |
| `playbooks/win_disk_facts.yml` | Disk and volume layout | Read-only |
| `playbooks/win_package_inventory.yml` | Installed packages sample | Read-only |
| `playbooks/win_service_facts.yml` | Service status filter | Read-only |
| `playbooks/win_firewall_inspect.yml` | Firewall rule sample | Read-only |
| `playbooks/win_eventlog_recent.yml` | Recent event log entries | Read-only |
| `playbooks/win_scheduled_task_inspect.yml` | Scheduled tasks sample | Read-only |
| `playbooks/win_iis_site_status.yml` | IIS feature and sites | Read-only |
| `playbooks/win_workload_healthcheck.yml` | App port + service + site summary | Read-only |
| `playbooks/win_iis_deploy_site.yml` | Deploy demo IIS site | **Mutating** |
| `playbooks/win_app_service_configure.yml` | Set service state | **Mutating** |
| `playbooks/win_firewall_app_port.yml` | Allow TCP port for workload | **Mutating** |
| `playbooks/win_optional_feature.yml` | Optional Windows features | **Mutating** |
| `playbooks/win_service.yml` | Start/stop/restart service | **Mutating** |
| `playbooks/win_updates.yml` | Windows Update install | **Mutating**, long |
| `playbooks/win_reboot.yml` | Controlled reboot | **Disruptive** |

## Extra variables (examples)

- **win_app_service_configure.yml**: `service_name`, `service_state`
- **win_iis_deploy_site.yml**: `iis_site_name`, `iis_site_port`, `iis_site_path`
- **win_firewall_app_port.yml**: `app_firewall_rule_name`, `app_tcp_port`
- **win_optional_feature.yml**: `feature_name`, `feature_state`
