# Ansible playbook template

![Ansible](https://img.shields.io/badge/usage-playbook--template-blue)
![Platform](https://img.shields.io/badge/platform-Ubuntu-lightgrey)
![License](https://img.shields.io/badge/license-Unlicense-green)

## Description

This Ansible project provides a modular, scalable, and reusable structure to automate infrastructure provisioning and configuration.  
It follows **Ansible best practices** and is well-suited for both homelabs and production-grade environments.

### Features

- Clean and modular directory layout
- Centralized variable management via `group_vars` and `host_vars`
- Supports external roles and collections via `requirements.yml`
- Compatible with dynamic and static inventories
- Custom `ansible.cfg` for environment-specific tuning

## Project Structure

```
ansible-project/
├── ansible.cfg          # Ansible configuration file
├── hosts.yml            # Inventory file listing the servers
├── site.yml             # Main playbook that runs all roles
├── requirements.yml     # List of required roles and collections
├── group_vars/          # Variables for host groups
├── host_vars/           # Variables for individual hosts
├── roles/               # Contains all roles for different server types
└── README.md            # Project documentation
```

## Usage

1. **Install external roles and collections** (if any):

   ```bash
   ansible-galaxy install -r requirements.yml
   ```

2. **Run the playbook**:

   ```bash
   ansible-playbook -i hosts.yml site.yml
   ```

   > 💡 Use `-K` to prompt for `sudo` password if required.

## Configuration

The project is controlled by `ansible.cfg`, which can define:

- Inventory path (e.g., `hosts.yml`)
- Roles path (e.g., `./roles`)
- SSH settings (e.g., control persist, pipelining)
- Vault password file (optional)

You can override values via:

```bash
ansible-playbook site.yml -e "key=value"
```

Or use structured variable files in:

- `group_vars/<groupname>.yml`
- `host_vars/<hostname>.yml`

## Recommended Best Practices

- **Version Control**: Track changes to playbooks and inventories with Git.
- **Secrets Management**: Use `ansible-vault` for sensitive data (e.g., API tokens, passwords).
- **Idempotency**: Design roles to be repeatable and state-aware.
- **Testing**: Consider using tools like Molecule for role testing in CI pipelines.
- **Linting**: Use `ansible-lint` to validate YAML and role syntax.

## License

Unlicense

## Author Information

This playbook template is maintained by Max Bergmann.  
Feel free to fork, improve, or contribute back! 🚀

