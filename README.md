# Homelab v2.4.7

v2.4.7 keeps the v2.4.6-r4 stabilization fixes and restores the safer Cloudflared architecture:

- Cloudflare Tunnel name is stable: `homelab-main`.
- Cloudflared browser auth and DNS route creation run early on the Proxmox host.
- `cert.pem` stays on Proxmox only.
- VM103 receives only the tunnel-specific JSON credential and runs a simple systemd service.
- qBittorrent policy automation is added: 30 active downloads, 0 uploads, 30 active torrents, 1000 KiB/s upload limit, stop/no-seed after completion, SMTP notification attempt with `admin@bacmastercloud.com`.

## Fresh install

```bash
bash <(curl -fsSL https://raw.githubusercontent.com/bacproxmox/homelabv2.4.7/main/bootstrap.sh)
```

## Notes

- Guided fresh install still performs destructive reset of `nvme-vm` and `nvme-vm-two` only in guided/destructive mode.
- Imported TrueNAS API keys are ignored; fresh TrueNAS installs generate a new API key via the postinstall helper.
- Cloudflared uses no Cloudflare API token in the normal flow.
