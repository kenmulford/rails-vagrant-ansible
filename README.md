# rails-vagrant-ansible

A Vagrant box for Rails development, provisioned with Ansible.

## Usage

- Install Ansible
- Run `ansible-galaxy install rvm_io.rvm1-ruby`
- Copy the following into your Rails app folder: (if this is a new Rails app that hasn't been created yet, copy them into the project folder you want to use.)

```
ansible/
Vagrantfile
```

- Edit `ansible/playbook.yml` to comment out any installations you don't need
- Edit `ansible/config.yml` to configure versions and DB setup info
- From within your Rails app folder, run `vagrant up` and then `vagrant ssh`. This will connect you to the Vagrant box.
- From within the Vagrant box, run `cd /vagrant`
- If this is a new Rails app that hasn't been created yet, run `rails new .`. This will create a new Rails app in that folder
- Run `rails s -b 0.0.0.0`

Then your app will be accessible at [http://localhost:3000](http://localhost:3000)

## License

MIT. See License file for more info.
