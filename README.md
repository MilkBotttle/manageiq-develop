# manageiq-develop

## Develop env requirement
* Ubuntu 17 
* RAM 8G
* CPU 4core

## Develop environmnet create

* install requirement package
```
sudo apt install git                              # Git and components
sudo apt install memcached                        # Memcached for the session store
sudo apt install postgresql libpq-dev             # PostgreSQL Database server and to build 'pg' Gem
sudo apt install bzip2 libffi-dev libreadline-dev # For rbenv install 2.2.0 (might not be needed with other Ruby setups)
sudo apt install libxml2-dev libxslt-dev patch    # For Nokogiri Gem
sudo apt install libsqlite-dev libsqlite3-dev     # For sqlite3 Gem
sudo apt install nodejs nodejs-legacy npm         # For ExecJS Gem and bower
sudo apt install g++                              # For unf Gem
sudo apt install libcurl4-gnutls-dev              # For Curb
sudo apt install cmake                            # For rugged Gem
sudo apt install libgit2-dev pkg-config libtool
sudo apt install libssl1.0-dev                    # for puma < 3.7.0

```
* Install the Bower and Yarn package manager
```
sudo npm install -g npm
sudo npm install -g bower yarn
```
* Install the Gulp and Webpack build system
```
sudo npm install -g gulp-cli
sudo npm install -g webpack
```

* Enable Memcached
```
sudo systemctl enable memcached
sudo systemctl start memcached
```
* Configure PostgreSQL
```
sudo grep -q '^local\s' /etc/postgresql/`9.6`/main/pg_hba.conf || echo "local all all trust" | sudo tee -a /etc/postgresql/`9.6`/main/pg_hba.conf
sudo sed -i.bak 's/\(^local\s*\w*\s*\w*\s*\)\(peer$\)/\1trust/' /etc/postgresql/`9.6`/main/pg_hba.conf
sudo systemctl restart postgresql
sudo su postgres -c "psql -c \"CREATE ROLE root SUPERUSER LOGIN PASSWORD 'smartvm'\""
```
```
note
posgresql version check
```

* install rvm
```
sudo apt-add-repository -y ppa:rael-gc/rvm
sudo apt-get update
sudo apt-get install rvm
```
```
note
check the dns config when start install
need relogin and source rvm.sh
```

* install ruby
```
rvm install 2.3.3
```

* clone github repo and setup
```
git clone https://github.com/ManageIQ/manageiq
cd manageiq
bin/setup #do not run this in root or sudo
```
```
note
check the folder ~/.config/configestore not root
```

* start / stop miq
```
rake evm:start
rake evm:stop
```
* login
```
http://ip:3000
admin /smartvm
```

## Develop other pluin eg. manageiq-provider-openstack

* prepare the repo
We use the plugins folder to put the plugins
```
mkdir /path/to/manageiq/plugins
cd plugins
git clone plugs
```
* create Gemfile.dev.rb in bundle.d
```
override_gem 'manageiq-provider-openstack', :path => File.expand_path("../plugins/manageiq-provider-openstack")
```

