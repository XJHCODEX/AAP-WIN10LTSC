# LTSC Workstation Compliance Profile (v1.0)

Reference mapping for `roles/windows_compliance_report` checks. Use with job template **LTSC - Windows Compliance Report**.

## Control catalog

| ID | Category | Control | PASS expectation |
|----|----------|---------|------------------|
| SEC-001 | Account Security | Guest account disabled | Guest not enabled |
| SEC-002 | Account Security | Password minimum length | >= 8 (configurable) |
| AUD-001 | Auditing | Logon events audited | Success and/or Success and Failure |
| AUD-002 | Auditing | Policy change audited | Success and/or Success and Failure |
| FW-001 | Network | Firewall profiles | Domain, Private, Public enabled |
| FW-002 | Network | Public inbound default | Default inbound Block |
| DEF-001 | Endpoint Protection | Defender RTP | Real-time protection on |
| DEF-002 | Endpoint Protection | Defender signatures | Updated within 7 days (configurable) |
| UPD-001 | Patch Management | Recent hotfix | Within 90 days (configurable) |
| UPD-002 | Patch Management | Windows Update service | wuauserv running |
| ENC-001 | Encryption | BitLocker OS volume | Protection on |
| RDP-001 | Remote Access | RDP / NLA | RDP off, or NLA required |
| TLS-001 | Cryptography | TLS 1.0 server | Disabled |
| TLS-002 | Cryptography | TLS 1.1 server | Disabled |
| SMB-001 | Protocols | SMBv1 | Not enabled |
| UAC-001 | System Hardening | UAC | EnableLUA=1 |
| PS-001 | PowerShell | Execution policy | Restricted / AllSigned / RemoteSigned |
| LTSC-001 | LTSC | Edition | Caption contains LTSC |
| SVC-001 | Services | WinDefend | Running |

## Extending to full STIG/CIS

1. **Audit-only today:** Run this role for a scored summary in AAP stdout.
2. **Hardening:** Integrate `ansible-lockdown.Windows_10_STIG` as a separate *remediation* workflow (not read-only).
3. **Commercial audit:** Lockdown Enterprise / Goss-based audit for full STIG evidence chains.
