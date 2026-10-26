# Code signing of the manager

From 0.2.25 the launchers of the manager (`OpenThinRDP-Manager.exe` and the copy it keeps, `.launcher`) are signed
with Authenticode by the project, with a timestamp, so the signature stays valid after the certificate expires.
The rest of the manager is covered by `MANIFEST.txt`, signed with the release key of the project and checked by the
launcher before every start.

| | |
|---|---|
| Certificate | [openthinrdp-codesign.cer](openthinrdp-codesign.cer) |
| Subject | `CN=OpenThinRDP Project, O=OpenThinRDP, C=IT` |
| SHA-1 thumbprint | `584417E1549EFAE6F7D9DEEAAACC59D352A6F864` |
| Valid until | 23 October 2036 |

The certificate is the project's own (self-signed), not one bought from a certification authority: Windows shows the
signature as *not trusted* until you allow it. That takes one step, and then covers every next release.

## Allow it once

- **Your EDR or antivirus** (SentinelOne, Defender for Endpoint, CrowdStrike...): an exclusion or allow rule by
  **signer** or **certificate** with the thumbprint above, instead of one by path or hash that every release changes.
- **Windows, for all your PCs**: a GPO that imports `openthinrdp-codesign.cer` into *Trusted Root Certification
  Authorities* and *Trusted Publishers* (Computer Configuration > Policies > Windows Settings > Security Settings >
  Public Key Policies). The signature then shows as valid.

## Or sign it with your own certificate

If your company has its own code signing certificate (from your enterprise CA, or bought), the manager signs itself
with it: *Settings > Security > Code signing > Sign the manager*. It signs every new version again after it updates
itself, so the rules you already have for your own signer keep working.

Check a file: `Get-AuthenticodeSignature .\OpenThinRDP-Manager.exe | Format-List` in PowerShell.
