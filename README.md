# QuickSetup

Ansible playbook that sets up an **Ubuntu** VM. Pick a profile per VM.

## Usage

```bash
sudo apt update && sudo apt install -y ansible git

ansible-pull -U <repo_url> -i site.yml -t desktop
```

## Options

Choose playbooks to use with tags (`desktop`, `development`, `offensive`).

```bash
ansible-pull -U <repo_url> -i site.yml -t development offensive
```

## Additions

To create an additional playbook add a new role at roles/<name>/tasks
