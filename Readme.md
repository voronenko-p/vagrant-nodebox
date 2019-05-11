Vagrant ansible boilerplate
===========================

Boilerplate for project level Vagrant file

Put your custom provisioning logic into `Vagrantfile.provision`, for example

```

# ================================== CUSTOM PROVISIONING
#    https://www.vagrantup.com/docs/provisioning/ansible_common.html
      config.vm.provision "ansible" do |ansible|
          ansible.playbook = "deployment/provisioners/lamp-box/box_lamp.yml"
          ansible.verbose = true
          ansible.groups = {
              "lamp_box" => [vconfig['vagrant_machine_name']]
          }
      end

# /================================== CUSTOM PROVISIONING

```

You can also have untracked `Vagrantfile.local` which allows you to locally modify some aspects for the shared project Vagrantfile.


Basing on https://galaxy.ansible.com/softasap roles  there are multiple compatible "box provisioners",
which share common approach with both Vagrant and Terraform provisioners, that allow you to reuse the same 
code organization for production deployment also.

For terraform part check out https://github.com/Voronenko/devops-terraform-ansible-boilerplate
