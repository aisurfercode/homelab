## Summary of the Repo
This repo is used to establish a homelab using ansible automation

## Folder structure
.
├── AGENTS.md           - contains information for coding agents this file itself
├── ansible             - ansible code lives inside ansible directory
│   ├── ansible.cfg     - ansible configuration
│   ├── docs            - documentation directory
│   ├── inventory       - host inventory, variables and group variables
│   ├── playbooks       - plays organized into invoking roles
│   └── roles           - tasks related to each role as referenced in playbook
└── README.md           - Brief introduction of the project, not complete

## CAUTION
The README.md may cover only partial coverage of all features

### USING TOOLS
Prefer using out of the box tools, before planning to write a script.
This is specially required while 'reading' or 'writing' a file.

In other words avoid 'bash' commands to run cat/echo etc. shell commands to read, write into files,
there are already given built-in tools which have better integration like 'read' or 'write'. 

Using bash makes sense only when read/write tool give errors.

### SAFETY
while making changes - make a temporary file first, compare changes
then only sync the temporary to the existing file. 
This extra step prevents confusion or git reverts later on.

### ANSIBLE GUIDELINES
- Make sure to use core ansible features and in rare cases only extensions.
- Make sure to write idempotent code.
- Make sure to keep playbooks organized with tasks with specific goals
    - installation
    - verification/testing
  this makes the code modular and keeps small responsibilies per role.
 
