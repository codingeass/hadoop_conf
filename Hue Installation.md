Hue Installation Instruction
============================

1. Check and install following library development packages and tools

		ant
		gcc
		g++
		libkrb5-dev
		libmysqlclient-dev
		libssl-dev
		libsasl2-dev
		libsasl2-modules-gssapi-mit
		libsqlite3-dev
		libtidy-0.99-0 (for unit tests only)
		libxml2-dev
		libxslt-dev
		make
		mvn (from maven package or maven3 tarball)
		openldap-dev / libldap2-dev
		python-dev
		python-setuptools
		libgmp3-dev
        
2. To build and get the development server running:

		git clone https://github.com/cloudera/hue.git
		cd hue
		make apps
		build/env/bin/hue runserver

3.  Add following lines in .bashrc

		export HUE_HOME=/home/amandeep/hue  
		export PATH=$PATH:$HUE_HOME/build/env/bin
