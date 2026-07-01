# Homelab AI Agent Stack

An Ansible-managed local AI runtime.

- Raspberry Pi 5 → Hermes Agent
- Radxa Q6A → Ollama inference backend
- Handshake → validates Hermes ↔ Ollama runtime

---

## Architecture

```text
                 Ansible 

+-------------+        HTTP / OpenAI API        +-------------+
| RaspberryPi | ─────────────────────────────▶ |  Radxa Q6A  |
|             |                                |             |
| Hermes      |                                | Ollama      |
| Agent       |                                |             |
+-------------+                                +-------------+
        │                                              │
        └────────────── Handshake ─────────────────────┘

                        Validates
                        • provider
                        • endpoint
                        • model
                        • context
                        • inference
```

---

## Runtime Contract

```text
Hermes Agent ──▶ Ollama API ──▶ Local Model
```

Hermes expects:

```yaml
provider: ollama
base_url: http://<ollama_host>:11434/v1
model: <model>
context_length: <value>
```

---

## Ansible Layout

```text
ansible/
├── inventory/
├── group_vars/
├── playbooks/
│   └── pi5.yml
└── roles/
    ├── hermes/
    ├── ollama/
    └── handshake/
```

---

## Roles

### hermes

Installs and configures Hermes Agent.

Owns:

- agent runtime
- CLI
- model provider configuration


### ollama

Installs and configures Ollama.

Owns:

- inference service
- model lifecycle


### handshake

Validates final runtime state.

Owns:

- Hermes ↔ Ollama configuration alignment
- model configuration
- end-to-end query test

---

## Deployment

```bash
ansible-playbook playbooks/pi5.yml
```

---

## Design Principles

- Roles own isolated responsibilities
- Inventory defines runtime configuration
- Validation is explicit
- Avoid manual drift
- Keep system boundaries clear

---

## Current State

```text
Pi5 ──▶ Hermes ──▶ Ollama ──▶ Local LLM
```

Future:

- messaging gateway
- tools
- agent workflows
- Hermes-assisted infrastructure refactoring
