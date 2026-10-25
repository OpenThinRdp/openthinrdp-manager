# OpenThinRDP Manager

**A free health center for your infrastructure: Hyper-V and failover clusters, Proxmox VE, VMware vSphere, Remote
Desktop Services and Citrix, domain controllers, DNS and certificates, SQL Server AlwaysOn, Veeam and VM backups, and
the hardware (iDRAC, iLO, XClarity), in one window, with no agent and no server.** It finds what is wrong, says it in one plain sentence, and repairs it when you confirm. It also manages
[OpenThinRDP](https://github.com/OpenThinRdp/openthinrdp) thin clients, but it does not need them.

<p align="center">
<img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp/main/docs/screenshots/manager-home.png" alt="OpenThinRDP Manager, Home: the health of the infrastructure, the Hyper-V cluster and its hosts, the remote desktops, the hardware, what to look at first" width="100%">
</p>

**[Download the latest release](https://github.com/OpenThinRdp/openthinrdp-manager/releases/latest)**: a zip, nothing to
install. Windows 10/11 or Windows Server 2016 and later, Windows PowerShell 5.1 (in every Windows). English and Italian.

## What it checks

| | |
|---|---|
| **Hyper-V hosts** | memory, CPU, disks, services, VMs that are off, saved, paused or without heartbeat, old checkpoints, planned VMs left behind, guardians of the vTPM, the room for one host to fail |
| **Failover clusters** | nodes, quorum and witness (and why the witness is offline), Cluster Shared Volumes, Storage Spaces Direct pool and disks, repairs running, networks for live migration, anti-affinity |
| **Remote Desktop Services** | connection brokers and their database, session hosts and virtual desktops, who cannot sign in now and why, the RDP certificates, RD Gateway and RD Web, the broker self-repair |
| **Active Directory and DNS** | domain controllers, replication, FSMO roles, SYSVOL and NETLOGON, the clock against the PDC emulator, ADWS, DNS zones, reverse zones, stale records |
| **SQL Server AlwaysOn** | the listener, replicas, synchronisation, suspended databases, failed jobs, backups, logins missing on a replica |
| **Backups** | the backups of the VMs as Hyper-V sees them, and a backup of the VMs to a share, without an agent |
| **Proxmox VE** *(new)* | quorum, nodes, memory, storage, HA resources, failed tasks and backups, failing disks |
| **VMware vSphere** *(new)* | the health of vCenter, hosts disconnected or off, datastores almost full |
| **Veeam Backup & Replication** *(new)* | failed jobs, jobs that stopped running, repositories almost full or offline |
| **Citrix Virtual Apps and Desktops** *(new)* | controllers, unregistered machines, groups without free desktops, licenses in grace period |
| **Certificates** | every certificate of every server, what uses it, when it expires, whether it renews by itself; the enterprise CA and its revocation list; which RDP servers a client could verify |
| **Hardware** | over Redfish (Dell iDRAC, HPE iLO, Lenovo XClarity, Supermicro): power now and over 24 hours, power supplies, temperatures, fans |
| **Your own services** | a web page, a TCP port or a SQL query, as their users reach them; your own checks and commands |

Each problem comes with what it means in plain words and, when there is one, a repair you confirm before it runs.
History and forecast (memory, disks, volumes over 30 days), maintenance per item, notices when a problem comes or
goes, and `-HealthReport -Json` for Task Scheduler or a monitoring system.

## Why it is different

- **No agent, no server, no database.** It reads your servers over WinRM and SQL with the account you run it as.
  Administration without administrator rights is possible (JEA).
- **You can read what it runs on your servers.** Every command it sends is in `commands\` and `rds\`, plain
  PowerShell, and it shows what it will do before you confirm.
- **Its files are signed.** The launcher checks every file against `MANIFEST.txt`, signed with the project key, before
  anything runs: a changed file stops it.
- **Your secrets stay with you.** SSH keys, signing keys and iDRAC accounts are in an encrypted vault next to the
  manager (PBKDF2 600 000 rounds, AES-256, HMAC); nothing goes to the project unless you send it.

## Start

1. Extract the zip into a folder, on a share if more administrators use it.
2. Start `OpenThinRDP-Manager.exe`. The first time, choose **The servers alone** (or the management folder of your
   OpenThinRDP devices), then **Settings > Health Center**: your hosts, brokers, SQL listener and backup share.
3. On each PC: `OpenThinRDP-Manager.exe -Install` puts a shortcut with the icon on its desktop.

The launcher is not signed with a certificate: Windows SmartScreen may ask the first time.

The full guide: [the manager](https://github.com/OpenThinRdp/openthinrdp/blob/main/docs/manager.md).

## With OpenThinRDP thin clients

[OpenThinRDP](https://github.com/OpenThinRdp/openthinrdp) turns thin clients and old PCs into Remote Desktop devices
(Debian, FreeRDP with UDP, Secure Boot, open source). With them, the same window also shows every device and its user,
signed updates with pilot devices and going back, the remote screen, how long each sign-in takes, the peripherals,
scheduled jobs and the inventory.

## Proxmox, vSphere, Veeam or Citrix? Try it

Those four are new: built against their documented APIs, read only, and not yet run on many real sites. If you run
one of them, try the manager and [tell us](https://github.com/OpenThinRdp/openthinrdp-manager/issues) what it read and
what it missed: your report decides what comes next.

## Issues and questions

[Open an issue](https://github.com/OpenThinRdp/openthinrdp-manager/issues): what you saw, the Windows versions, and
the message of the manager. A check that is wrong: *Report a false positive* in the manager prepares the issue, with
the names of your servers replaced.

## License

Free for any use, also commercial, closed: see [LICENSE.md](LICENSE.md). The thin client OpenThinRDP is open source
(GPLv3). The manager of the OpenThinRDP releases up to 0.2.22 was published under the GNU GPL and stays under it.
