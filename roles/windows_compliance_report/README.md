# windows_compliance_report

Read-only Ansible role that evaluates a **baseline compliance profile** on Windows hosts and prints an **AAP-friendly** scored report.

## What this is / is not

- **Is:** A structured workstation audit (account, audit, firewall, Defender, patching, BitLocker, TLS, SMBv1, UAC, LTSC identity) suitable for demos and drift visibility.
- **Is not:** A full DISA STIG or CIS benchmark assessment. For remediation at scale, see [ansible-lockdown/Windows-10-STIG](https://github.com/ansible-lockdown/Windows-10-STIG) (remediation role; separate audit tooling not bundled).

## Variables

| Variable | Default | Purpose |
|----------|---------|--------|
| `compliance_report_profile` | `ltsc_workstation` | Profile identifier in output |
| `compliance_max_patch_age_days` | `90` | WARN threshold for last hotfix |
| `compliance_max_defender_signature_age_days` | `7` | WARN threshold for AV signatures |
| `compliance_min_password_length` | `8` | Minimum password length check |

## Usage

```yaml
- hosts: windows
  roles:
    - role: windows_compliance_report
```

## Scoring

- **PASS** = 1 point, **WARN** = 0.5, **FAIL** / **INFO** = 0
- Score % = `(pass + 0.5*warn) / total * 100`
