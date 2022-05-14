From: https://github.com/rbenv/ruby-build/discussions/1940

Install the dependencies

Ubuntu 22.04:

$ sudo apt install build-essential checkinstall zlib1g-dev
Fedora 36:

$ sudo dnf groupinstall "Development Tools"
$ sudo dnf install perl-core zlib-devel
Download OpenSSL 1.1.1

$ cd ~/Downloads
$ wget https://www.openssl.org/source/openssl-1.1.1o.tar.gz
$ tar xf openssl-1.1.1o.tar.gz
Compile it

$ cd ~/Downloads/openssl-1.1.1o
$ ./config --prefix=/opt/openssl-1.1.1o --openssldir=/opt/openssl-1.1.1o shared zlib
$ make
$ make test
$ sudo make install
Link the system's certs to OpenSSL 1.1.1 directory

$ sudo rm -rf /opt/openssl-1.1.1o/certs
$ sudo ln -s /etc/ssl/certs /opt/openssl-1.1.1o
Install ruby

Use RUBY_CONFIGURE_OPTS=--with-openssl-dir=/opt/openssl-1.1.1o before the command to install the ruby version

$ RUBY_CONFIGURE_OPTS=--with-openssl-dir=/opt/openssl-1.1.1o rbenv install 2.7.6
If you want to make this permanent, add this line to your .bashrc or .zshrc file:

export RUBY_CONFIGURE_OPTS="--with-openssl-dir=/opt/openssl-1.1.1o/"
Then you don't need to use RUBY_CONFIGURE_OPTS=--with-openssl-dir=/opt/openssl-1.1.1o before the command anymore.
