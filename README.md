# manageiq-develop

## Develop env requirement
Ubuntu 17
RAM 8G
CPU 4core

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
