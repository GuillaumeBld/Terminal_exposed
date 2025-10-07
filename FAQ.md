# FAQ

**Why not expose SSH directly?**
Because a web terminal is easier to gate with OAuth and requires no client setup, yet we still keep it isolated from the host.

**Can I use Wetty instead of ttyd?**
Yes, swap the image and port, keep the same Traefik labels.

**Can I run without OAuth?**
Not recommended. At minimum add strong basic auth and IP allowlist, however OAuth is preferred.
