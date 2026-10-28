# Know what is broken before your users call

**Your whole infrastructure, checked in 30 seconds. Free.** OpenThinRDP Manager is the health center small and
mid-size IT teams were missing: point it at your Hyper-V cluster, Proxmox, vSphere, Remote Desktop farm, Citrix site,
domain, SQL Server and Veeam, and it shows you every problem, the worst first, each one in a plain sentence with what
it means and the fix.

No agent to install. No server to build. No per-host license. **Download, extract, run.**

**[⬇ Download the free manager](https://github.com/OpenThinRdp/openthinrdp-manager/releases/latest)** · Windows 10/11
and Windows Server · English and Italian · **1.0.0**, it updates itself · [its page](https://openthinrdp.github.io/manager.html)

<p align="center">
<img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp-manager/main/docs/m-home.png" alt="OpenThinRDP Manager home: health score, Hyper-V cluster, remote desktops, hardware, the problems to look at first, today's sign-ins" width="100%">
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
- *"A disk died and the RAID was degraded for a month."* **What the iDRAC says of every part**: each disk with its remaining life and a failure it predicts, RAID and its battery, memory module by module, power supplies, fans, temperatures, the hardware log and every firmware version.

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

## See it

| | |
|---|---|
| <img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp-manager/main/docs/m-health.png" alt="Health Center: each problem in a plain sentence with its fix"><br>**Health Center**: each problem in a plain sentence, with a fix you confirm | <img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp-manager/main/docs/m-hardware.png" alt="Server hardware from the iDRAC, part by part"><br>**Server hardware**: what the iDRAC says of every part, disk by disk |
| <img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp-manager/main/docs/m-users.png" alt="Users: who cannot sign in right now and why"><br>**Users**: who cannot sign in right now, and why | <img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp-manager/main/docs/m-experience.png" alt="Experience: sign-in time over 30 days"><br>**Experience**: how long each sign-in takes, for 30 days |
| <img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp-manager/main/docs/m-devices.png" alt="Devices: every thin client with state, session and version"><br>**Devices**: every thin client, its state, user and version | <img src="https://raw.githubusercontent.com/OpenThinRdp/openthinrdp-manager/main/docs/m-settings.png" alt="Settings: each server with its own account and a Test button"><br>**Settings**: each server with its own account and a Test |
## Why IT teams pick it

- **Free for any use, also commercial.** No trial, no account, no "per socket".
- **Nothing to install on your servers.** It reads them over WinRM, REST and SQL with an account you choose; read
  only, unless you confirm a repair.
- **You can read every command it runs** on your servers: they ship as plain PowerShell next to it.
- **Fixes, not only alarms.** Restart the stuck service, bring the role online, sync the clock, resume the database,
  back up the VMs to a share: each one shown before it runs.
- **It answers in sentences.** "The witness of VDICL is offline: the share \\\\nas1\\witness refuses the computer
  account" instead of a red dot.
- **Born in production.** Built by sysadmins for a real site with two Hyper-V hosts, Remote Desktop and SQL
  AlwaysOn, and running there every day.
- **It grows fast.** Proxmox, vSphere, Veeam, Citrix and the enterprise CA arrived in a single release; what users
  ask for comes next.

## Up and running in five minutes

1. [Download the zip](https://github.com/OpenThinRdp/openthinrdp-manager/releases/latest) and extract it.
2. Start `OpenThinRDP-Manager.exe`, choose **The servers alone**.
3. **Settings > Health Center**: your hosts, brokers, SQL listener, Proxmox or vCenter. Done: the Home fills in.

## Add free thin clients to the same window

Your users connect to those desktops from somewhere. [OpenThinRDP](https://openthinrdp.github.io/) turns any PC or
old thin client into a locked-down Remote Desktop client, free and open source, for Windows VMs on **Hyper-V,
Proxmox, VMware or any cloud** ([Proxmox and VMware](https://openthinrdp.github.io/proxmox-vmware-thin-client.html)):
RDP over UDP that stays smooth on bad lines, USB and webcams, signed updates. With it, this same manager runs the
whole fleet: every device, every sign-in, how fluid each session was.

## Questions

### Is it a PowerShell script that edits configuration files?
No. That was the first manager of OpenThinRDP, in its first weeks (up to 0.2.22). Today it is a Windows application with
releases of its own (1.0.0 from 28 October 2026), signed with the project key, that updates itself; the health center
works also without any thin client. The commands it runs on your servers stay plain PowerShell you can read.

### Is it really free?
Yes, for any use, also in a company and for your customers. It is not open source: its license forbids selling it or
building a competing product with it.

### Does it need an agent or a server?
No. It runs on your PC and reads your servers with Windows tools (WinRM, SQL) and the REST APIs of Proxmox, vCenter and
Veeam. Nothing is installed on them.

### Can it break something?
It only reads, until you choose a repair; every repair shows what it will do and asks first. What it runs on servers
is plain PowerShell you can read.

### I run Proxmox, vSphere, Veeam or Citrix: can I use it?
Yes: they arrived in this release, built on their official APIs. Be one of the first sites to run it, and
[tell us what it found](https://github.com/OpenThinRdp/openthinrdp-manager/issues): reports from real sites are
what we work on first.

### What is OpenThinRDP?
The same team builds [OpenThinRDP](https://openthinrdp.github.io/), a free open source thin client OS for Remote
Desktop on any hypervisor (RDP over UDP, Secure Boot, signed updates). With it, the manager also runs your whole fleet
of thin clients from the same window.

**[⬇ Download the free manager](https://github.com/OpenThinRdp/openthinrdp-manager/releases/latest)**

## License

Free for any use, also commercial, closed: see [LICENSE.md](LICENSE.md). The thin client OpenThinRDP is open source (GPLv3).
