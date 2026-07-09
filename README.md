# Goals / Roadmap
Web-based tool, probably docker-published, which offers functionality to run scripts, install patches and perform other OS-level management of Check Point management servers and firewalls. Should be fully browser-based UI and all container(s) deployed from a single docker compose file. Any configuration should be via a .env file with an example provided in the repo. 

### Proposed setup/provisioning flow:

- Connect via Mgmt API to management server to import/refresh list of CHKP hosts
- Leverage Run Script function via Mgmt API to deploy Gaia API creds to selected hosts
- Once Gaia API creds are deployed and tested on a host then the host is added to an inventory within the tool
- Inventory should be periodically and on-demand refreshed from management environment
- Inventory should be groupable manually or via tags, possibly tags consumed from management

### Proposed usage flow:

- Hosts or groups of hosts in the inventory can be selected individually or with multi-select for tasks
- Commands/tasks can be selected from an admin-defined library of tasks or created ad-hoc
- Commands can be implemented via clish script, Gaia API functions, or bash script
- If there is collectable output from the command that should be displayed on screen or optionally in a tar bundle
- Tasks can be scheduled and can be configured to execute in batches if there are a high number of targets

### Other nice-to-have funcionality:
- Clish config backup with configurable version retention
- Patch installation leveraging CDT functions (and also automated SCP and clish commands for management servers)
