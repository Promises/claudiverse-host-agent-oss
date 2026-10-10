# Claudiverse host agent documentation

The host agent is the small service that runs on each machine where seats
run. It keeps one outbound WebSocket to the Claudiverse server and, when the
server asks, starts, resumes, stops and interrupts seats in tmux, switches
their permission mode, and takes over seats started by hand. The machine opens
no port. The agent, not the server, decides what the machine allows, so even a
compromised server cannot make it go further than its config.

- To install it in a few steps, follow the repository's [README](../README.md)
  or the setup guide's
  [3. A machine for seats](https://github.com/Promises/claudiverse-oss/blob/main/docs/guide/3-machine.md).
- To know exactly what it does, read the **[reference](reference/README.md)**.

The words these pages use (host, seat, profile, allowed folders, and so on)
are defined in the Claudiverse
[glossary](https://github.com/Promises/claudiverse-oss/blob/main/docs/glossary.md).

## Reference pages

| Page | What it covers |
|---|---|
| [Overview](reference/README.md) | What the agent is, a diagram of its parts, the page index |
| [The host channel](reference/channel.md) | The WebSocket, the `host:<name>` channel, every request and refusal code, reconnects |
| [Starting seats](reference/starting-seats.md) | `spawn`, `resume` and `start_profile`, runtimes, the MCP catalog, the environment a seat gets |
| [Allowed folders](reference/roots.md) | The folder whitelist, browsing folders, adding and removing roots |
| [Trust and first-run setup](reference/trust-and-setup.md) | What the agent writes to `.claude.json` before a seat starts |
| [Seat control](reference/seat-control.md) | `stop`, `interrupt`, `set_mode` and the mode sweep |
| [Adopt](reference/adopt.md) | Putting a seat started by hand under a profile |
| [Local relay](reference/relay.md) | Running a plain `claude` on the account pool, with a direct fallback |
| [Install and service](reference/install-and-service.md) | `install.sh`, the systemd and launchd services, logs, updates, removal |
| [Configuration](reference/configuration.md) | Every config key, environment variable, limit and timing |

Each page has the same sections: an introduction, How it works,
Configuration, Interface, Failure modes and troubleshooting, Related pages and
Source.

## The other side of each request

The agent answers the server; the apps and tools ask the server. These pages
describe the same features from the other side:

| Feature | Server | Clients |
|---|---|---|
| Hosts, spawn, stop, resume, profiles | [Profiles and hosts](https://github.com/Promises/claudiverse-oss/blob/main/docs/reference/server/profiles-and-hosts.md) | Mac [New seat](https://github.com/Promises/claudiverse-apps/blob/main/docs/mac/new-seat.md), [Profiles](https://github.com/Promises/claudiverse-apps/blob/main/docs/mac/profiles.md); Android [New seat](https://github.com/Promises/claudiverse-apps/blob/main/docs/android/new-seat.md), [Profiles](https://github.com/Promises/claudiverse-apps/blob/main/docs/android/profiles.md) |
| Adopt | [Profiles and hosts](https://github.com/Promises/claudiverse-oss/blob/main/docs/reference/server/profiles-and-hosts.md) | Mac [Adopt](https://github.com/Promises/claudiverse-apps/blob/main/docs/mac/adopt.md) |
| Host tokens | [Accounts, sign-up and tokens](https://github.com/Promises/claudiverse-oss/blob/main/docs/reference/server/auth.md) | Mac [Settings](https://github.com/Promises/claudiverse-apps/blob/main/docs/mac/settings.md) |
| The seat a spawn starts | [Sessions and rooms](https://github.com/Promises/claudiverse-oss/blob/main/docs/reference/server/sessions-and-rooms.md) | [The mod: registration](https://github.com/Promises/claudiverse-oss/blob/main/docs/reference/services/mod/registration.md), [cv-spawn.sh](https://github.com/Promises/claudiverse-oss/blob/main/docs/reference/runners/cv-spawn.md) |
| The relay's pooled requests | [API proxy](https://github.com/Promises/claudiverse-oss/blob/main/docs/reference/server/api-proxy.md), [Account pool](https://github.com/Promises/claudiverse-oss/blob/main/docs/reference/server/account-pool.md) | |
