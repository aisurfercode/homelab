## Summary of the Repo

This repo is used to establish a homelab using ansible automation

## CAUTION
The README.md may cover only partial coverage of all features

### USING TOOLS
provide preference to out of the box tools, before planning to write a script.
This is specially required while 'reading' or 'writing' a file.

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
 
