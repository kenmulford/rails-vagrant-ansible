# rails-vagrant-ansible

A Vagrant box for Rails development, provisioned with Ansible.

## Installation

- [Install Ansible](http://docs.ansible.com/ansible/intro_installation.html)
- Run `sudo ansible-galaxy install rvm_io.rvm1-ruby`
- Copy the following into your Rails app folder: (if this is a new Rails app that hasn't been created yet, copy them into the project folder you want to use.)

```
ansible/
Vagrantfile
```

- Edit `ansible/playbook.yml` to comment out any installations you don't need
- Edit `ansible/config.yml` to configure versions and DB setup info
- From within your Rails app folder, run `vagrant up`
- Set up your app to use the database connection provided. Either:
  - Install the [`dotenv`](https://github.com/bkeepers/dotenv) gem and update your `database.yml` with the following entries:

        development:
          host:     <%= ENV['DB_HOST'] %>
          database: <%= ENV['DB_NAME'] %>
          username: <%= ENV['DB_USERNAME'] %>
          password: <%= ENV['DB_PASSWORD'] %>
        test:
          host:     <%= ENV['DB_HOST'] %>
          database: <%= ENV['DB_NAME'] %>_test
          username: <%= ENV['DB_USERNAME'] %>
          password: <%= ENV['DB_PASSWORD'] %>

  - Or, hard-code your `database.yml` file to use the same config as `ansible/config.yml` (not recommended)

## Usage

- From within your Rails app folder, run `vagrant ssh`. This will connect you to the Vagrant box.
- From within the Vagrant box, run `cd /vagrant`
- If this is a new Rails app that hasn't been created yet, run `rails new .`. This will create a new Rails app in that folder
- Run any of your normal Rails setup commands, like `bundle install` and `bin/rake db:migrate`
- Run `bin/rails server -b 0.0.0.0`

Then your app will be accessible at [http://localhost:3000](http://localhost:3000)

## License

MIT. See License file for more info.
