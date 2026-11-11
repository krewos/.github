<p align="center">
  <img src="https://raw.githubusercontent.com/krewos/.github/main/profile/logo.svg" width="112" height="112" alt="KrewOS logo" />
</p>

<h1 align="center">KrewOS</h1>

<p align="center">
  <strong>Self-hosted, local-first multi-agent runtime &amp; observatory.</strong><br />
  Run and coordinate a crew of specialized AI agents on your own infrastructure, using your own LLM API keys.
</p>

<p align="center">
  <a href="https://krewos.github.io"><strong>Website &amp; Docs</strong></a> ·
  <a href="https://krewos.github.io/demo.html"><strong>Live Demo</strong></a> ·
  <a href="https://github.com/krewos/krewos"><strong>Quickstart (Docker Compose)</strong></a> ·
  <a href="https://github.com/krewos/krewos/pkgs/container/krewos"><strong>Container Registry (<code>ghcr.io/krewos/krewos</code>)</strong></a> ·
  <a href="https://github.com/krewos/krewos/issues"><strong>Issues &amp; Feedback</strong></a> ·
  <a href="https://github.com/krewos/krewos/blob/main/LICENSE"><strong>EULA 1.0</strong></a>
</p>

---

### Why KrewOS?

- **Team Collaboration & Instant Control** — Work 1-on-1 with specialist agents or in multi-agent team rooms (Circles) led by **Helios**, complete with backchannel specialist handoffs and instant mid-turn interruption.
- **Interactive Observatory & Live Control Panels** — See what every agent is doing in real time, take over their live Chromium browser for 2FA or logins, or step into their dedicated Linux terminal and file explorer.
- **Reusable Skills & MCP Tools** — Give agents custom Markdown playbooks (`SKILL.md`) that you can trigger with `/` slash commands in chat, alongside external Model Context Protocol (`mcp.json`) servers.
- **Hardened Single-Container Stack ("Verify the Cage")** — One Distroless/Hardened container (`ghcr.io/krewos/krewos`, built on `gcr.io/distroless/cc-debian13` with zero `SUID`/`SGID` bits, `read_only: true`, `cap_drop: ALL`, and zero host `docker.sock` exposure) bundles the Rust runtime, SQLite persistence, automatic TLS reverse proxy (`nginx`), per-agent Linux UIDs (`20001+`), persistent terminals, and isolated Chromium profiles.
- **Encrypted Secret Vault & Persistent Memory** — Per-agent secrets are encrypted at rest with `ChaCha20-Poly1305` and automatically redacted across tool outputs, terminals, and file previews. Background memory consolidation distills long-term knowledge into SQLite and `MEMORY.md`.

---

### 60-Second Quickstart

```bash
git clone https://github.com/krewos/krewos.git
cd krewos
cp .env.example .env
docker run --rm -it ghcr.io/krewos/krewos:latest /usr/local/bin/krewos --hash-password
# Set KREWOS_AUTH_PASSWORD_HASH, KREWOS_LLM_BASE_URL, and KREWOS_LLM_API_KEY in .env
docker compose pull && docker compose up -d
bash scripts/container-security-check.sh   # optional: verify the kernel & Distroless cage
```

Then open **[https://krewos.localhost](https://krewos.localhost)** (full setup &amp; local CA trust guide in **[krewos/krewos](https://github.com/krewos/krewos)** and **[krewos.github.io](https://krewos.github.io)**).

---

### Repositories

| Repository | Purpose |
|---|---|
| **[`krewos/krewos`](https://github.com/krewos/krewos)** | Official Docker Compose deployment kit, `.env.example`, `mcp.json`, issue tracker, and **[EULA 1.0](https://github.com/krewos/krewos/blob/main/LICENSE)** |
| **[`krewos/krewos.github.io`](https://github.com/krewos/krewos.github.io)** | Public showcase website &amp; documentation hosted on **[krewos.github.io](https://krewos.github.io)** |
