# QuickSetup

Ansible playbook that sets up an **Ubuntu** VM. Pick a profile per VM.

## Usage

```bash
sudo apt update && sudo apt install -y ansible git
git clone <repo-url> quicksetup && cd quicksetup

ansible-playbook site.yml -e profile=development --ask-become-pass
```

Run as your normal user, not with `sudo`.

## Profiles

Profiles live in [`profiles/`](profiles/). You must pass one with `-e profile=<name>`.

| Profile | Installs |
|---|---|
| `development` | common, desktop, development, shell |
| `offensive` | common, desktop, offensive, shell |

To add one, copy a file in `profiles/` and use its name as the `profile` value.

## Roles

- **common:** vim, wget, curl, git, unzip, gnupg2, Universe repo
- **desktop:** Firefox, VS Code, Ghostty
- **development:** Docker, Neovim, Postman
- **shell:** Zsh (default shell), tmux, bat, htop
- **offensive:** Nmap, Netcat, Chisel, NetExec, SearchSploit, Proxychains, Impacket, LinPEAS, WinPEAS, GTFOBins, wordlists/SecLists, Hydra, John, Burp Suite, ffuf, smbmap

## Options

Turn a role on or off in the profile (`install_desktop`, `install_development`, `install_offensive`, `install_shell`). Skip a single tool with an extra var:

```bash
ansible-playbook site.yml -e profile=development -e install_docker=false --ask-become-pass
```

Tool vars: `install_firefox`, `install_vscode`, `install_ghostty`, `install_docker`, `install_neovim`, `install_postman`, `install_zsh`. All default to `true`.
