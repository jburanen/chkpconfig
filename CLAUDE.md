# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project status

This repository currently contains only planning material (README.md) and a LICENSE — no source code, build system, or tests exist yet. There are no build/lint/test commands to run at this stage. When implementation begins, update this file with the actual commands and architecture notes.

## Project goal

chkpconfig is a planned web-based tool (browser UI, Docker-deployed via a single `docker compose` file, configured via `.env`) for OS-level management of Check Point management servers and firewalls: running scripts, installing patches, and other administrative tasks.

### Planned provisioning flow

- Connect via the Check Point Management API to import/refresh an inventory of CHKP hosts.
- Use the Management API's Run Script function to deploy Gaia API credentials to selected hosts.
- Once Gaia API creds are deployed and verified on a host, add it to the tool's inventory.
- Inventory refreshes periodically and on demand from the management environment.
- Hosts can be grouped manually or via tags (including tags pulled from the management server).

### Planned usage flow

- Select individual hosts or groups (multi-select) as task targets.
- Commands/tasks come from an admin-defined library or are created ad-hoc.
- Commands can be implemented as clish scripts, Gaia API calls, or bash scripts.
- Command output is displayed on screen and optionally collected into a tar bundle.
- Tasks can be scheduled and batched when targeting a large number of hosts.

### Other planned functionality

- Clish config backup with configurable version retention.
- Patch installation via CDT functions, plus automated SCP/clish workflows for management servers.

## .gitignore maintenance

A general-purpose `.gitignore` exists covering env files, OS/editor cruft, and common Node/Python/Docker artifacts. As the actual tech stack is chosen and new tools/frameworks are introduced, update `.gitignore` to match (e.g. add framework-specific build output, package manager lockfile caches, language-specific artifacts) rather than letting generated files leak into commits.

## Commit convention

When creating git commits in this repository, always include Claude as a co-author:

```
Co-Authored-By: Claude <noreply@anthropic.com>
```
