# ansible 

## Assignment

1. Create an Ansible Playbook to install HashiCorp Terraform and Vault on a Linux OS.
    - Bonus: Check for existing installation/s.
2. Provide step/s to test the Playbook **locally**.
    - Bonus: Leverage a unit testing framework.
3. Create an Ansible Task inside of a Role which runs an AWS command with arguments as key-value pairs. The Task should define a default key-value pair and allow the caller (i.e. Playbook) to override the defaults.
E.g.:
```yaml 
# Role
- name: Task
  command: <command>
  vars:
      .....

# Playbook
- role: role-name
  vars:
      .....
```

## What to Submit

1. [Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) `main` in this repo to your own namespace.
2. Create a new branch in your repo with the name: `<your_github_username>`.
3. Submit a [PR](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) from your forked repo into the `main` branch of this repo.

 - name: Install prerequisites
    package : 
    name:"{ item } "
    update_cache :yes
    with_items: "{{ vault_install_prerequitesites}}"
    become: yes
 -name : Download binary
   geturl:
   url: https://releases.hashicorp.com/vault/{{vault_version}}/vault_{{vault_version}}_linux_amd64.zip
   dest :/tmp/vault_{{vault_version}}_linux_amd64.zip
   owner: "{{vault_user}}"  
   group:"{{vault_group}} " 
   mode: 0755
   checksum:  "{{vault_checksum}} " 
   register :vault_download
 -name : "unzip vault archive {
   unarchive:
   src : "{{ vault_download .dest  }}"
   dest :/usr/local/bin
   copy : no
   owner: "{{vault_user}}"  
   group:"{{vault_group}} " 
   mode: 0755

Write a task in an existing role that runs an AWS command with arguments as key-value pairs. The task should define a default key-value pair and allow the caller of the task/role to override the key-values ?

Aws ec2 existing-role-key-pairs --key-name mykeypair

 {
     "keypairs" : [
     {
         "key name " : "mykeypair"
}
]
}


Test the playbook in the previous step ?
          --check  mode ansible can be used as a layer of testing as well .if running a deployment playbook against an existing   system , using the --check flag to                the ansible command .
