
# NetBox With Ansible

Automating network configuration generation using **NetBox as the Source of Truth** and **Ansible** as the automation engine.

The project uses the NetBox Ansible inventory plugin to retrieve network devices dynamically from NetBox and a Jinja2 template to generate device configuration files.

---

## Architecture

```text
                    ┌─────────────────────┐
                    │       NetBox        │
                    │                     │
                    │  Sites              │
                    │  Devices            │
                    │  Roles              │
                    │  Primary IPs         │
                    │  Custom data         │
                    └──────────┬──────────┘
                               │
                               │ NetBox API
                               ▼
                    ┌─────────────────────┐
                    │ Ansible Inventory   │
                    │                     │
                    │ nb_inventory        │
                    └──────────┬──────────┘
                               │
                               │ Dynamic inventory
                               ▼
                    ┌─────────────────────┐
                    │   Ansible Playbook  │
                    │                     │
                    │ Generate configs     │
                    └──────────┬──────────┘
                               │
                               │ Jinja2
                               ▼
                    ┌─────────────────────┐
                    │ Generated Configs   │
                    │                     │
                    │ Router_01.cfg       │
                    │ Router_02.cfg       │
                    │ Router_03.cfg       │
                    └─────────────────────┘
