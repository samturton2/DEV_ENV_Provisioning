# Vagrant & VM Provisioning

Provisioning is derived from providing and supplying something. For example, provisioning for food or water.

In this context it will be providing our machines with instructions, variables, files and folders.

This will mean we can set up a machine to a specific state when turn on.

## Provisioning with Vagrant
### Core sections of provisioning
There are some actions that are core to provisioning. These concepts are tool and language agnostic.
- making files available/syncing files
- being able to run commands/scripts
- injecting environment variables

### Steps when  given new env project
- What language?
- Is there a framework to install? (rails, flask, django, wordpress)
- any specific packages? list of? (requirements.txt)
- Any tests?
#### Answers for this current Project
- Code in JS and others ( tests in ruby and rspec)
- No frameworks to Install (install testing framework rspec)
- Specific packages with environment file, Gemfile dependcies
- Tests include integration tests to run outside the machine
  - rake spec
  - Some unit tests in JS inside

### Syncing file to vm
- Allowing us to send files and sync them into the VM.
```ruby
  # Sync the app folder
  # config.vm.synced_folder "path/origin/folder", "path/to/destination/folder"
  config.vm.synced_folder "app", "/app"
```
- then `vagrant destroy` `vagrant reload` `vagrant up` `vagrant ssh`

### Running a bash script
This bashscript cna install packages, alter files, do actions in our linux servers when we run `vagrant up`.
This will allow us to set up the machine to state that is desirable for us and automate processes.

In order:
- Create a provion.sh file
- add anything you want to happen when you open the VM
```
sudo apt update
sudo apt install nginx -y
```
- add to vagrantfile
```ruby 
  # run the provision script
  config.vm.provision "shell", path: "environment/provision.sh"
```

- **Managing and running services in linux**
- ```sudo systemctl <action> <system>```
  - `sudo systemctl stop nginx` 
  - `sudo systemctl status nginx` 
  - `sudo systemctl start nginx`

#### Gem and bundler vs pip and packages
- Gems are packages in ruby or dependencies
- Bundler is ruby's package manager
- Gemfile keeps a list of dependencies to be installed
- To install gems from the Gemfile, you run:
`bundle install`

- **Installing gem bundler**
- `gem install bundler`
- **installing tests**
- go to directory with the gemfile in it
- `bundler`
- should be installing lots of dependencies
- **running tests**
- `rake spec`

##### Ruby's testing framework is rspec
- rspec needs to be installed

##### JS package manager is npm (node package manager)
- npm packages

##### Ubuntu package manager
- apt
