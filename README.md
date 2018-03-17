
# Project Title

This small project demonstrate few use cases with F5 BIG-IP and Ansible.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites

The most important prerequisite is Ansible version 2.5. Below is the full list of my running environment:
```
ansible==2.5.0rc3
asn1crypto==0.24.0
bcrypt==3.1.4
bigsuds==1.0.6
certifi==2018.1.18
cffi==1.11.5
chardet==3.0.4
cryptography==2.1.4
enum34==1.1.6
f5-icontrol-rest==1.3.7
f5-sdk==3.0.12
idna==2.6
ipaddress==1.0.19
Jinja2==2.10
MarkupSafe==1.0
netaddr==0.7.19
paramiko==2.4.1
pyasn1==0.4.2
pycparser==2.18
PyNaCl==1.2.1
PyYAML==3.12
requests==2.18.4
six==1.11.0
suds-jurko==0.6
urllib3==1.22
```

### Installing

A step by step series of examples that tell you have to get a development env running

Get this repo to your local machine
```
git clone https://github.com/lukaszsedek/f5-ansible.git
```
Install python virtualenv

```
$ pip install virtualenv
```

Create virtual env
```
$ cd f5-ansible
$ virtualenv env
$ source env/bin/activate
```

Install libs

```
$ pip install -r requirements.txt
```

when your installation is done, your  `pip freeze` command should output the same list of libs as above.

Make sure your Ansible is 2.5
```
$ ansible --version
	ansible 2.5.0rc3
```

## Running the code

All playbooks are written as simple as it was possible. The code was run only in lab environment (standalone F5 BIG-IP VE).

### inventory

The inventory keep only one entry, which is my virtual lab machine with 192.168.0.10 address. 

### Executing playbooks
For instance:
```
ansible-playbook -i hosts setup.yml
```

If you encrypted credentials.yml then:

```
$ ansible-playbook -i hosts setup.yml --ask-vault-pass
```

### Files

Explanation of all playbooks

|File| Description |
|--|--|
| `setup-all.yml` | Playbook which build from a scratch HTTPS virtual server with SSL offload, custom HTTP health monitors. The project is located in an isolated partition and route domain |
| `hosts` | Sample inventory file. Only one BIG-IP machine is there |
|`project.yml` | The YML file with variables for `setup-all.yml` playbook. This file has meta-data for this project.| 

### Variables

|Variable name | meaning |
|--|--|
| `partition` | the name of BIG-IP partition. This name will be shown in top right corner |
| `rd_id`| Unique number of routing domain | 
| `vlans.name` | the name of the vlan |
| `vlans.tag` | 802.1q vlan number |
| `vlans.interface` | the interface where vlan will be assigned| 
| `self_ips.name` | |
| `self_ips.address` | |
| `self_ips.netmask` ||
| `self_ips.vlan` | |
| `self_ips.allowed_service` | |
|`nodes.name`|| 
|`nodes.address`||
|`nodes.port`||
|`pool_name`||
|`vs.name`||
|`vs.destination`||
|`vs.port`||
|`probe.name`||
|`probe.send`||
|`probe.receive`||
|`probe.port`||



## Built With

* [F5 BIG-IP VE Trial](https://f5.com/products/trials/product-trials/) - F5 BIG-IP VE. You can obtain your 90-days trial license.
* [Ansible 2.5](https://docs.ansible.com/ansible/devel/roadmap/ROADMAP_2_5.html/) - Ansible automation tool
* [F5 SDK 3.0.12](https://f5-sdk.readthedocs.io/en/latest/) - Required to invoke F5 API from Ansible.

## Contributing

Please read \[CONTRIBUTING.md\](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

I use [SemVer](http://semver.org/) for versioning. For the versions available, see the \[tags on this repository\](https://github.com/your/project/tags). 

## Authors

***Lukasz Sedek*** - *author* - \[Lukaszsedek\](https://github.com/lukaszsedek)

## License

This project is licensed under the MIT License - see the \[LICENSE.md\](LICENSE.md) file for details
