# Ansible PoC

To check if the uv tool's binary directory is included in the systems's PATH:

```sh
echo $PATH | tr ':' '\n' | grep $(uv tool dir --bin)
```

To list all hosts:

```sh
ansible --inventory inventory.yaml --list-hosts all
```

To test the connection to all hosts:

```sh
ansible --inventory inventory.yaml --module-name ansible.builtin.ping all
```

To run the playbook with a dry run:

```sh
ansible-playbook --ask-pass --ask-become-pass --check --inventory inventory.yaml playbook.yaml
```

To pilot the playbook on a subset of hosts as a staged rollout:

```sh
ansible-playbook --ask-pass --ask-become-pass --inventory inventory.yaml --limit workers[0] playbook.yaml
```
