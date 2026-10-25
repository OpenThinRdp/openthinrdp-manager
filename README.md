# Know what is broken before your users call

**OpenThinRDP Manager is a free health center for the infrastructure of small and mid-size IT teams.** Point it at
your Hyper-V cluster, Proxmox, vSphere, Remote Desktop farm, Citrix site, domain, SQL Server and Veeam, and in about
30 seconds you see every problem, the worst first, each one in a plain sentence with what it means and how to fix it.

No agent to install. No server to build. No per-host license. **Download, extract, run.**

**[⬇ Download the free manager](https://github.com/OpenThinRdp/openthinrdp-manager/releases/latest)** · Windows 10/11
and Windows Server · English and Italian

<p align="center">
<img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp/main/docs/screenshots/manager-home.png" alt="OpenThinRDP Manager home: health score, Hyper-V cluster, remote desktops, hardware, the problems to look at first, today's sign-ins" width="100%">
</p>

## The calls it saves you

- *"Nobody can sign in."* It shows **who cannot sign in right now, and why**: the broker refusing, the VM in saved
  state, the desktop that will not start. Then the repair, one click, after you read it.
- *"The cluster went down when we patched one host."* It tells you **before**: the witness is offline, one host
  cannot carry the VMs of the other, a CSV is almost full.
- *"The backup failed last week and nobody noticed."* Failed Veeam jobs, Proxmox backups that did not run, VMs whose
  Hyper-V backups are only crash-consistent: on the first page, every morning.
- *"The certificate expired on Saturday."* **Every certificate of every server**, what uses it, when it expires,
  whether it renews by itself; your CA and its revocation list.
- *"The server room is hot."* Power supplies, fans and temperatures from iDRAC, iLO and XClarity.

## Everything you run, one window

| | What it checks |
|---|---|
| **Hyper-V & failover clusters** | hosts, VMs, checkpoints, quorum and witness, CSVs, Storage Spaces Direct, room for a host failure |
| **Proxmox VE** | quorum, nodes, storage, HA, failed tasks and backups, failing disks |
| **VMware vSphere** | vCenter health, hosts, datastores |
| **Remote Desktop Services & Citrix** | brokers, session hosts, virtual desktops, unregistered machines, licenses, who cannot sign in |
| **Active Directory & DNS** | domain controllers, replication, FSMO, time, zones |
| **SQL Server AlwaysOn** | replicas, synchronisation, jobs, backups, logins |
| **Veeam & VM backups** | failed and stale jobs, repositories, Hyper-V backup state |
| **Certificates** | every server, the enterprise CA, RDP certificates clients can verify |
| **Hardware** | Dell iDRAC, HPE iLO, Lenovo XClarity, Supermicro (Redfish) |
| **Your own services** | a web page, a port, a SQL query, your scripts |

## Why IT teams pick it

- **Free for any use, also commercial.** No trial, no account, no "per socket".
- **Nothing to install on your servers.** It reads them over WinRM, REST and SQL with an account you choose; read
  only, unless you confirm a repair.
- **You can read every command it runs** on your servers: they ship as plain PowerShell next to it.
- **Fixes, not only alarms.** Restart the stuck service, bring the role online, sync the clock, resume the database,
  back up the VMs to a share: each one shown before it runs.
- **It answers in sentences.** "The witness of VDICL is offline: the share \\\\nas1\\witness refuses the computer
  account" instead of a red dot.
- **Built by sysadmins, for a real production site** with two Hyper-V hosts, Remote Desktop and SQL AlwaysOn, and
  tested against it every day.

## Up and running in five minutes

1. [Download the zip](https://github.com/OpenThinRdp/openthinrdp-manager/releases/latest) and extract it.
2. Start `OpenThinRDP-Manager.exe`, choose **The servers alone**.
3. **Settings > Health Center**: your hosts, brokers, SQL listener, Proxmox or vCenter. Done: the Home fills in.

## Questions

### Is it really free?
Yes, for any use, also in a company and for your customers. It is not open source: its license forbids selling it or
building a competing product with it.

### Does it need an agent or a server?
No. It runs on your PC and reads your servers with Windows tools (WinRM, SQL) and the REST APIs of Proxmox, vCenter and
Veeam. Nothing is installed on them.

### Can it break something?
It only reads, until you choose a repair; every repair shows what it will do and asks first. What it runs on servers
is plain PowerShell you can read.

### Proxmox, vSphere, Veeam, Citrix: is it ready?
They are new in this release, built on their documented APIs and tested against recorded answers of those APIs, not yet on many real sites. If you run one, try it and
[tell us what it found](https://github.com/OpenThinRdp/openthinrdp-manager/issues): we are looking for sites to try
them.

### What is OpenThinRDP?
The same team builds [OpenThinRDP](https://openthinrdp.github.io/), a free open source thin client for Remote Desktop
(RDP over UDP, Secure Boot, signed updates). With it, the manager also runs your whole fleet of thin clients from the
same window.

**[⬇ Download the free manager](https://github.com/OpenThinRdp/openthinrdp-manager/releases/latest)**

## License

Free for any use, also commercial, closed: see [LICENSE.md](LICENSE.md). The thin client OpenThinRDP is open source (GPLv3).
