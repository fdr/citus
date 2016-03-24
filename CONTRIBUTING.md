# Contributing to Citus

Thank you, we're happy you want to contribute! You can help us in
different ways:

* Open an [issue](https://github.com/citusdata/citus/issues) with
  suggestions for improvements
* Fork this repository and submit a pull request

Before accepting any code contributions we ask that Citus contributors
sign a Contributor License Agreement (CLA). For an explanation of
why we ask this as well as instructions for how to proceed, see the
[Citus CLA](https://www.citusdata.com/community/CLA).

### Getting and building

#### Mac

1. Install XCode
2. Install packages with homebrew

   ```bash
   brew update
   brew install git openssl postgresql
   brew link openssl --force
   ```

3. Get, build and test the code

   ```bash
   git clone https://github.com/citusdata/citus.git

   cd citus
   ./configure
   make
   sudo make install
   cd src/test/regress
   make check
   ```

#### Linux with Apt-Get (Ubuntu, Debian)

1. Install build dependencies

   ```bash
  sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
  wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
  sudo apt-get update

  apt-get install -y --no-install-recommends \
          autotools-dev build-essential ca-certificates debhelper devscripts \
          fakeroot flex libedit-dev libfile-fcntllock-perl libpam0g-dev \
          libselinux1-dev libxslt-dev lintian postgresql-server-dev-9.5 \
          postgresql-9.5 git
   ```

2. Get, build and test the code

   ```bash
   git clone https://github.com/citusdata/citus.git
   cd citus
   ./configure
   make
   sudo make install
   cd src/test/regress
   make check
   ```

#### Linux with Yum (RHEL, CentOS, Fedora)

1. Find the Postgres 9.5 RPM URL for your repo at [yum.postgresql.org](http://yum.postgresql.org)
   (e.g.  for CentOS 7 it is
   `https://download.postgresql.org/pub/repos/yum/9.5/redhat/rhel-7-x86_64/pgdg-centos95-9.5-2.noarch.rpm`)
2. Register its contents with Yum:

   ```bash
   yum localinstall -y [the-rpm-path]
   ```

3. Install build dependencies

   ```bash
   yum -y update
   yum groupinstall -y 'Development Tools'
   yum install -y \
           curl flex libxml2-devel libxslt-devel openssl-devel \
           pam-devel readline-devel rpm-build tar \
           postgresql95-devel postgresql95-server git

   git clone https://github.com/citusdata/citus.git
   cd citus
   PG_CONFIG=/usr/pgsql-9.5/bin/pg_config ./configure
   cd src/test/regress
   make check
   ```
