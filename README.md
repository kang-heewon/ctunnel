# ctunnel

`ctunnel` is a lightweight wrapper around [Cloudflare Tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/) that lets you forward a local port to your custom domain — just like `ngrok http <port>`, but with your own domain and free via Cloudflare.

## ✨ Features

- Use your own domain (e.g. `dev.example.com`)
- One-time init, then quick `ctunnel http <port>` usage
- Auto-generates tunnel config and maps your domain
- Fully local and lightweight (pure Bash)
- **Multiple tunnels support** with `--name` option

---

## 🚀 Installation

```bash
# 1. Install cloudflared (if not already)
brew install cloudflared

# 2. Download or create ctunnel
curl -o /usr/local/bin/ctunnel https://raw.githubusercontent.com/kang-heewon/ctunnel/refs/heads/main/ctunnel
# or manually copy ctunnel to /usr/local/bin/

# 3. Make it executable
chmod +x /usr/local/bin/ctunnel
```

---

## 📖 Usage

### Initialize a tunnel

```bash
ctunnel init --tunnel <name> --domain <your.domain.com>
```

This creates a Cloudflare tunnel and saves config to `~/.ctunnel/<name>.yml`.

### Start a tunnel

```bash
# Use a specific tunnel by name
ctunnel http <port> --name <name>

# Use default tunnel (if --name is omitted)
ctunnel http <port>
```

### Multiple tunnels example

```bash
# Initialize multiple tunnels
ctunnel init --tunnel dev --domain dev.example.com
ctunnel init --tunnel staging --domain staging.example.com

# Run them (in separate terminals)
ctunnel http 3000 --name dev
ctunnel http 4000 --name staging
```
