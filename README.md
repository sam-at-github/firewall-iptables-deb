# Overview
Simple iptables firewall setup packaged as a debian init script. Based off tutorial by David A. Ranch at  http://www.ecst.csuchico.edu/~dranch. We break out actual rules to directory `/etc/firewall-iptables/scripts.d/` and run them with `run-parts start|stop`. This makes thing more customizable and easy to manage.

# Installation
To install as a .deb package:

    git clone https://github.com/sam-at-github/firewall-iptables && git checkout debian
    cd firewall-iptables/ && dpkg-buildpackage -b -uc -us && cd -
    sudo dpkg -i firewall-iptables_*.deb

Alternatively you can use the Makefile.

# Configuration
All configuration for built in scripts is via vars in /etc/default/firewall-iptables. See the defaults.

# Usage
Should be installed as a service as above, and used like `service firewall-iptables {start|stop|restart|force-reload}`. The built-in individual scripts can also be used like `CONFFILE=./firewall-iptables.conf ./scripts.d/001-forward {start|stop}`.
