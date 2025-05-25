# Nordic DNS Blocklist

## Overview

**Nordic DNS Blocklist** is a curated `hosts` file containing domains known to serve ads, tracking scripts, and behavioral analytics - with a focus on those active in the Nordic countries  
(Denmark, Sweden, Norway, Finland, and Iceland), but is not limited to them.  
It is **not intended to be a complete blocklist**, but rather a targeted extension to improve privacy for users in the Nordics.

If you're already using other popular blocklists, this list is meant to complement them by adding region-specific domains that might be missed elsewhere.

## Compatibility

This blocklist is compatible with:

- All major operating systems (Linux, Unix, macOS, Windows)
- DNS sinkholes like [Pi-hole](https://pi-hole.net/)
- Router-level DNS filtering
- DNS proxies like `dnsmasq` or Acrylic DNS Proxy

The list uses the `0.0.0.0 domain.com` format - a standard hosts file syntax supported across most platforms and DNS filtering applications.

## Integration Options

### Pi-hole

To use this blocklist in **Pi-hole**:

1. Open the *Web Admin Interface*
2. Go to *Lists*
3. Add the following URL:

   ```text
   https://raw.githubusercontent.com/PaulSorensen/nordic-dns-blocklist/main/hosts
   ```

4. Click *Add blocklist*
5. Update Gravity under *Tools > Update Gravity*

This will merge the list with your existing blocklists.

### System Hosts File

You can manually append this list to your system’s `hosts` file:

- **Linux/Unix**: `/etc/hosts`
- **macOS**: `/etc/hosts` or `/private/etc/hosts` (depending on version)
- **Windows**: `%SystemRoot%\system32\drivers\etc\hosts`

> Sudo/administrator privileges are required to modify the `hosts` file.

#### Flush DNS Cache

After editing the hosts file, flush your DNS cache:

- **Linux** (systemd-based):

  ```bash
  sudo resolvectl flush-caches
  ```

- **macOS**:

  ```bash
  sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
  ```

- **Windows**:

  ```cmd
  ipconfig /flushdns
  ```

## License

This project is licensed under the **MIT License**.  
See the [`LICENSE`](./LICENSE) file for details.
