Ansible modules for configuration of IOS XE routers with Netconf
=======

# Introduction
Cisco has shipped IOS XE with support for the Netconf configuration API for a
while. So far you either had to purchase an expensive provision system such as
[NCS](http://www.tailf.com/network-control-system/) or develop your own custom
applications in order to utilize it. The goal with iosxe-ansible is to provide
an open source alternative for all you guys that don't need a fancy tier-1 ISP
provisioing system but still don't want to be stuck in the old CLI/custom
script world.

With iosxe-ansible you'll be able to configure your routers via the open
source Ansible automation framework instead, leaving the old SSH/CLI paradigm.

# What is Ansible
Ansible is an open source IT automation and configuration management tool.
Unlike Puppet and chef, Ansible is agentless, which makes it perfectly suited
to configure networking equipment where it's impossible to install an agent.

For more information regarding ansible, please look at the [official
docs](http://docs.ansible.com).

# Install 
This guide assumes that you have:
* Ansible up and running on your control node.
* Git installed.
* Python pip installed.

**Install the required [pyskate](http://github.com/jonasstenling/pyskate) Python module**
```
sudo pip install pyskate
```
**Install iosxe-ansible files**

Clone this repo and copy all iosxe_ files to your ansible module search path.
```
git clone https://github.com/jonasstenling/iosxe-ansible.git
sudo cp iosxe-ansible/iosxe_* /usr/share/ansible/
```
**Enable netconf in your routers**
```
router#conf t
netconf ssh
end
```
**Test netconf connectivity to your router from your control node**
```
ssh -l admin router.my.domain.com -s netconf
Password:
<?xml version="1.0" encoding="UTF-8"?><hello xmlns="urn:ietf:params:xml:ns:netconf:base:1.0"><capabilities><capability>urn:ietf:params:netconf:base:1.0</capability><capability>urn:ietf:params:netconf:capability:writeable-running:1.0</capability><capability>urn:ietf:params:netconf:capability:startup:1.0</capability><capability>urn:ietf:params:netconf:capability:url:1.0</capability><capability>urn:cisco:params:netconf:capability:pi-data-model:1.0</capability><capability>urn:cisco:params:netconf:capability:notification:1.0</capability></capabilities><session-id>3975491096</session-id></hello>]]>]]>
```
If you see the hello prompt from your router you should be able to connect to it via Netconf.

# User guide
* There is documentation in the source code of the modules on how to use them.
* Please review the example-playbooks directory for some example use cases. 

#Contributing and feedback
If you want to contribute to iosxe-ansible, report bugs or have other
feedback, raise an issue on [GitHub](https://github.com/jonasstenling/iosxe-ansible/issues)!
