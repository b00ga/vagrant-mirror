Vagrant.configure("2") do |config|
  config.vm.hostname = "mirrortest.example.com"

  config.vm.box = "bento/almalinux-8"
  config.vm.synced_folder "shared-folder", "/vagrant"
  config.vm.synced_folder "playbooks", "/ansible", :mount_options => ["ro"]

  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 2
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ##ansible.galaxy_role_file = "requirements.yml"
    ansible.galaxy_roles_path = "/etc/ansible/roles"
    ##ansible.galaxy_command = "sudo ansible-galaxy collection install -r %{role_file} -p /usr/share/ansible/collections --force && sudo ansible-galaxy role install -r %{role_file} --roles-path=%{roles_path} --force"
    ansible.provisioning_path = "/ansible"
    ansible.compatibility_mode = "2.0"
    ##ansible.verbose = '-vvv'
  end
end
